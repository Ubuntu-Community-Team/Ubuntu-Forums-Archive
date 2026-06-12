---
title: "Triple-Boot Nightmare!"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by Apv507 on 2010-09-10
I have a Computer, It came with Windows 7 64bit on it. I installed Ubuntu through WUBI. I used the Windows Disk Management program to resize my HDD. I shrunk the main drive and created a 20 gig free space. I installed WindowsXP on this 20g space. I had to change from AHCI to ATA. I started my new XP installation. As I should have expected my the screen that let me pick between Windows 7 and Ubuntu was gone, and it just said XP. Well thats cool. I get in XP use bcdeasy and use the install Win7 to mbr. So I restarted. Great I now I have Ubuntu and Win7... but no XP. So i think, okay, ill boot into Ubuntu, use the update grub command and XP will be there, so i do it and restart. No XP, So i try to boot into Win7 and see if i can do something in there.. No luck it says it can't boot and takes me to a startup recovery thing. Which, as Windows recovery things tend to do, doesn't find anything wrong. So I have Ubuntu now, which is great, but I do need Windows.. Can anyone Help?

---

### Post by PRC09 on 2010-09-10
With WUBI in this mix I am not sure but with windows previous versions the oldest OS was always installed first and then the newer version for dual boot purposes.However with Vista/Win7 install I think they create their own boot partition usually (100mb) or so where the boot files are located.  When you installed XP you probably wiped the Win7 bootloader as well as grub files.As for a solution with WUBI in the mix I am not sure.If it was me I would start over and put Xp first then Win7 and give Ubuntu its own partition and install there.Someone else may have a better solution but it will probably take as much time to sort this out....If you post the results  of the info from the boot info script I am sure someone will help out here...


[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Apv507 on 2010-09-10
Wiping everything is not my last option, Can I manually create the stuff I need. I don't really care about XP that much, I would just like my Win7 and Ubuntu

---

### Post by garvinrick4 on 2010-09-10
> **Apv507 said:**
> Wiping everything is not my last option, Can I manually create the stuff I need. I don't really care about XP that much, I would just like my Win7 and Ubuntu
Wubi works off of windows boot loader and is a folder in C: drive right next to users.
Booting two windows installs on same drive is a pain in the rear. 
Get rid of XP by deleting in gparted in Ubuntu or whatever partitioning program you use.
Look into Windows 7 boot manager bcdedit and look for a entry with wubildr in it. That is what Ubuntu puts in there to boot off of. 
As administrator in command line.
```
bcdedit.
```
If having trouble booting into Ubuntu go to the Ubuntu folder in C:drive and open and use the uninstall in there not add and remove programs in Windows.
Put install cd in tray choose Wubi and follow instructions. 
These are my recommendations, each has their own but if you want 2 Windows use an external USB. 
 After using Ubuntu for a while you will want to do a partition install instead of WUBI anyway. Nothing wrong with Wubi to get the hang of it with. And if you screw it up all you got to do is use the uninstall and a install cd and in 20 minutes you have a fresh wubi install. Only takes that long to do partition install once you understand the procedure. Give it time. Good luck partner

---

### Post by Apv507 on 2010-09-11
I ran bcdedit and no i can boot into windows7, is there no easy way to add windows XP? no few lines of code i can add to boot.ini or something?

---

