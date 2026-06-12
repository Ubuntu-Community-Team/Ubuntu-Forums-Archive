---
title: "problem with uninstalling python2.7"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by Shamma009 on 2011-03-29
hello all, 
 
I have this problem I am trying to fix from several days now :( 
 
so, I installed python2.7 in my ubuntu and then I downloaded packages for python and apperantly, they got installed in python2.6, so whenever I want to run my code I have to run it in python2.6 
 
so I deleted the file of python2.7 and I uninstall it in synaptic, but whenever I type python in the command line it gives me the 2.7 version !!!! which I don't know how ...
 
the issue now is the following, I downloaded ROS which is Robot operating system and I think it is looking for python2.7 which I deleted, so it gave me at the begining error of pythonmodel and I fixed it so it points to to usr/lib/python2.6 and now it gives me that error when I try to run roscore command which should start the ros nodes ...
 
 
 
[PHP]Traceback (most recent call last):
  File "/opt/ros/diamondback/ros/bin/roscore", line 34, in <module>
    from ros import roslaunch
  File "/opt/ros/diamondback/ros/core/roslib/src/ros/__init__.py", line 41, in <module>
    import roslib
  File "/opt/ros/diamondback/ros/core/roslib/src/roslib/__init__.py", line 50, in <module>
    from roslib.launcher import load_manifest
  File "/opt/ros/diamondback/ros/core/roslib/src/roslib/launcher.py", line 45, in <module>
    import roslib.manifest
  File "/opt/ros/diamondback/ros/core/roslib/src/roslib/manifest.py", line 46, in <module>
    import roslib.packages
  File "/opt/ros/diamondback/ros/core/roslib/src/roslib/packages.py", line 52, in <module>
    from subprocess import Popen, PIPE
  File "/usr/lib/python2.6/subprocess.py", line 427, in <module>
    import select
ImportError: No module named select
[/PHP]
 
 
mmmmmmmmmmmmmmmm, any idea of what might be the problem? I tried to uninstall ros from synpatic, and install it again with no use :(

---

