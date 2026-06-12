---
title: "kubuntu hangs at startup after installation (kubuntu specific)"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by zardoz on 2006-11-14
Hy!
I have ubuntu 6.10 installed since some time, but now wanted to test kubuntu. So I decided to install kubuntu on another partition (from the kubuntu 6.10 alternate install cd).
During the installation process I chose to install grub on a floppy.
Everything went fine and it was time to restart. Then I got the Grub menu, where I selected my kubuntu system.
The initial startup splash screen appeared, but the status bar didn't move a bit. It just hanged at the beginning. I tried it several times and waited really long. With the same result.
When I start kubuntu in recovery mode, everything is fine until the status report "sd 6:0:0:0: Atached scsi removable disk sdb" and then it hangs there again. Strange thing is, that I dont have a removable disk connected to my computer. And there is only one dvd drive and one harddrive.
So I went to my (working) ubuntu installation and inserted an extra grub option for kubuntu in menu.lst ... then restarted and tried to boot kubuntu with the masterrecord (respectively ubuntu) grub menu ... and voila, it started without any problem.
I also installed for testing purposes ubuntu on that partition with grub on the floppy ... that worked without a problem. So it seems to be kubuntu specific problem.
Another thing, that attracted my attention was, that kubuntu speaks of sdb everytime an ubuntu of sda.
For example in the menu.lst entry from kubuntu there was the line:
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb4 ro quiet splash
and in ubuntu it is:
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash

I am not sure if this problem is only present, when installing grub on a floppy ... i thinks so, otherwise many people perhaps would have that problem.

My my system:
CPU: Core 2 Duo 
Mainboard: Gigabyte GA-965P-DS4 (Intel P965 Chipset) 
My DVD Drive and my Samsung HDD are both on SATA
SATA in AHCI Mode

---

