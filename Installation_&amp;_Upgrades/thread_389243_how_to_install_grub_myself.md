---
title: "how to install grub myself?"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by hygum on 2007-03-20
I ran the newest ubuntu live cd and its installer programs. All things went well until i rebooted. At reboot the PC went into xp home as nothing had happen. And i told ubuntu to install grub on hda0, so i thougt that there will be a boot screen were i could choose between ubuntu and windows.

Ubuntu were installed on a sepate drive with complete control of it, no other partitions.

---

### Post by bulldog on 2007-03-20
How many hdd's are in your computer?

If you have more than one,it's almost certain you installed GRUB on another hdd.
BTW,you have to name a hdd like (hd0) or (hd1) and so on, **not** hda0 or something like that.

---

### Post by hygum on 2007-03-20
thanks i've at the moment two harddiscs, but i want to add some more which are unplugged at the moment, which had been plugged in before.

I think you're right about installing grub at the wrong harddisc, but

1) How do i install grub on the correct harddisc, using ubuntu? (which i now can login to with the boot selector of the motherboard)
2) Will i have to tell grub every time i change the number of harddiscs, or can it identify them?

---

### Post by tommcd on 2007-03-20
See this for reinstalling grub with the live CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
It may be a good idea to set the ubuntu drive as 1st boot in your Bios, and install grub to it. Remember, grub starts counting hard drives from 0. So it's hd0, hd1, etc.

---

### Post by bulldog on 2007-03-20
If you want to reinstall GRUB,
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)<---use the hd number from the find command
```
Exit the grub shell
```
quit
```
Grub will be installed to the mbr of the hdd which contains Ubuntu.

---

### Post by jiminid on 2007-04-19
Hi,
How would I change your howto to reinstall ubuntu grub onto my ubuntu's root partition, NOT the MBR?
already reinstalled my pclos grub to the mbr so now I get grub error 13 when I try to boot into ubuntu (feisty)

Ubuntu is on hdb1. when I installed via the live  cd it didn't give me an option to install grub at all. better to use the alternate cd from now on?

thanks for your help!

---

### Post by tommcd on 2007-04-20
Use the live CD to reinstall grub to the MBR. Grub should detect pclos and update grub accordingly.
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
Write back if you have problems.

---

