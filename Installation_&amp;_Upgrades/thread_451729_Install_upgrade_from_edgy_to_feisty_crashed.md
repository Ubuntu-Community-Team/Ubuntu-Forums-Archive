---
title: "Install upgrade from edgy to feisty crashed"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by Magicalturkey on 2007-05-22
I originally installed Ubuntu 6.06lts yesterday from a disc I received in the mail.   I installed envy to install the proper nvidia drivers in an attempt to use dual screens with my tv to play movies.
I thought i had read that it will not handle well with upgrades somewhere during the install.  

Overnight I upgraded 6.06 to edgy 6.10, using the update manager included with the system, it appeared to work well, and it then finished and restarted. 

Once it restarted it was unable to go back to the gui of Ubuntu, instead popping a screen up saying the xserver is unable to start.   So i restarted the machine to try and see if it was just a glitch and somehow it worked.  
I didn't attempt to fix it as it started up.  I may have selected the next one down on the menu when booting, though. 

I then set about updating the system to the newest build 7.04 feisty, using the same method.  it worked well until it finished downloading all the files and started installing them.   Once it started installing the packages it crashed and it took me to a black screen and i reset it. 

Upon restarting i couldn't get anything to start up and kept getting the xserver error.  I searched the forums here and used:
sudo dpkg-reconfigure xserver-xorg
to reconfigure the nvidia drivers. 

This worked and allowed me to start up the previous build.  Now it tells me when i click on the update to try and fix it the first error that shows up is "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem" 

Then when i click close on the error message it tells me "Could not upgrade the system!
Fix broken packages first."

Also i clicked on show updates and a pop up dialog tells me that "Not all upgrades can be installed, Run a partial upgrade to install as many as possible."  and it gives me a button that says partial upgrade.  However once i click on it it closes it all and does nothing. 

I am unsure how to do this, any help would be appreciated.  I am a total newbie to linux, but i am excited to figure out all this. 

Thanks in advance. 
-Mark :D

Edit: I am running an AMD64 processor and using the 64bit versions of Ubuntu

---

### Post by zvacet on 2007-05-22
Programs<accessories>terminal

```
sudo dpkg --configure -a
```

---

### Post by Magicalturkey on 2007-05-23
haha Thank you, I guess it was simpler than i thought.

---

