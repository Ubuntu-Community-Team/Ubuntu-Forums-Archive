---
title: "Can not install Ubuntu GNOME"
date: 2017-03-07
forum: Installation &amp; Upgrades
---

### Post by aalkouri on 2017-03-07
Hello all.

I installed Ubuntu years ago and enjoyed it, however, because of various reasons, I stopped using it, and linux in general.

I just got back from Scale and was super pumped up to get back into Linux so I decided to try out on my main desktop at home.

I installed a USB live installation, but for whatever reason, I can not get it to install all the way.

The installer will get to the very end and give a "Bootloader install failed" error.  It gives me 3 options, but no matter which option I pick, nothing happens:


[ATTACH=CONFIG]274030[/ATTACH]


At first, I thought it was because I have a unique hard drive (PCI SSD in RAID) so I unraided it, then tried installing it, still same issue.  I also completely wiped my backup SATA SSD and tried installing there, still, same exact issue.

What could possibly be the problem here?

Couldn't find anything online for this issue.

Any help would be appreciated.

---

### Post by adedamoo-ab on 2017-03-07
What did you use to make the usb a bootable usb?

Make the usb a bootable device(you can use Rufus for this), restart your system and let the system boot from the usb drive...
I hope this helps.

---

### Post by aalkouri on 2017-03-07
> **adedamoo-ab said:**
> What did you use to make the usb a bootable usb?

Make the usb a bootable device(you can use Rufus for this), restart your system and let the system boot from the usb drive...
I hope this helps.

I did use Rufus.  It seems to work with live, but I can't install the OS to the hard drive.

---

### Post by adedamoo-ab on 2017-03-07
Are you installing it on a system as the sole OS or to reside with another OS on the system. 
Are you formatting the drive during installation?

---

### Post by Bucky Ball on 2017-03-07
Install the bootloader to sda, not sdb. ;)

Doesn't look like the OS is not installed, just looks like it's having an issue installing the boot loader.

You can choose to 'Continue without bootloader' but after that you would need to boot to a live session and use Boot Repair to install grub (see red link, first line of my signature).

Hard to give much more advice without more details of your setup. Does sdb exist, have you got two drives in the machine, are you dual-booting?

There is no reason to burn another USB at this point as it doesn't look like it has anything to do with that. Odd that it's defaulting to install grub to sdb, though. Are you choosing 'Something Else' and partitioning manually or choosing one of the auto installs? If 'Something Else', you can choose where to put grub from there. It is normally sda.

---

### Post by aalkouri on 2017-03-07
> Bucky Ball;13616933]Install the bootloader to sda, not sdb. ;)

You can choose to 'Continue without bootloader' but after that you would need to boot to a live session and use Boot Repair to install grub (see red link, first line of my signature

Choosing any of the options does nothing, nothing happens.

> Hard to give much more advice without more details of your setup. Does sdb exist, have you got two drives in the machine, are you dual-booting?

I have a PCI SSD hard drive in RAID striped that I completely formated.  For troubleshooting sake, I disconnected by other 2 SATA SSDs so I currently have no other Operating Systems on my machine and no other hard drives but this in-line RAID hard drive.
> 
There is no reason to burn another USB at this point as it doesn't look like it has anything to do with that. Odd that it's defaulting to install grub to sdb, though. Are you choosing 'Something Else' and partitioning manually or choosing one of the auto installs? If 'Something Else', you can choose where to put grub from there. It is normally sda

I tried various combinations, I tried doing the "something else" but it was very confusing and I didn't know how to proceed.

Here is the previous error though:

[ATTACH=CONFIG]274031[/ATTACH]

---

### Post by aalkouri on 2017-03-07
> **adedamoo-ab said:**
> Are you installing it on a system as the sole OS or to reside with another OS on the system. 
Are you formatting the drive during installation?

I am formatting the drive during installation, I want to use it as a sole OS.

---

### Post by Bucky Ball on 2017-03-07
Probably because you have it set up as a RAID drive. That changes things and can't help you with that, sorry.

---

### Post by aalkouri on 2017-03-07
[ATTACH=CONFIG]274033[/ATTACH]

Here is the "Something Else" option, how am I even supposed to make sense of this? 

Can someone point me to some documentation?

What is ext4 ext3 etc?

---

### Post by Bucky Ball on 2017-03-07
They are file types. Making head or tail of it would you did some research about this. There is lots of info about partitioning with 'Something Else', what an EXT* partition is and also what the 'mapper' entry against all of your partitions means. 

Your partitions all have 'mapper' next to them which either means they're RAID partitions, encrypted, not sure which as know nothing about either, as mentioned, sorry. Not sure why that is the case. All I can help you with in this case is wiping the lot with gparted, and you might not even be able to do that with all I, personally, know.

One thing is known. You appear to have successfully installed 16.04 LTS twice, both with their own /swap partitions. That is not necessary, but also not what you intended either I wouldn't think.

You could try fixing with boot repair, but not sure if that would work with these partitions. First line of my signature, red link.

Good luck with it.

---

