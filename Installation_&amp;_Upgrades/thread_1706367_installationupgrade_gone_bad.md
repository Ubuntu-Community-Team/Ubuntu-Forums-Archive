---
title: "installation/upgrade gone bad"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by bearclaw50 on 2011-03-13
I have been using ubuntu 9.04 from my desktop for 6 months using an ethernet cable. I installed ubunto 9.04 on my laptop and it went well, however I could not get the wireless to work. I put a ubuntu 10.10 disk into the laptop computer (Toshiba satellite L655) attempting to upgrade. During the process I got an error message, something about not getting all the packets or something to that effect. I continued with the upgrade and now I have a mess.  I don't get a GUI or prompt to enter my user name and password when I turn on the computer, just a bunch of text.    starting up: mount: mounting none /dev failed/ no such device  w:dev tempfs not available, falling aback to tmpfs.    then it goes to this.....    fsck from util-linux-ng 2.17.2 /dev/sda1 has been mounted 36 times without being checked, check forced. Your disk drives are being checked for errors, this may take some time  Press C to cancel all checks currently in progress.     and it just stays like this.  I have nothing on this computer, is there something I can do to just start all over. I attempted to put the disk back in hoping for a chance at a fresh install, but no such luck.

---

### Post by mörgæs on 2011-03-13
Hi, welcome to the fora.

A clean install of 10.04 or 10.10 is the way to go. 

Have you changed the boot order in BIOS, so the computer will boot from the CD drive?

---

### Post by bearclaw50 on 2011-03-13
No I have not done that, and I don't know how to do that.  any suggestions?

---

### Post by Hedgehog1 on 2011-03-13
bearclaw50,

To change the boot order on a computer, you need to get into the BIOS setup.  When you computer first powers up, there is typically a little text saying things like 'Bios=F10' down low on the screen.

The exact key varies between manufactures, I have see 'DEL', F1, F10, F9...

On your laptop - is this a dual boot, or an Ubuntu only install?

***The Hedge***

:KS

---

### Post by bearclaw50 on 2011-03-13
It is Ubuntu only.  I changed the boot order to CD and got the install Ubuntu going.  Looks like this is going to work. :D:D:D

---

### Post by bearclaw50 on 2011-03-13
installation appeared to go great.  However, when I restarted after the install, still no GUI.  I get
Ubuntu 10.10 bearclaw tty1
bearclaw login:
password:

I enter my username and password and nothing happens.

---

### Post by Hedgehog1 on 2011-03-13
> **bearclaw50 said:**
> installation appeared to go great.  However, when I restarted after the install, still no GUI.  I get
Ubuntu 10.10 bearclaw tty1
bearclaw login:
password:

I enter my username and password and nothing happens.

Did you load the server edition? That edition has no default GUI.  If you did install the server edition of 10.10, please download and install the desktop edition of 10.10.

If you **did** load the desktop edition of 10.10, please download the 10.04.02 desktop edition and install that.  We need you to have a working Ubuntu, and the 10.04 is very good, too (and has fewer video driver conflicts AND long Term Support).

***The Hedge***

:KS

---

### Post by mörgæs on 2011-03-14
Yes, 10.04.2 is good, but before flushing 10.10 you could try to add boot options:

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by amyrg32 on 2011-10-15
I also have upgraded, but i have a different problem. My computer is stuck on the black screen where the system verifies that all things are properly working. I have restarted the computer, but at this point thats all I know to do. If antone could give me some advice i would be very gratefull. 
Thanks 
AmyG

---

### Post by amyrg32 on 2011-10-15
I also have upgraded, but i have a different problem. My computer is stuck on the black screen where the system verifies that all things are properly working. I have restarted the computer, but at this point thats all I know to do. If antone could give me some advice i would be very gratefull.

---

