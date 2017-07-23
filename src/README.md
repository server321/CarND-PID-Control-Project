# Introduction #

The goal of this project is to create a PID controller, tune its hyperparameters by testing on the simulator.

The simulator provides cross-track error (CTE), speed, and steering angle data via local websocket uWS. 
The PID controller must respond with steering and throttle commands to drive the car reliably around the simulator track. I used only steering command to control the car.


# Components of PID #

## Proportional ##

The "P" for proportional means that the car will steer in proportion to the cross-track error, or CTE. CTE measures how far from the middle line of the road the car is. If the car is to the left of the line then you the car should steer to the right and otherwise. The coeficient is proportional to the distance from the lane center. This is the most directly observable effect on the car's behavior. 

 
## Integral ##

The I for "integral" means component that counteracts a bias in the CTE which prevents the P-D controller from reaching the center line. This bias can take several forms, such as a steering drift. If the coefficient is too high for I, the car tends to have quicker oscillations, and does not tend to get up to a quick speed. A low coefficent for I will cause the car to tend to drift to one side of the lane or the other for longer periods of time.

## Differential ##

The D for "differential" means component that counteracts the P component's tendency to overshoot the center line. A properly tuned D parameter will cause the car to approach the center line smoothly. Too high of a coefficient leads to almost constant steering angle changes of large degrees, where although the car will be well-centered it can hardly move. Too low of a D coefficient will lead to the oscillations being too high with more overshooting.

# Tuning hyperparameters #
I experimented with Twiddle to try out different parameters, but removed it from the final code. I found the values and then the final values were determined by manual tuning.

The final hyperparameters are:

Kp = 0.15
Ki = 0.0002
Kd = 2.0

