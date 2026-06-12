---
title: "Install from boot menu"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by danny1990 on 2012-01-24
Can anyone tell me how i can install from the boot menu rather then going into the live cd mode then install currently I'm trying to install ubuntu 11.10 but i've been stuck on the home screen for around 20 minutes the desktop bar is showing and the background picture is showing but the mouse icon is showing that it is loading my patiance is wearing thin and i'm getting tired looking at it going round and round 

I'm wanting to install unbuntu as the only os and not duel boot

I havn't tried ubuntu since 6.06 the installation with that was perfect i never had any problems with installation or anything

I have searched around but i cannot find anything for what i need to do

Any help is appreciated, Thanks

---

### Post by drs305 on 2012-01-24
If you have the Ubuntu iso on an accessible partition, have a working Grub 2, and want to run an Ubuntu installation ISO from the Grub 2 menu, here is a link describing the process. Not sure if that is what you are looking to do, so if it isn't please elaborate.

[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

Note that this will work from a normal grub menu, not just the rescue prompt. To get to the prompt from a Grub 2 menu, press "c".

---

### Post by danny1990 on 2012-01-24
I don't have ubuntu installed yet, I have downloaded the ISO and burned it on my last cd, the cd is fine it was fresh out the box it came in

What i mean is when i boot from the cd i want the option to install and not load into live cd

when i boot into the cd it just loads the live cd, I've tried holding shift and i selected install but it just booted into live cd

---

### Post by sudodus on 2012-01-24
I suggest that you really take advantage of the possibility to run Ubuntu live from the CD drive. This way you can test if it works, and if you wish, you can test some other version (different release date) or flavour (different desktop environment but still Ubuntu).

Then when you feel that you like it and want to install, it is easy. You want Ubuntu as the only operating system. Simply press the install icon on the desktop, and it starts the install wizard. When asked how to use the hard drive (partitioning), select to use the whole drive for Ubuntu, and you will get it.

After the installation has finished, select reboot (and remove the CD from the computer), and you will boot from the hard drive using grub.

---

### Post by drs305 on 2012-01-24
If you aren't able to run or install Ubuntu, you might have the option to change some of the CD startup options during the early portions of the boot. Pressing the F6 key, for instance, can change some of the kernel options (users having video problems may have to use the 'nomodeset' option, for instance).
Here is a link regarding some of the options:
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")


Depending on what you see while it boots, you may also be given the option to check the disk.

If you can't get that specific CD to boot, you may want to try redownloading the ISO and burning a new CD. Or you can try the Alternate CD, which sometimes will work when the normal CD does not.

---

