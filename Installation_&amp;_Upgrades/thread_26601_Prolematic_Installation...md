---
title: "Prolematic Installation.."
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by Sabih on 2005-04-13
I just installed Ubuntu on my system, dual booting it with Windows XP, and when attempting to login to Ubuntu, it alerts me that its unable to load Xserver and leaves me at the command line prompt.. when i attempt to login via command line, it doesnt open the GUI at all.. I have no idea what to do from here

Could someone please help me load the GUI and get properly into Ubuntu.

Thankyou :)

---

### Post by heimo on 2005-04-13
Hi!

I'm not sure, but probably you have messed up resolution settings and need to fix those on command line. It can be something else too, so some more information would be nice. (EDIT: Oh, I don't mean that YOU have messed up, I think your system has wrong settings and autodetection didn't work!)

Logon to command line and try running 
startx

Pay attantion to errors and warnings. If the output scrolls out of screen, you can hold down shift and hit Page Up to scroll up. Do you see "No screen found" or something similar?

You can also check the same information with *less /var/log/Xorg.0.log* (q to quit).

You can find some information about fixing the xorg.conf here: (some of it is not possible on command line, I think)
[http://www.ubuntuforums.org/showthread.php?t=21984](http://www.ubuntuforums.org/showthread.php?t=21984)

You could view the xorg configuration file *less /etc/X11/xorg.conf* and send us the Device and Monitor sections and 10-15 lines from Screen section. And if you can describe your hardware - monitor and graphics card or the make and model of your computer, that'd help too.

---

### Post by Sabih on 2005-04-13
I am running -  AMD Athalon  XP 2600+ (2.09GHz) CPU
                     - 512MB RAM
                     - 120GB HDD
                     - Radeon 9200 graphics card

I think you are right about the screen resoloution being the problem, as when i was looking at the installation screenshots on this website, the next screen i should have got upto was picking my resoloution but i never got to see that screen.

---

