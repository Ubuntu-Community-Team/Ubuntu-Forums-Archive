---
title: "Black/blank screen when booting off CD"
date: 2011-12-25
forum: Installation &amp; Upgrades
---

### Post by jebriggsy on 2011-12-25
Hey guys, I need some help.

I have an HP Pavilion g6-1b59wm laptop.  It has a dual-core 64-bit AMD processor and integrated ATI graphics. Got it for Christmas :)

I'm trying to install Ubuntu 11.10 for 64-bit architechture.  It starts working, see the ISOLINUX message.  It gets to what looks like a GUI - a purple background and two symbols at the bottom (nothing else) - and then seems to load a little more before the screen turns black and I am forced to force shut down.  I haven't tried using the alternate installer because I fear that the problem might be a little more in depth than just a GUI-based OS install (I mean, this is a Win7 box, new tech and etc).

So what do you think?  Need moar info?  Use 32-bit instead (would rather not :/ )? Alternate install + custom configuration of x.org or something similar (I would need help with this)?

Much thanks!

---

### Post by BC59 on 2011-12-25
Can you boot with the installation CD and reach to the screen Try Ubuntu?

---

### Post by jebriggsy on 2011-12-25
No, the screen turns blank/black before I reach that point

---

### Post by BC59 on 2011-12-25
If you hold down SHIFT during boot, can you reach the Grub Menu?

---

### Post by jebriggsy on 2011-12-25
Holding SHIFT brought me to the screen with try/install/check and etc!  Are there any special options I should use before continuing?

---

### Post by BC59 on 2011-12-25
In such a case go on with the installation.

---

### Post by jebriggsy on 2011-12-25
Both "Try Ubuntu without Installing" and "Install Ubuntu" have both resulted in the original problem - blank/black screen.  I've tried both with the acpi=off option (as I've encountered similar problems before and setting that option helped) but it didn't work.  Any suggestions?

Thanks again

---

### Post by BC59 on 2011-12-25
The best thread about this problem is here:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by jebriggsy on 2011-12-25
Thank you.  Using the nomodeset option allowed me to get further into the installation process.  I was able to see the GUI being loaded.

However, I now have errors to report, which are keeping me from moving forward in the install process.  Here is what is output to the GUI loading screen (Ubuntu 11.10 with 4 dots under it) about 85 seconds in (if the numbers between brackets before the errors themselves are timestamps as I believe them to be)

Bad LUN (0:1)
Bad target number (1:0)
Bad target number (2:0)
Bad target number (3:0)
Bad target number (4:0)
Bad target number (5:0)
Bad target number (6:0)
Bad target number (7:0)

And then there was an error whose full text was not completely discernible as some of it appeared behind the loading animation and other errors.  The gist of it was:

saned disabled.  edit (filepath obstructed by gui) saned.conf

EDIT: After displaying these errors the GUI crashes and I'm left with the CLI Linux interface

---

### Post by BC59 on 2011-12-25
Very strange...I could only suggest you to try again. Do you use USB or CD to boot?

---

### Post by jebriggsy on 2011-12-25
I posted after trying a few times hoping it was a hiccup >.<  I'm using the CD to boot

---

### Post by BC59 on 2011-12-25
You could try downloading another .iso and making a USB pendrive bootable. You can make it with the program Unetbootin through Windows. Try to install Ubuntu with this pendrive.

---

### Post by duckegg12 on 2011-12-26
I have the same problem as Jetbriggsy in trying to install Oneiric. The same thing happened with Natty and Meerkat. Black screen and end-of-story "after the "choose monitor resolution" screen
The range of available resolutions in the install program doesn't go up to 1920x1080 which is my Samsung BX 2440 monitor.
I looked up the vesa codes for 1920x1080 and found vga=283, but install wouldn't accept that.
When I use the 'nomodeset' parameter via F6 the live disc/install process starts up in something called 'Easy Peasy' version 1.6, which seems amazing, and is useless because its only install option is to install Easy Peasey 1.6 which looks like a primitive netbook interface. Not something I want with my PC - Nvidia GT9800 graphics card and a i7 cpu. 
All this happend with Natty and Meerkat also.
For comparison I tried to install PCLinux OS and it ran and installed with no problems. I conclude this means there is a problem in the Ubuntu installer with higher-resolution monitors...?
Surely someone else has encountered this?

---

### Post by BC59 on 2011-12-26
You could try another option. Install the minimal CD:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
After the installation you can install full Ubuntu if you like.

---

### Post by BC59 on 2011-12-26
Another solution would be the Alternate Installation:
[http://www.ubuntu.com/download/ubuntu/alternative-download#alternate](http://www.ubuntu.com/download/ubuntu/alternative-download#alternate)
In that case maybe you will need the help of the forum, because the alternate is more complicated than the normal installation.

---

### Post by duckegg12 on 2011-12-29
Thanks, BC59.
I did an install using the minimal disc, using my 1920x1080 monitor.
The install was visible on the screen throughout and seemed to have proceeded OK.

However, when I re-booted I received the black screen and my monitor 'on light' started blinking - which means it wasn't going any further.

So, I took an old 1280x1020 monitor out of the cupboard, substituted it and re-booted. The result was OK-normal. The new install was all there and visible. So I installed the NVIDIA proprietary driver.

Then I put back the 1920X1080 monitor and it booted and displayed OK !!

So I now conclude that Ubuntu fails to detect some higher-resolution monitors, and my Samsung BX 2440 is one of them.

It would be interesting to know the experience of people with other 1920x1080 (or higher) monitors !

---

