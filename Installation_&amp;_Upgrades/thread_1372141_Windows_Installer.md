---
title: "Windows Installer"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by SuperlativeConspiracy on 2010-01-04
Hi,
I've just downloaded the windows installer, but before I proceed, theres a few things I want to be sure of;

1) I only have one drive on my laptop, which has Vista installed on it, but I want to keep vista, and dual boot it with Ubuntu. Does the installer simply create a new partition from the free space, leaving my install of Vista untouched, or does it overwrite it?

2) I have a 64-Bit system - is this a problem when using the Windows Installer? I saw 64 options for the disc images, but no option was given for the windows installer.

Also, whats the minimum ammount of space I should have to install ubuntu onto?

---

### Post by Dayofswords on 2010-01-04
i think your talking about Wubi

i suggest you read this
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

it will give you all the info you need and more


Wubi doesn't make a partition, it instead makes big file on the windows drive for it to work on, which you choose the size of that file
your vista is remained relatively untouched, other than that there is a new program on and and disk space is used up

3GB of space is required as a minimum
[you should use >5gb for drive space]("https://wiki.ubuntu.com/WubiGuide#Can%20I%20force%20Wubi%20to%20install%20even%20if%20I%20have%20%3C%205GB%20of%20free%20disk%20space?") or else you cant really have much wiggle room

as explained in the example(later), wubi installs the appropriate XX-bit os version when it goes to download the files(long wait on that part, the file is ~700mb)

for example:
Q:Why is the AMD64 version of Ubuntu getting downloaded and installed?

A:The machine you are trying to install Ubuntu on may be 64 bit. The AMD64 installation is appropriate for all 64 bit architectures, no matter if they are AMD or Intel.

---

### Post by SuperlativeConspiracy on 2010-01-04
Ah thanks, but now I'm confused; Does that work like an Emulator? Or is it the same as a normal install of ubuntu, other than installing/uninstalling it from windows? Because it sounds like an emulator, other than the selecting the OS upon boot.. :confused:

---

### Post by madmax.santana on 2010-01-04
@SuperlativeConspiracy: I strongly suggest you don't use the Windows Installer feature, instead download a disk-image and mount it on a USB then install it on a separate partition.

This is solely my opinion and based on my personal experience that my whole system was nearly jammed and it was very very crowded or that's what it looked like to me.

---

### Post by SuperlativeConspiracy on 2010-01-04
Ah thanks, I'll bare that in mind. Only trouble is for some assinine reason, Vista won't let me create a new partition, or shrink my current paritions. Vista and a Backup/recovery partition take up my entire drive, and for some reason I can't shrink either partition.

Edit: I'm gonna give Wubi a try anyway, and see if I have any luck with it. Although to be honest, I'd rather use the more conventional method of burning the image to a CD. Anyone else had this problem? Because theres a hell of a lot of stuff I need on both existing partitions, and for the work I do at college I rely on being able to use photoshop, premiere and after effects, so I need windows. (WINE and the like are far too unstable)

---

### Post by Dayofswords on 2010-01-05
let me simplify this a bit

you install ubuntu as any other program on your computer,

but now when you startup you will choose which OS you want to use, Vista or Ubuntu.when you choose ubuntu at startup, you are running ubuntu and not windows at all, its the full thing, but the whole OS is inside a file in the windows drive(AKA a virtual drive).

if you want to remove ubuntu simply go to add/remove programs(i think thats its name in vista) and uninstall ubuntu from there, everything will be just as it was before

---

