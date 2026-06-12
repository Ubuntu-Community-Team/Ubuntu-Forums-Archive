---
title: "Unable to execute command &quot;rosmake openni_kinect --rosdep-install&quot;"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by eabryan on 2011-05-05
When I attempt to execute the above command, here is what I see

ecestudent@ubuntu:~$ rosmake openni_kinect --rosdep-install
[ rosmake ] Packages requested are: ['openni_kinect']                                                                                                        
[ rosmake ] Logging to directory/home/ecestudent/.ros/rosmake/rosmake_output-20110505-151351                                                                 
[ rosmake ] Expanded args ['openni_kinect'] to:
['openni_camera', 'nite', 'openni', 'openni_camera_unstable', 'openni_tracker']                              
[ rosmake ] Generating Install Script using rosdep then executing. This may take a minute, you will be prompted for permissions. . .                         
rosdep executing this script:
{{{
set -o errexit
#Packages
sudo apt-get install nite-dev libusb-1.0-0-dev openni-dev sip4 ps-engine
}}}
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[ rosmake ] rosdep install failed: rosdep script failed with stderr 
{{{
E: Unable to locate package nite-dev
E: Unable to locate package openni-dev
E: Unable to locate package ps-engine

}}}


I have tried to update using:

$ sudo apt-get update

but I have had no success.

---

### Post by RobotsRocks on 2011-07-09
I think that this happens because you don't have the ros repositories in the apt sources.list.

Try with this, depending your distribution:

[LIST]
[*]**Ubuntu 10.04 (Lucid)** 

[LIST]
[*]
$sudo 'echo "deb [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) lucid main" > /etc/apt/sources.list'
[/LIST]
**Ubuntu 10.10 (Maverick)** 

[LIST]
[*]
$sudo 'echo "deb [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) maverick main" > /etc/apt/sources.list'
[/LIST]
**Ubuntu 11.04 (Natty)** 

[LIST]
[*]
$sudo 'echo "deb [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) natty main" > /etc/apt/sources.list'[FONT=Verdana][/FONT]
[/LIST]
[/LIST]
   Then update the repositories with:

            $sudo apt-get update

And finally try again the rosmake.

NOTE: I get the repositories from [http://www.ros.org/wiki/diamondback/Installation/Ubuntu](http://www.ros.org/wiki/diamondback/Installation/Ubuntu) . 



> **eabryan said:**
> When I attempt to execute the above command, here is what I see

ecestudent@ubuntu:~$ rosmake openni_kinect --rosdep-install
[ rosmake ] Packages requested are: ['openni_kinect']                                                                                                        
[ rosmake ] Logging to directory/home/ecestudent/.ros/rosmake/rosmake_output-20110505-151351                                                                 
[ rosmake ] Expanded args ['openni_kinect'] to:
['openni_camera', 'nite', 'openni', 'openni_camera_unstable', 'openni_tracker']                              
[ rosmake ] Generating Install Script using rosdep then executing. This may take a minute, you will be prompted for permissions. . .                         
rosdep executing this script:
{{{
set -o errexit
#Packages
sudo apt-get install nite-dev libusb-1.0-0-dev openni-dev sip4 ps-engine
}}}
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[ rosmake ] rosdep install failed: rosdep script failed with stderr 
{{{
E: Unable to locate package nite-dev
E: Unable to locate package openni-dev
E: Unable to locate package ps-engine

}}}


I have tried to update using:

$ sudo apt-get update

but I have had no success.

---

