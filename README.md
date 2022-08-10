# naorobot-licalisation-path-planning
naorobot localisation 
We put in every room a landmark in the top on the wall so that it does not mix with
other signs in the room. first step when nao wake up is to raises his head, scan the
place looking for that landmark
These landmarks are in the shape of a circle in various colors every color define
a place
- Red circle represents the bed room
- Green circle represents the living room
- Blue circle represents the kitchen
So basically, what we are trying to do is essentially filter out a color. By default, the
images are represented in three channels Blue, Green, and Red. But, using this mode
of representation, you cannot filter colors easily as the values are split into three
channels. That's where the HSV (Hue, saturation, value) mode of representation comes
to play, The line HSV = cv2.cvtColor(img, cv2.COLOR_BGR2HSV) converts the
BGR format image to HSV format representation. And just add +-delta value to H
channel and you can filter the color accordingly.For example, if you want to filter green
color The BGR representation of green color will be (0,255,0). First, we need to find
the equivalent color representation in HSV that is (60,255,255). We can add a [H-10,
100,100] and [H+10, 255, 255] as upper and lower values accordingly.
Since the land mark is located in a certain place for this example located in (0,3)
coordinate that means nao find his direction in the room and left only two
coordinates so it would find it exact location (x, y coordinate) in the map
Every coordinate in the map has certain values within a specified range (x and y)
To find this coordinate Nao will activate his sonar calculate the distance to get x
value and the turn 90° and activate his sonar and calculate the distance to get y
value Consider that the room surroundings are (the width is 2.5 cm and the length also
2.5cm ) because the maximum range of nao sonar is 2.5cm
And also taken into account the fixed obstacle


naorobot path planning

![image](https://user-images.githubusercontent.com/73589635/183874745-68076194-3feb-45fa-8947-d516e2105b4d.png)

In the figure the robot is in coordinate with blue color and the destination in
the coordinate with green color so in order to find the best way to go to that point
we notice when dropping the robot coordinate on the x and y parameter and then
connect it with destination coordinate an right triangle formed ,Now based on the
relationship between the robot point and the destination point will fix the robot
direction without forgetting that the robot in the beginning is faced to the left with
90° from the previous part what left is correcting the angle calculate the steps , with
using phytagels formular 
to find hypotenuse value witch represent
the number of steps and calculate the angle of it tan∅
and we get the turning angle for the robot , now after getting the angle and the number od
steps nao will walk to the destination point

![image](https://user-images.githubusercontent.com/73589635/183877364-3827a36f-be9d-49c1-ad77-8b365342d904.png)
