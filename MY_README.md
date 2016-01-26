#Explanations on the optimizations I did and how to double check the results#

##./index.html page loading optimizations##

###To verify the optimization goal of a (https://developers.google.com/speed/pagespeed/insights/)###

1. Check out the repository
2. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

3. Open a browser and visit localhost:8080
4. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok http 8080

5. enter the url ngrok provides  in insights and click analyze

### What i did to reach the goal of 90 ###

I basically followed the insights advices:
*optimized images
*moved css inline and kept css for printing in a separated file
*moved js scripts to the end of html

##fps optimization of pizza page##

###You can turn on fps screen in google chrome to check for fps stay above 60 when scrolling down the slider###

1. enter chrome://flags/
2. activate fps Counter
3. restart chrome

###What I did###

For both goals (render time after pizza resize and 60 fps), I altered the relevant for iteration.
You'll find related comments in the main.js file.
Besides this I moved the initialLeft property of elm out of the updatePositions, as the values are static
and by this they are getting calculated only once and not every time updatePositions runs.
I moved the floating pizza parameters out of the updatePositions and into constants as the given value
off 200 floating pizzas unnecessarily high to me. 30 filled my 13" screen...
