---
title: "Booting grub from a partition"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by Lars Noodén on 2008-08-09
I'd like to install grub on /dev/sda5 instead of the MBR for /dev/sda

How can that be done?

I've tried changing /boot/grub/device.map to include
   (hd0,4) /dev/sda5

and then run 
   grub-update /dev/sda5

However, that gives, after a  long pause, the following error
   GRUB GRUB Hard Disk Error

after which the machine must be powercycled to do anything else

---

### Post by Diabolis on 2008-08-09
Reinstall grub:
```

sudo grub
find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
```

So the output of the **find** command is the input of **root**.

---

### Post by louieb on 2008-08-09
Not real clear on what you are trying to do. Are you trying to make a dedicated GRUB partition? [IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") 

Is sda5 you Ubuntu / (root) partition?

When it boots, what boot loader/manager do you want loaded by the code in the MBR? [IDBS MBR Page]("http://users.bigpond.net.au/hermanzone/p6.htm")

---

### Post by caljohnsmith on 2008-08-09
> **Diabolis said:**
> Reinstall grub:
```

sudo grub
find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
```

So the output of the **find** command is the input of **root**.
I don't think that is what Lars Noodén is looking for, because doing the above commands will simply reinstall Grub into the MBR of the same drive as his Ubuntu. If he wants to put Grub in the boot sector of his Ubuntu partition, he should do:
```
sudo grub
grub> find /boot/grub/stage1
[returns (hdX,Y)]
grub> root (hdX,Y)
grub> setup (hdX,Y)
```

---

### Post by Diabolis on 2008-08-09
Isn't that just the same thing???

Anyway, It doesn't matter where the grub is if you only care about using it instead of the MBR.

---

### Post by caljohnsmith on 2008-08-09
> **Diabolis said:**
> Isn't that just the same thing???

Anyway, It doesn't matter where the grub is if you only care about using it instead of the MBR.
It can be easy to confuse them, but they actually aren't the same thing. For instance, if I do the "find /boot/grub/stage1" and it shows my Ubuntu partition is on (hd0,3), then if I do like you suggested:
```
grub> root (hd0,3)
grub> setup [COLOR="Red"](hd0)[/COLOR]
```
Then that installs Grub to the MBR of the first HDD (since (hd0) is the first HDD), and the Grub in the MBR will point to the Ubuntu partition (hd0,3) for all its configuration files. But if I want to install Grub to the boot sector of the Ubuntu partition, I would do:
```
grub> root (hd0,3) 
grub> setup [COLOR="Red"](hd0,3)[/COLOR]
```
Since (hd0,3) refers to the Ubuntu partition, and not the HDD (hd0). 

But I think Lars Noodén will probably have to fix his device.map first, because putting "(hd0,4) /dev/sda5" is not correct notation in the device.map file, since the device.map file only references HDDs and not their individual partitions.

---

### Post by Lars Noodén on 2008-08-11
/dev/sda5 is the root partition for xubuntu

/dev/sda3 is where I have OpenBSD

/dev/sda2 is where I have OS X

AFAIK, I have EFI/rEFIt in /dev/sda1

rEFIt gives me icons for all three systems, the ones for  OpenBSD and xubuntu both go to grub in the MBR thus adding an extra step of having to choose the system again.  My guess is if I can have rEFIt go to different installations of grub for each OS, then I only have to choose once by having the different grubs default to different systems/partitions.

Is that possible?  

> **louieb said:**
> [IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") 

Thanks.  That's a useful link.

---

### Post by louieb on 2008-08-11
> **Lars Noodén said:**
> ...I can have rEFIt go to different installations of grub for each OS, then I only have to choose once by having the different grubs default to different systems/partitions.

From what you described thats what is going on already. 
refit is loaded by code in the MBR.
And when you select Ubuntu or BSD you get its GRUB menu loaded.
Then you have to select it again to get the OS to load. 
What you can do is go into the GRUB configuration file and set **timeout** to 1 or 2 seconds. OR you can uncomment the **hiddenmenu** statment (Not recommended by me).

On that same page [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") there a description of both. Actually the comments in the configuration file are pretty good. 

Good Luck.

---

