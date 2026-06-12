---
title: "Problem with SATA drive"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by JamesDMitchell on 2007-03-24
I've been trying to get a version of Linux to work, the main reason is to repartition my windows drive without paying for partition magic or something like that!

I've got the 6.06 LTS live CD and when I ran that and ran gparted it said no devices found.

I've done a fair bit of searching and found threads such as [this one about Dell 1501s]("http://ubuntuforums.org/showthread.php?t=375886") and they suggested trying pci=nomsi - I tried that and it made no difference.

It's a 160GB Western Digital SATA drive.

I'm downloading a gparted live CD now but I'm not massively optimistic that that will work.

Anybody know how to get this working?

Thanks,

James

---

### Post by Scunizi on 2007-03-24
Even though you don't have raid going, I found doing the following neccessary with my sata drives. I found this information [here.]("http://www.ubuntu.com/getubuntu/releasenotes/606#head-f0fc50174e566788f02aa164fb6e80aa9c65ee24")

> If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer.

---

### Post by JamesDMitchell on 2007-03-24
Thanks Scunizi but no joy...

When I did sudo vgchange -a n I got No volume groups found and I'm still getting no devices found in gparted.

I'll try the gparted live cd...

---

### Post by Scunizi on 2007-03-24
Ok... since you mentioned Dell in your original post I assume that your's is also a Dell.  When you finally are able to discover the drive with something be careful.  Dell sometimes puts a hidden partition on the drive.  You will need it if you ever want to install windows again from their rescue CD's.  The CD will typically look for that hidden partition to validate the install.  Don't delete the hidden partition.

On another note, have you been into the bios and looked at how the drive is configured?  Is it the first drive in sequence?  What kind is it and how old?  Are you able to take it out and test it on a desktop? If you can get to it disconnect the sata connectors and reconnect them a few times just to buff the contacts so you'll have a solid connection.  

After re-reading your post it almost sounds like you already have a functional copy of windows on the machine and you're trying to create a dual boot situation.  Is that right?  If so disreguard the previous paragraph.

---

### Post by Gilgad Drumheller on 2007-03-29
All i've got to add is the massively unhelpful: I've got the same problem!
closest thing to a fix i can find is this: [http://ubuntuforums.org/showthread.php?t=388032](http://ubuntuforums.org/showthread.php?t=388032)
However, with the liveCD and whatnot, i'm not sure what requires a reboot (and thus wouldn't work)

To give more info about the problem, i have two SATA disks, 2 raid controllers (both disabled), and blank screen inside gparted.  Additionally, fdisk -l returns nothing (just goes down to the next line)

---

### Post by Scunizi on 2007-03-29
The live CD's will not see your harddrive without mounting them unless you are going through the install process in which case Ubuntu uses (or use to) Gparted.

---

### Post by Gilgad Drumheller on 2007-04-02
Yea, neither gparted nor the installer sees any hard drive.
I've heard it could be a problem with herd5, so i'll be testing others.

---

### Post by hyperian on 2007-04-02
try disabling sata native support

---

### Post by Gilgad Drumheller on 2007-04-04
tried -> failed
I hear this is a unresolved bug, but i have no idea when its will be fixed.
*sigh*

---

