---
title: "GRUB2 is not loading"
date: 2014-10-02
forum: Installation &amp; Upgrades
---

### Post by Michel_Naslavsky on 2014-10-02
I am trying to set a dual boot system (Win7 + Ubuntu). 

I have first installed Win7 in a 180gb partition (SSD 240gb), leaving the remaining space to Ubuntu (8gb swap). I have also a 3TB HD, where I would like to destinate to /home and a common data partition to be seen and used by both OSs.

ISSUE: when booting, there is a quick message of error, the GRUB does not load -> but a terminal with grub prompt loads. Typing exit leads me directly to Ubuntu, as if it does not see the Win7 installation.

In attempt to solve it, I have downloaded the Boot-Repair tool, but it does not work, since I could not find a way to replace the Grub.

Here is the report:
[http://paste.ubuntu.com/8481492/](http://paste.ubuntu.com/8481492/)

How should I proceed?

Thanks

---

### Post by oldfred on 2014-10-02
Did you have BIOS set to boot from 3TB drive as sda when you installed Windows to sdb drive?
You are missing the 100MB boot partition. Windows installs 100MB boot partition onto the drive set as boot in BIOS.

You do not have to have the separate Boot partition for Windows. It primarily is for those who want to encrypt the main install. And it has the repair console, but you should have a Windows repair CD or flash drive anyway, so that is not critical. 
But you need to run Windows repairs on sdb, it has boot flag so repair should work.
You are missing bootmgr and /boot/BCD files which Windows repair will add. 
Then a sudo update-grub will run os-prober and add Windows to the grub menu.

You show a FAT32 partition on the 3TB drive. Do not use FAT. It has no journal so repairs are difficult and it cannot store any files over 4GB. Better to use NTFS if you want to share data.

You also show negative partition size for sda2??? Not sure I have seen that.

---

