---
title: "Ubuntu OS upgrade using terminal"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by btophek on 2012-10-22
Is there a way of using the terminal only of upgrading an older version of Ubuntu to something more current?  Say 9.04 to 12.04?  Tried using the CD's unfortunately I usually get  "unrecoverable loading error" or the computer will just freeze up while loading the OS into memory.

---

### Post by ~LoKe on 2012-10-23
Personally I wouldn't update from such an old release to a new one.  You might run into some trouble.  Re-installing with a USB drive would be best.

But if you can't and you absolutely want to try, edit /etc/apt/sources.list and replace your repo's with the current ones.

---

### Post by 2F4U on 2012-10-23
You cannot directly upgrade from 9.04 to 12.04. In theory, you could go 9.04 -> 9.10, then 9.10 -> 10.04 and finally to 12.04. But it would probably be much faster, saver and easier to do a fresh install.

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)
[https://help.ubuntu.com/community/EOLUpgrades/Karmic](https://help.ubuntu.com/community/EOLUpgrades/Karmic)
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

### Post by btophek on 2012-10-23
The problem I run into using CD's is the bios is old and interferes with the upload.  According to the iso image readme notes there is a way of by passing the bios during an install.  However, I don't have enough experience to know how to do this.  The readme notes explain this but I don't understand. I don't know if using a usb port install would be any different than a cd install?

---

### Post by jerrrys on 2012-10-23
Another possibility would be a terminal only install.  This could be done with the mini.iso which is a very small download (something like 30MB).

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You would then load the ubuntu desktop directly off the internet.  Which would take a while, but may serve as a work-a-round in your case.

Do you have any files that need to be kept?  Could you do this install on a new partition?

And what are your specs?  CPU, speed, ram, video?  May be that Ubuntu is too much for your old box and would be better to go with something else.

---

### Post by btophek on 2012-10-23
All the files on the hard drive that I wanted I saved onto a external hard drive, music, photos etc.    The hard drive has been freshly formatted.  There is nothing on it.  It used to have 12.04 Ububtu on it now I can't load anything greater than 9.04 without experiencing problems.   I'd like to update my bios first except in Gateway's web site it's hard to find the bios update for my machine and of course they want to charge you for their assistance.  

I have never tried a minimial CD install?  I'm wondering how this would work?

---

### Post by jerrrys on 2012-10-23
You neglected to post your computer specs.  So assuming that you can run 12o4 you would:

#1  Install the 12.04 mini.iso (terminal only install) and reboot.  If the reboot  option is not given to you, enter:

sudo reboot

#2  You would then reboot to a blank screen with nothing but a blinking cursor.  You would then press:

Ctrl + Alt + F1

And then enter:

sudo apt-get install ubuntu-desktop

This will give you the full ubuntu desktop and being a 600+MB download, it will take a while.

There are many ways to use the mini.iso, but I think this would be the simple way to go for you.

If you are running 1gig of ram, dual core and a good video card; you should be good to go.  Less than that will give you a performance hit.

Edit;  Here's an example

[http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24)

---

