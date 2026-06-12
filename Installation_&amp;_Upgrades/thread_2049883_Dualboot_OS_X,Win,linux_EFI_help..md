---
title: "Dualboot OS X,Win,linux EFI help."
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by davig019 on 2012-08-29
Hi,

This is the first time im installing linux so need a bit of help.

Im trying to get my multibooting working to no avail. I Have 3 hard drives that im aiming to setup like so:

```
1Tb 
-Windows 7 (to be upgraded to 8)

320Gb
-OS X
-Chameleon Bootloader

3Tb
-Windoos 7 (typoed so i could tell them apart)
-Ubuntu
-Fedora
-Remaining space Storage

```

I have currently got the 1tb and 320gb working. Its boots to the 320Gb OS X disk and from the chameleon bootloader i can boot OS X or Windows 7.
Being over 2.2Tb i used UEFI to re-install Windoos to 3Tb. Went fine, could boot to it either directly by selecting the hard drive on boot or from OS X bootloader. 

When i installed a Linux distribution it went wrong from there on. (I tried ubuntu first but have also tried with fedora). It would give some grub(?) errors then boot into fedora. The OS X bootloader wouldn't see any linux install though. The Chameleon Bootloader could still see windoos but would tell me bootmgr is missing. I told linux to use the ESP created by the windoos 7 install as i think i read that somewhere else the wholse drive is controlled by this one partition.
I have formated the 3Tb drive now and have misplaced the Ubuntu disk so cant provide exact errors or the like atm.

What is the best way to setup my 3Tb hard drive so that the bootloader on my OS X drive can detect the 3 OS'S as separate installs? What happens if i were to create 3 efi system partitions, one for each os. would all hell break loose or might it work?

I wont be booting to the 3Tb drive as mentioned so i don't think i will need grub? If grub i would boot from one bootloader to another and that defeats the object of a bootloader imo.
I could buy another hard drive and install my Linux distros to that and im sure it would work. But its not what im aiming for!

I've looked at some pages already and im affraid they dont meant a great deal to me! sorry! Any help is great :)

Thanks

EDIT:
Just found this page via googling, just skip down to the installing linux section. [http://lifehacker.com/5698205/how-to-triple-boot-your-hackintosh-with-windows-and-linux](http://lifehacker.com/5698205/how-to-triple-boot-your-hackintosh-with-windows-and-linux) .is it possible to install the bootloader to the same partition as the ubuntu install?

---

### Post by oldfred on 2012-08-29
Is this a Mac?

---

### Post by davig019 on 2012-08-29
It's a pc running mountain lion i.e. hackintosh. It's just the Hackintosh boot loader that im intending to use just as I'm already familiar with it.

I'm in the process of installing fedora and Ubuntu(when I find the disk) to a spare 1Tb hard drive i had set asside for backup for my main windows 7/8 instal, on two 30Gb partitions to see if the osx boot loader picks them up of a mbr disk.

I would ideally have them on the 3Tb drive and to the osx boot loader see them as individual disks rather than seeing a disk with a bootloader

---

### Post by oldfred on 2012-08-29
Thead closed.

Hackintosh/Apple EULA violation. 
We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalized with infractions and warnings.

For more information, please see the forum policy: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy). If you believe this was made in error, please post in the Resolution Center, which you can find in the previous link.

---

