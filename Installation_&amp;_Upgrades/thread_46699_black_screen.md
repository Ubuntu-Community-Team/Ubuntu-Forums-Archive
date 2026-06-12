---
title: "black screen"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by sisya on 2005-07-05
help me....

i installed ubuntu 5.04 just now and it seemed to go smoothly...just when the install seemed to have finished the screen went black/blank, with just a underscore blinking at the top left corner.  mouse doesnt work keyboard doesnt work...nothing works


i restarted the comp and it rebooted and it came right back to the same black screen

cd is not faulty coz i installed from the same cd and it worked like a dream

and yes i've got nvidia

so someone help...tell me is there a safe mode or recovery mode or something...

dont just ask me to type some fancy commands coz i already told u...i only end up at a blank screen kb and mouse dont work and i dont see anything.

---

### Post by lonboy on 2005-07-05
Does this blank/black screen occur before the system reboot (before all the packages are configured) or after all of the packages have been installed and configured? Sounds like a bootloader issue. Maybe use fdisk to clean your MBR before you install.

---

### Post by sisya on 2005-07-05
when i install there comes a point where it says remove the cd from the drive and then it continues into the 2nd stage of installation....

all that goes smoothly except at the end of the 2nd part of install it just goes blank....so i reboot it..hard reboot using the button on the cpu tower...and it starts rebooting....grub loads and ubuntu is default so it continues and starts booting...except after booting it comes back to the blank/black screen

i tried booting into the recovery mode...but it takes me to some # prompt...i dont know what to do from there

---

### Post by mwaddoups on 2005-07-26
bump

Same thing happened to me...after installation it went thorugh the second stage, and when it finally reached "Stopping Gnome...Starting Gnome" I also got the blank screen with the blinking underscore, which stops blinking and it crashes. I also noticed if I use "apt-get install gnome" in the recovery mode, It says this package is depended upon, but either missing or..." something else. Could this mean gnome never installed properly, and if so could someone give me some step by step instructions on how to install it again by the recovery mode. I am running Ubuntu in dual boot with XP, partitioned in an extended partition with 6gb of ext2 and 600mb of swap. I also tried "apt-get install xfce" but this package was not found. I am using a wg121 wireless netgear usb adaptor for internet which is no immediately compatible with linux without using ndiswrapper, so I have no internet access if this could be a problem. Could someone please coem up with some suggestions, as this is my first time trying Ubuntu and it sounds so good, I don't want to leave it and go to fedora (which is what I am considering). Please help!

---

### Post by mwaddoups on 2005-07-26
:| please help me! I really need help with this as I have tried reinstalling Ubuntu 4 times and to no avail. Just an idea is all I need...

---

### Post by loeboy on 2005-07-27
This may be a longshot... Do you have two video cards in your computer? We had a similar problem at work with one of the computers which had two video cards (onboard and pci). We could see all of the text scroll by when booting, but the monitor would go black before loading up X. It seemed that X would get confused on which display to use. We ended up removing the pci card and used the onboard video. Everything works fine now.

I wish you luck on finding the solution.

---

### Post by delirium on 2005-07-27
I had the same problem (2 video cards).  

First log on into recovery mode and use the command lspci to see all the cards you have installed.  Then edit xorg.conf in /etc/X11/  to get it to work.  Post if you need more specific questions.

---

