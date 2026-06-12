---
title: "RhythmBox and Software center problem"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by Jeyaganeshdj on 2009-11-17
Please find the errors when i tried to run RhythmBox and Ubuntu Software center from terminal. I cannot open this apps through menu. Please let me know how to solve this problem

RhythmBox

** (rhythmbox:2035): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:2035): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:2035): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault

Ubuntu Software center

Traceback (most recent call last):
File "/usr/bin/software-center", line 25, in <module>
import pygtk
ImportError: No module named pygtk

---

### Post by mardis on 2009-11-19
I'm getting the same error ...


ImportError: No module named gobject

** (rhythmbox:8415): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:8415): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:8415): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault
mardis@mardis-desktop:~$ No module named pygtk
No: command not found


I've tried removing and reinstalling without any luck.

---

### Post by Jeyaganeshdj on 2009-11-22
Hi,

 I got the below error when trying to run firewall.. the same type of error when i try to start software center and rhythmbox.


  Please let me know whether this can be rectified or I should do a complete reinstallation.. I have not got any replies for the same type of error for more than 4 days.. I am not trying to be rude but atleast if i know i cannot find a solution its better i try again installing...

home@home-desktop:~$ gufw
Traceback (most recent call last):  File "/usr/share/gufw/gufw.py", line 20, in <module>
    import view.guiGufw
  File "/usr/share/gufw/view/guiGufw.py", line 19, in <module>
    import pygtk
ImportError: No module named pygtk

---

### Post by hbpb on 2009-11-23
I am having a similar problem.  Software center tries to open and then just quits and disappears.  I tried to reinstall software center.  Didn't fix the problem.  When I enter 
software-center in the terminal window it gives me an error message-
ImportError: No module named pygtk

All this began after a recent install of Ubuntu and having accepted all updates post-install.

Any help would be great!

---

### Post by Jeyaganeshdj on 2009-11-28
still no one knows the solution?????

---

### Post by Jeyaganeshdj on 2009-11-28
Without RhythmBox and software center atleast I can manage. But without firewall its hard to stay in Ubuntu. Will clean up ubuntu and heading back to windows.... Thanks and Bye.....

---

