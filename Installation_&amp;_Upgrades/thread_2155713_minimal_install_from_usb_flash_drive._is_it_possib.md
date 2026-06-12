---
title: "minimal install from usb flash drive. is it possible?"
date: 2013-06-19
forum: Installation &amp; Upgrades
---

### Post by innn on 2013-06-19
I've installed ubuntu one day ago and decided LXDE is for me and proceeded to uninstall unity and stuff but afraid risking the stability of the OS I would like to reinstall with the minmal version and apt-get my way towards LXDE.

Is it possible to install from usb flash. that is my only option.

---

### Post by MidnightGrey on 2013-06-19
Lubuntu is the distro you're after.
Its built on ubuntu replacing unity for LXDE.

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by Paqman on 2013-06-19
Yep, you can use [unetbootin]("apt:unetbootin") to get the minimal image onto a USB stick. You can't use the normal USB disk creator tool that Ubuntu comes with.

---

### Post by innn on 2013-06-19
> **Paqman said:**
> Yep, you can use [unetbootin]("apt:unetbootin") to get the minimal image onto a USB stick. You can't use the normal USB disk creator tool that Ubuntu comes with.

I get it that by normal usb disk creator that ubuntu comes with is the dd command.

Yep, didn"t work,

I have to try the unetbootin.

---

### Post by Paqman on 2013-06-19
> **innn said:**
> I get it that by normal usb disk creator that ubuntu comes with is the dd command.


Dd is a command line tool that's installed by default, it can do lots of stuff and could be used to set up a USB stick, although it's a bit of a messy way of doing it. The tool I referred to is a GUI application called USB Startup Disk Creator (or some such). It can be used to put normal Ubuntu images onto a USB stick, but doesn't work for a minimal image.

---

### Post by Bucky Ball on 2013-06-19
*Thread moved to **Installation & Upgrades**.*

Go for it. For the minimal install, you will find this helpful:

[http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24)

You have two choices at the first set of options; terminal install or regular install. Choose the top one; install.
Eventually you have two choices; you can pick a machine profile (something that suits what you use your machine for and suitable software) or install software manually (selection at bottom of the list). I did the latter (did a mini install two days ago and typing from it now!). 

When you've finished the install, take dongle out (I presume), reboot to the hard drive and you will get to a cursor. Simply:

```
sudo apt-get install lxde lxterminal pcmanfm gcc synaptics update-manager network-manager apt gksu thunderbird firefox evince gimp
```

I had my list scribbled on a bit of paper which I now can't find, but there are some essential things the line above is missing and you will need. You will remember things you use and find things you need as you go, but as you have Synaptics and a terminal you'll be able to install what's missing. This list should get you up and running to that point. You could rip out almost everything from that list bar lxde if you like and really take a roller coaster learning curve!  

Something like the above suits me but maybe not you so do some planning and make a list first. You might spend a bit of time on a minimal and need to do some research to get it right, but you learn a bit and it's worth it.

PS: You will get to a section where you install grub. If you are dual-booting the mini (and the stable OS is running the grub on /sda) then unless you want the minimal install to overwrite that and run the show, install its grub to the same partition you are installing the mini or not at all. 'sudo update-grub' in the stable install when you have finished the mini install. ;)

PPS: If you have valuable data on any of the partitions, back ... it ... up.

---

### Post by innn on 2013-06-19
> **MidnightGrey said:**
> Lubuntu is the distro you're after.
Its built on ubuntu replacing unity for LXDE.

[http://lubuntu.net/](http://lubuntu.net/)



thanks, I did eventually that and I like it more than Ubuntu :) 

=distraction-free.


@paqman

I got it you were talking of a tool I wasnt aware until now not being accustomed to ubuntu.

I did however tried ```
dd if=/home/username/Downloads/mini.iso of=/dev/sdc
``` and it actually worked. I had a bootable usb.

During installation I didnt pay attention to the fact that grub wanted to install to a sdb (being the thumbdrive) instead of a sdc (being my hard drive )
Now its working.

---

### Post by Bucky Ball on 2013-06-19
PPPS: Do it with a cable plugged in rather than wireless. Wireless can be problematic. The install depends on a solid connection to the net. 

PPPPS: In case you missed my last post #6, have a read. ;)

---

### Post by Bucky Ball on 2013-06-19
> **innn said:**
> 

While installing I mounted some ntfs partition in /windows and get those errors in mounting it that Ive becomed well acquainted with these two days pressing 3 times the S key to skip

Do you know how can I mount it --even read-only I wouldnt mind? 

 It could be that I left windows 8in a hibernated  state I can not remember and I do not have windows now anymore.

Post that in a new thread with a related title rather than here. Try and include as much info as possible (a link to here if you like). Two issues in one thread gets confusing, dilutes community effort and actually reduces your chances of getting help as the thread title has nothing to do with your new issue. 

Please mark this thread as solved by following the link in my signature. Thanks. ;)

PS: You might try searching for 'mount ntfs ubuntu'. There's a lot of information out there. Let us know what's confusing. ;)

---

### Post by innn on 2013-06-19
> **Bucky Ball said:**
> 

You have two choices at the first set of options; terminal install or regular install. Choose the top one; install.
Eventually you have two choices; you can pick a machine profile (something that suits what you use your machine for and suitable software) or install software manually (selection at bottom of the list). I did the latter (did a mini install two days ago and typing from it now!). 

I went with the lubuntu minimal profile. It suits me. No problems installing software manually but the installer dumped me inside aptitude in the second case.
 Didn't like it. Barely found the quit button. :) 

Thank you kindly for your help.

---

### Post by sudodus on 2013-06-20
> **innn said:**
> thanks, I did eventually that and I like it more than Ubuntu :) 

=distraction-free.


@paqman

I got it you were talking of a tool I wasnt aware until now not being accustomed to ubuntu.

I did however tried ```
dd if=/home/username/Downloads/mini.iso of=/dev/sdc
``` and it actually worked. I had a bootable usb.

During installation I didnt pay attention to the fact that grub wanted to install to a sdb (being the thumbdrive) instead of a sdc (being my hard drive )
Now its working.

Thank you for finding out that the mini.iso cloned to USB works now :KS

A dd-cloned USB pendrive of the version 12.04 of mini.iso booted but did *not* work all the way a couple of weeks ago (and probably still does not work). I was encouraged by your post and downloaded ***mini.iso ******version 13.04 (32-bits)***, cloned it to a USB pendrive with dd and installed a working Lubuntu minimal system :-)

I will edit my [tutorial]("http://ubuntuforums.org/showthread.php?t=1958073") to encourage people to clone the mini.iso (using a shell-script to make it safe).

---

