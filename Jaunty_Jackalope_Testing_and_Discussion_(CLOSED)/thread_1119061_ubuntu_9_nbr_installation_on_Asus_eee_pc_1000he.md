---
title: "ubuntu 9 nbr installation on Asus eee pc 1000he"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cubical10 on 2009-04-07
First off:
1. I realize that I am currently running a beta.
2. Mods, if this topic could be better placed in another forum, please move it.


I have installed the latest 9.04 beta.  For the most part everything works.
The function keys for audio (Fn+F10/F11/F12 | mute/down/up) work with on screen display.
The function keys for screen brightness (Fn+F5/F6) work, but there is no on screen display.

Fn+F2 will suspend the machine without issue.

Fn+F3, F4, F7, F9 do nothing.

Wireless works, there is no issue after resuming on suspend.

The one issue I am having is that the WebCam is not recognized.  I cannot get it to work with Cheese or Skype.  Both apps claim that no camera is found.
**Can anyone help me setup the camera**?  As far as I know, the camera works.
I have this eeepc setup to dual boot with the XP installation that it came with.  The camera works in XP.

root@eeepc0:/home/cubical# uname -a
Linux eeepc0 2.6.28-11-generic #40-Ubuntu SMP Fri Apr 3 17:39:51 UTC 2009 i686 GNU/Linux

---

### Post by cariboo on 2009-04-07
I moved your post.

Jim

---

### Post by e.j. on 2009-04-07
Try kernel 2.6.29?

[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

The webcam on my 1000he works in Skype and Cheese on 2.6.29. On the other hand, it also worked right after installing the 9.04 beta w/ 2.6.28...

---

### Post by IanW on 2009-04-08
Have you enabled the camera in BIOS?

---

### Post by cubical10 on 2009-04-08
@Jim, thank you for moving this topic to the proper forum.

I installed the kernel as suggested, but that did not work.

I went back into XP, made sure the camera was enabled and working and then reinstalled Ubuntu.  After the install the camera was not there, again.  So I checked the BIOS and found that the camera was disabled.  I re-enabled the camera and all is good.  So it seems to me that the camera is disabled at the BIOS level during the install.  Or maybe I was not paying attention.
Thanks for taking the time to help.


I installed kernal 2.6.29 again just for kicks.  I cannot see a difference between them.   Both work well.

---

