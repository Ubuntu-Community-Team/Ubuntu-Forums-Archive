---
title: "Grub menu looping back"
date: 2018-09-30
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2018-09-30
History:[INDENT]I installed Ubuntu 18.04 it was working fine on my Toshiba Satellite laptop with a dual boot with Windows10.  I was trying to modify the fstab file, and broke the system, and could not load Ubuntu.  I installed Ubuntu again, but did not format the /home partition.  For some reason I could not get the WIFI to work on Ubuntu, so I did a clean install reformatting the / and the /home partitions.  
[/INDENT]
Current problems:

[LIST=1]
[*=1]When I try to choose Windows10 from the grub menu, the menu just loops back.  I can choose Ubuntu and it works.  Since I first tried to boot Windows, I now get an error when Ubuntu loads saying that there is a problem with the system, but it seems to work fine. 
[*=1]I cannot get my shared data partition to work on Linux, it is read only and owned by root.


After some further attempts to solve the 2 problems, It looks as though Wondows10 was not shut down correctly, and may be in a state of hibernation, which may be preventing it from starting up. 
[/LIST]

---

### Post by oldfred on 2018-10-01
Often the issue is Windows fast start up. And note that Windows updates will turn it back on and those may be in back ground an you do not notice them.
Also fast start up should not be used if dual booting Windows 10 & 7. The hibernation flag is set on all NTFS partitions.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

It looks like you have one drive and the old BIOS/MBR configuration. Windows 10's fast start up & the way it turns that on, makes use with BIOS a bit more difficult.
If you miss that it is on, you cannot boot Windows from grub menu. Only from MBR. Grub only boots working Windows. 
Best to have Windows repair disk for each version you have installed. You may be able to use Boot-Repair.
You have to temporarily install a Windows boot loader to MBR, boot into Windows (possibly f8 for repair console) and fix Windows. 
Then use Ubuntu live installer to restore grub to MBR. You can use Boot-Repair or just a grub install command.

With new UEFI, you can alway boot Windows or Ubuntu directly from UEFI. Or no boot loader install required when Windows turns its fast start up back on and grub does not boot it.

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

