---
title: "Video drivers not loading?"
date: 2006-04-18
forum: Installation &amp; Upgrades
---

### Post by shenders on 2006-04-18
:confused: 
Hello,Brand newbie here.
I need some info running live cd.Everything seems to install but when it gets to the end all I get are colored video lines on the monitor.Can someone help with this.It seems like no video drivers are loading and of course I wouldn't know how to go about that anyway.
The card is 6800gs NVidia.
I set the resolution option to 1024x768 and 800x600 and get the same results.
Thanks for any help.

---

### Post by Sutekh on 2006-04-19
I really suggest that you check out post # 3 of this thread

[Ubuntu Forums - Live CD X Server Prob?](http://ubuntuforums.org/showthread.php?p=935524#post935524)

The poster was able to solve their problem by using the **live-expert** function of the LiveCD.  Using this method they were able to stop the auto-detection of their hardware and specify the video driver that the LiveCD uses.  

If you are able you should try to boot the LiveCD using the **live-expert** mode and choose the **vesa** driver.

I think this problem is due to the selected default driver.  Fortunately NVIDIA cards seem to be alot easier to configure than ATI cards, so you should be able to fix your problems very easily (either in the LiveCD or if you decide to install Ubuntu)

This thread contains three methods to install better supported NVIDIA drivers.

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers](http://ubuntuforums.org/showthread.php?t=75074)

 - Method 1 is very easy and will install the v7667 NVIDIA drivers from Ubuntu's repository, this can be done both in a LiveCD session or on an installation

 - Method 2 is a little more involved, I don't know if this can be achieved in a LiveCD session, but certainly can be done in an installation, and isn't too hard

I wish you the best of luck!

---

### Post by Mr Darcy on 2006-05-02
Hi Shenders.
I had exactly the same problem with my XFX 6800GS.
I followed some instructions to install as a server then load everything, but there is an easier method here;
[http://www.ubuntuforums.org/showthread.php?t=138417&highlight=6800gs](http://www.ubuntuforums.org/showthread.php?t=138417&highlight=6800gs)
Hope this helps.

---

