---
title: "Ubunto install on USB stick results in &quot;error: hd0,1 read error&quot;"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by snowy_cat on 2011-01-03
Currently I wanted to try a small ubuntu install for router conf. I tied this before with Debian Lenny but want to use Ubuntu.
 
I use a Atom mobo with only a USB stick and a CDROM drive connected, walked through the whole install, just a non-expert install and no additional options.
 
When it reboots after the last install step (grub2) it shows the Grub2 boot menu with the default options, but when I want to run Ubuntu (normal or recovery mode) it says : 
 
```
error: hd0,1 read error
error: no such partition
error: no such partition
 Failed to booth both default and fallback entries
Press any key to continue...
```
 
Stange, I thought something was wrong with my usb stick so I tried another and got the same error. Next I tried a normal HDD and it works fine on the HDD.
 
After some reading I checked the root enviroment variable and it say's (hd0,1) which is correct I suppose it's the only disk in the system. Also I use 1 partition to test the install. At install time the disk layour would be : 
 
```
/dev/sda1     /
/dev/sda2 swap
```
 
The fs used is default ext4.
 
So I think something is wrong and my USB sticks aren't reconized by the bootloader.
Is there some module missing ?
 
I also checked the usb drive on failures afther install but it's totaly alright. I also tried the rescue option to reinstall the grub2 bootloader but unfortunally no succes here. 
 
When I use debian, the grub is working fine on my USB sticks, debian uses the grub bootloader instead of grub2.
 
Can anybody give me a clue on how to solve this problem ?

---

### Post by cipherboy_loc on 2011-01-03
> **snowy_cat said:**
> 
So I think something is wrong and my USB sticks aren't reconized by the bootloader.
Is there some module missing ?

I find it hard to believe that Grub would not recognize your flash drive; I have been booting Ubuntu from at least 2 different flash drives (on various systems -- All desktop) since the 8.10 builds.

More likely, and one which I have seen many times, is that your device is not hd0,1; instead it might be hd1,1 or something of the like. Also, what version of Grub were you using with Debian? Grub Legacy or Grub2?

If all that fails, can you boot from a LiveCD? Or a customized LiveCD that starts SSH on boot? If so, you might want to ssh into the machine (if you don't have keyboard+monitor+mouse), and wget the download script, chmod it, execute it, and post the resulting README file (in CODE tags) as a reply.


Cipherboy

---

### Post by C.S.Cameron on 2011-01-03
Does the USB drive work on another machinr?

Have you checked the ISO MD5SUM?

Welcome to the forums.

---

