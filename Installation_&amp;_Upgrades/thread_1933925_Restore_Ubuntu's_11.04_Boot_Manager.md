---
title: "Restore Ubuntu's 11.04 Boot Manager"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by hulkbuster on 2012-03-01
Hello folks:
        i have installed Ubuntu 11.04 in the second partition and  first partition being XP :everything went well , during the boot process its Boot Manager ie., **GNU GRUB  version 1.9~rc1-13ubuntu3** did recognise the 
**Ubuntu, with Linux 2.6.38-8-generic**
**Microsoft XP Pro (on/dev/sda1)**  
      
Since i restore my PC quite often so i thought why not try in advance and see what would happen if i try to restore the normal boot entry through Recovery console of Winxp CD.

So i loaded a  XP disc and went to Recovery console and gave the command **fixboot** and **fixmbr** command.

           Now this made normal bootup of XP and the Ubuntu's Grub Boot Manager didn't pop up:
So i just tested to see if i could give an entry in boot.ini of the xp partition and give the Ubuntu entry just like having a normal secondary OS: 

But on the next reboot i choose the Ubuntu option and it gave this error, i.e,
```
Windows could not start because the following file is missing or corrupt.
<Windows root>\system32\hal.dll
Please re-install a cioy of the above file.
``` Does or can any one give a nice suggestion with this,how do i get around this : i mean how can i get the Ubuntu in my secondary partition to boot choosing from the Boot Manager, i hope you have understood.

I havn't formatted that partition and when i load MagicParted it still show 3.5 GB of space being used and i just fixed a way to run my MTS M Blaze plugin modem and it feels good to browse and just fiddle aroung Ubuntu , basically i want Ubuntu since i heard it being virus proof and no know virus attacking the system.

My query is just to restore **Ubuntus boot manager** : or is their a way that i can boot Ubuntu from the **XP Boot Manager**:


Please help me in this:

---

### Post by darkod on 2012-03-01
You can't simply add ubuntu to boot.ini since windows can't boot it by default. It could work but other steps are needed.

As for reinstalling grub2 to the MBR, here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by hulkbuster on 2012-03-05
Thank you darkod , i was able to recover the Boot Manager of Ubuntu 11.04 and what do you know that the Microsoft Windows XP entry was still their and i was able to boot to it.

Slowly getting the hang of UBUNTU: hey do you know how can i edit the MS Windows Entry , i want it to be in the first and not Ubuntu from the GRUB 1.99 Boot Menu entry.


Thanking you in advance::D

---

### Post by oldfred on 2012-03-05
The easiest way is to install grub customizer. Or you can manually edit the grub file (/etc/default/grub) that chooses boot order.

HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

