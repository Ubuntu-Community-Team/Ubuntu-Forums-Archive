---
title: "Cannot Install 7.04 (freezes??)"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by WhatYouNeed on 2007-10-15
Brand new to Ubuntu and tying to create a media PC.  I have an old Dell machine that told me the system 32 file was corrupt.  I reinstalled windows 2000 professional as well as the network driver and the graphics card.  When I put the Ubuntu disk in the CD-ROM the browser window opens properly and I can install firefox or calmwin.  The problem comes win I restart the PC and have it boot from the CD ROM.

The Ubuntu installation screen comes up properly, but if I tell it to install normally the Ubuntu loading screen comes up, but eventually it will just go black and sit there doing nothing.  If I start Ubuntu in safe graphics mode, eventually an orange screen appears, but nothing else.

What am I doing wrong?

NTFS file system, recently formatted
29.6gig free
eGeForce 5200 128mb graphics 
Using an S video cable into a TV

---

### Post by PmDematagoda on 2007-10-15
Forgive me, but I didn't understand you, did you install Ubuntu using the Live CD? According to this it seems to be:-

> When I put the Ubuntu disk in the CD-ROM the browser window opens properly and I can install firefox or calmwin.

---

### Post by WhatYouNeed on 2007-10-15
I apologize.  Allow me to clarify.  When I start up the PC and allow it to boot into Windows 2000 Prof everything runs fine.  When I put the Ubuntu Live boot disk in the CD ROM from Windows 2000 Prof, Ubuntu loads properly and displays the appropriate screen.

When I restart however and allow the PC to boot off the Ubuntu live disk, everything works fine for the first few steps, then nothing.  A cursor at the top left corner of the screen flashes for a few seconds or so, then disappears leaving only a black screen. 

 If I start Ubuntu in graphics safe mode then eventually an orange screen appears, but no action is possible.

The boot disk works well, I tested it on my new HP laptop and got Ubuntu to run.

---

### Post by PmDematagoda on 2007-10-15
I think this may be your problem:-

> Using an S video cable into a TV

I think you may have to configure your xorg.conf file to use the S-video port instead of the normal VGA one, try the Ubuntu alternate CD to see if you can install it, after that we can get on to configuring the X-server properly.

---

### Post by WhatYouNeed on 2007-10-15
I was not sure if that would effect Ubuntu   Too lazy to go to the storage room and get a monitor.  I will try installing it with a monitor first. 

Thank you.

---

### Post by WhatYouNeed on 2007-10-15
Ok, it appears to be trying to load now.  Not sure what is meant by "some time" in the installation guide.  Ubuntu has been working for about an hour and 15 mins now.

Got error message at the beginning that Gnome had some errors and that some themes may not run.

Not sure if that is causing the extreme slowness.

The Nautilus toolbar or thingy at the beginning is as far as Ubuntu has loaded.

---

### Post by WhatYouNeed on 2007-10-15
I have no idea what I am doing wrong here.  Using a regular monitor now, not the S video.  Still getting the same error message about the Gnome.:mad:

---

### Post by PmDematagoda on 2007-10-16
Do you get to the desktop? 

I got the Gnome error message myself when I used the Live CD and it went away after I installed it. So you should not have it after installing Ubuntu.

---

