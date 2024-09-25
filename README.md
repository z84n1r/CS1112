java c
CS1112 Fall 2024 Project 2
due Wednesday 9/25 at 11pm
Objectives
Completing this project will solidify your understanding of for-loops, while-loops, and nested loops. The computational theme of this project is simulation, with problem 1 using randomness as a computational tool. You also will play with graphics.
Ground Rule
Since this is an introductory computing course, and in order to give you practice on specific programming constructs, some Python functions/features are forbidden in assignments. Specifically, the use of lists and the break and continue commands is not allowed in this project. Only the built-in functions and language features that have been discussed in class and in the assigned reading may be used. For this project, do not define your own functions; we will do that later in Project 3.
1 Eclipse
The “Monte Carlo approximation of π” presented in Lecture 5 allows us to estimate π using randomness and proportion. Indeed, the method of Monte Carlo Approximation has many uses in science and engineering and one of them is to estimate the area of arbitrary shapes whose boundaries can be described by a set of equations.
The equation (x − h)2 + (y − k)2 − r2 = 0 describes a circle with ra-dius r centered at (h, k). Therefore, a pair of values x and y satisfy-ing
(x − h)2 + (y − k)2 <= r2
is a point that lies inside or on the circle.

Write a script. estimate area (i.e., write a file estimate area.py) to de-termine the area of the lune (crescent) or ring formed from overlapping a bigger circle with a smaller circle using Monte Carlo approximation. Your script. should produce a figure showing the “darts” in the three areas: the smaller circle, the bigger circle excluding the occlusion, and the rectan-gular “dart board” area not covered by the circles. Display as the title of the figure the estimated area. In the example output (figure) above, the bigger circle has a radius of 3 and is centered at (2, -1). The smaller circle has a radius 2 and is centered at (1, -1). You can choose any color combination that you like in order to display the “darts”.
Start by reviewing the notes and code from Lecture 5 on the Monte Carlo approximation of π! This problem is slightly different as you are estimating the area of a shape:

Note the new file mc pi.py posted with Lecture 7 that includes graphics in addition to the numerics of the dart throwing approximation of π. You will find the graphics commands demonstrated in mc pi.py useful.
Requirements and program development hints
❼ Import and use the modules random and matplotlib.pyplot. You may additionally need math.
❼ Each circle is represented by three values: radius, x coordinate of the cetner, and y coordinate of the center. Using meaningful variable names, you can “hardcode” the values, i.e., type into the script. the values, that we used to produce the example figure above to start program development. Those values give two circles that overlap. After you have a working program, try other values. Hardcoding the values instead of using input statements makes initial testing easier. When you submit your file you can leave these hardcoded values in or replace them with input statements if you prefer.
❼ Your script. should do the area estimation only if the two circles overlap. If the two circles do not overlap, your program should print a message to the console saying so and should neither estimate an area nor do graphics. Hint: One way to tell whether two circles overlap is to consider the distance between their centers.
❼ If the circles overlap, your code should set the dart board such that both circles lie entirely within the dart board and are not too small to be seen clearly on the dartboard.
❼ You need to choose the number of darts for the Monte Carlo approximation. In the early stages of program development, use a small number of darts in order to speed up experimentation and testing! Once you are satisfied with your program after testing, choose a number of darts that shows the circles reasonably well.
❼ The area approximation is to be shown as the title of the figure, not displayed in the console. (Review the camera fov problem of Project 1 for how to work with the figure title.)
2 Blinking Indicator Light
Blinking indicator lights are often used as a safety measure to warn people about a potential danger. They are common in places like crosswalks and construction sites. The blinking of these lights can be achieved by charging and discharging a capacitor. A capacitor can store electrons inside it and act as a battery for a short period of time. We can use the following equations to describe the voltage (v) as a function of time (t) of a capacitor as it is charging:

where v0 is the voltage of the battery, R is the resistance of a resistor, C is the capacitance of the capacitor, and tc is the charging time of the capacitor to reach its maximum voltage. Note that exp(x) denotes the natural exponent of x (i.e., exp(x) = ex). After charging for tc time, the capacitor voltage reaches its maximum vmax, which is given by the following equation:

