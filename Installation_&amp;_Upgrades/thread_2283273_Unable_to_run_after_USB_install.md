---
title: "Unable to run after USB install"
date: 2015-06-20
forum: Installation &amp; Upgrades
---

### Post by Thomas_Darby on 2015-06-20
I am new to Ubuntu, although I tried it years ago on a live CD. I downloaded an ISO, placed the installer software on my USB (over 12 GB free), then began the package installation. It seemed to work perfectly. However, every time I do the full install (I've tried various ways), when I get to the button that indicates a restart is needed, I hit that, and one of the following happens: It restarts and boots from the USB as a Live session; or, if I remove the USB before restart, it hangs at a black screen with obscure wording and a prompt; or, if I remove the USB too early, I get the BSOD (Brown Screen Of Death) and have to shut the computer off.

I'm running this on my older laptop as an experiment before I switch my newer one. I wrote over my old XP install, and have a Dell D-610 with 2GB RAM, 250-GB HD, unknown processor (Intel Centrino).

I want to be able to use Ubuntu without the thumb drive installed. Please tell me what I'm doing wrong. I'm an old goat, my favorite video game is Pong, OK? So a little help will make my day.

---

### Post by Bashing-om on 2015-06-20
Thomas_Darby; Hello;

What we often see in the case of a USB install is that the bootloader (grub) gets installed to the USB drive, as by default this code is installed to 'sda' and many times this 'sda' device is recognized by the system as the USB drive ; rather than the desired target hard drive.

So, lets take a look at what is:
Boot up the liveUSB to "try ubuntu" ubuntu mode and post back the results of terminal commands:
```

sudo fdisk -lu
sudo blkid

``` and we see what the system sees for the hard drive identification and then ->
we direct where to install the boot code - using the liveUSB to do so .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]computers can be real stupid
[INDENT][INDENT][INDENT][INDENT]they only do what we tell them to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

And a hearty Welcome to the forum !

---

### Post by ajgreeny on 2015-06-20
When you are installing Ubuntu to a disk other than the hard disk in a machine, and particularly to a USB which may not always be attached, you really must choose "Something Else" and then at the bottom of the partitioning page you will see a dropdown box allowing you to choose where to install bootloader files.  You must make sure you choose the root of the USB disk, ie /dev/sdx (make sure you know which disk is which) and **do not put the bootloader on to a partition**, ie /dev/sdx1

---