After the charging time, the capacitor immediately starts to discharg代 写CS1112 Fall 2024 Project 2Python
代做程序编程语言e and it is described by the following equation:

The capacitor discharges until it reaches a minimum voltage given by vmin. The entire time taken for charging and discharging is given by:

Suppose that this capacitor powers an indicator light. We will use the following constant values in our programs: v0 = 10 volts, R = 10 × 103 ohms, vmin = 0.01 volts, and C = 10 × 10−6farads. [Revised 9/18]
2.1 How long does it take to reach a certain voltage?
Write a script. time to target (i.e., write a file time to target.py) to determine and print to console how many seconds it takes the capacitor to reach a user-specified voltage given a user-specified charging time for max voltage. If the capacitor cannot reach the specified voltage, your script. should print a message saying so. Solicit the goal voltage in volts and the max charging time (tc) in seconds as user inputs. Both input values should be positive and your script. should re-prompt the user (as many times) as necessary to ensure that positive values are entered. You can assume that the user does enter numbers and not words. Hardcode the constant values given above.
Use a loop to solve the problem; do not solve for the time algebraically. If the user specified voltage is achievable, you should increment the time and compute the voltage of the capacitor until the goal voltage is reached. Given the constants above and the typical voltage and charging time of interest, a time step in the order of 0.001 second would be reasonable. (A smaller time step will give higher accuracy but at the expense of a longer computation time.) You may not need all the equations given above.
You will need to use the math module functions exp to calculate the natural exponential of a value and log to calculate the natural log of a value. For example, to calculate e3.5 and ln 4.2 you would write the expressions math.exp(3.5) and math.log(4.2), respectively. This assumes that the math module has been imported. Now start practicing reading documentation. Go to https://docs.python.org/3/library/math. html to find the documentation of the math module. Next, look up math.exp and math.log on that page and read its description and usage. You already know how to call the log function given our example above, which makes now the best time to learn to read documentation! Documentation can seem cryptic to new programmers, so reading it when you already know how to call the function is an excellent way to learn the conventions used in documentation. Ask a member of the course staff if you want some help in interpreting the documentation.
Sanity check: With a max charging time of 0.5 seconds, it takes about 0.139 seconds to reach 7.5 volts (based on the given constants).
2.2 How long does the indicator light stay on?
Suppose that when the capacitor voltage is above a certain target voltage, the indicator light stays on. And when the voltage is below this target voltage, the light will stay turned off. (This cycle is repeated to make the indicator light blink.) Write a script. time on to determine the duration that the light stays on (during the period 0 ≤ t ≤ tf ) as a function of the charging time tc. Let the range of interest of the charging time to be 0.01 to 0.5 seconds. Solicit the target voltage as user input, re-prompting the user as necessary to ensure that the target voltage is a positive value. Your script. should produce a graph of duration versus charging time, an example of which is shown below for a target voltage of 5 volts.
Algorithmic notes:
❼ You need to loop over the charging times of interest. Choose a reasonable step size.
❼ For each charging time, you need to determine the duration when the light stays on (duration above the specified voltage). Again, use a loop to solve this subproblem—do not solve for the duration algebraically. Consider these two algorithms:
1. If the target voltage is achievable, loop over the time from zero to tf and check the voltage at each iteration. You need to devise a way to identify the beginning and ending time that the voltage is above the target voltage in order to calculate the duration.
2. Instead of going from t = 0 to the predetermined tf , you can have the loop end when the voltage drops back below the threshold.
You can use either algorithm to solve the problem, but which algorithm is more efficient? Write a one-sentence comment at the end of your script. to state and explain your answer.
Graphics notes. You will need the matplotlib.pyplot sublibrary for graphics, as before. However, it is not necessary to write code to “set up the figure window” as we did for the previous problems since we want to allow auto-scaling of the axes this time—matplotlib.pyplot by default will size the axes to show all the data, so you should neither manually set the axes scaling nor set the axes limits. I.e., just plot the data using a marker and a color of your choice. Label the axes and give the plot an appropriate title that includes the user-specified voltage.

Submit your files estimate area.py, time to target.py, and time on.py in CMS (after registering your group).







         
加QQ：99515681  WX：codinghelp
