---
title: "Partition Enigma with WinXP... (NOT the usual MBR problem)"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by mac.ryan on 2008-01-12
I am  (well... I WAS) using gutsy 64 bits on a dell XPS (centrino Duo Core2). The HD I have is a SATA Hitachi HTS64161.
 
For some reason I need to install windows beside ubuntu, so I proceeded resizing and moving partitions around in order to then do a winXP installation.
 
The last configuration that worked (prior to WinXP installation was:
 
sda2, primary: ext3 20 Gb with Gutsy installed
sda1, primary: 20 Gb, empty, for the next ubuntu release
sda3, extended:
   sda4 linux swap, 4Gb
   sda5 ext3, 100 Gb (as /home)
   free space 20 Gb (for the windows installation)
 
The system worked flawless (I tried to reboot it and checked the integrity of data prior to attempt winxp installation).
 
When I tried to install XP in the free space, it refused to do so. I thought it was because of me tryng to install it in a non-primary partition, so I gave it a second try using the sda1 partition, and it worked.
 
**Now the tricky bit: **of course I expeted GRUB to be gone (and in facts it was), so I put in the 64bit alternate installation disk, rebooted, selected 'recovery mode' and selected 'reinstall GRUB'.
 
The dialog appears for me to select what partition to use as root, but when I select sda2 it tells me
 
```
an error accurred while mounting the device you entered for your root file system
```
 
The only partition that does not give this error is actually sda1 (the one with windows). So I am asked where I want to install GRUB, but wherever I chose (my best option would be HD0) I get the following message:
 
```
unable to install GRUB. Executing 'grub-install HD0' failed. This is a fatal error.
```
 
**Now the trieckiest part ever:** I decided to try to reinstall ubuntu on the free space, but when it comes to the selection of what partition to use for the fresh installation, the HD is presented as if it was totally empty, without any partition of sort on it.
 
I also tried with a 32 bit standard CD (Still gutsy) but even with Gparted, the HD is presented as totally empty and unpartitioned.
 
The funny thing is: windows not only works normally, but also sees all the partitions correctly (although it says they are of an unknown type).
 
**MY QUESTIONS ARE...**
 
1) Does anybody have a clue of what is happening here?
2) Any suggestion on what to try next, either with an ubuntu CD or from within Windows / it's installation CD?
 
PS: I have complete backup of everything, but I woud honestly prefer to avoid to do a complete reinstallation of both unbutu and windows. Windows is not a problem, but in Ubuntu I had tons of software installed, and it will take forever to download it with a dialup connection!).
 
Many thanks in advance.

---

### Post by Pumalite on 2008-01-12
Google 'Installation of XP with Ubuntu installed first'

---

### Post by Pumalite on 2008-01-12
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by mac.ryan on 2008-01-12
Pumalite... thanks for your attempt to help... but I do not see how the page you linked should be relevant to my problem... that is the description of exactly **the usual MBR problem**, while I tried to make clear that my problem is different since the title of my post...
 
...did I miss anything in that page?

---

### Post by Pumalite on 2008-01-12
I believe the basis of your problem is that you are installing Windows AFTER Ubuntu.

---

### Post by mac.ryan on 2008-01-13
Bump...
 
anybody available to give some **real **help?

---

### Post by mac.ryan on 2008-01-16
I finally solved my problem. Not that I really understood what was wrong with the Hard Drive... but at least I found a workaround to revert the situation, I post it here what I did... just in case anybody else would get the same problem...

[LIST=1]
[*]Given that gparted as well as well as grub would not recognise the partition table, but given that I could still the list of partition with the Ubuntu Alternate CD recovery mode, I had the idea of opening a shell from there (select root system -> open a shell in the root system). Manually mounting the partition in console mode worked, and from there I made a tar of the entire partition on an external drive.
[*]Gparted would still prevent me to format the HD, and the only way I found to format the HD was to use again the recovery command shell and use fdisk to create a new partition table (this 'buldozed' any track of previous partitions from the HD).
[*]I then installed again windows (first) and ubuntu (second) in freshly created partitions. And - of course - grub.
[*]As a final pass, I rebooted with the CD, I erased the content of the ubuntu partition and dumped there the content of the tar file...
[*]Voila`... my system is back to normal, although (probably because of the different UUID partition numbers) I get some warnings during the boot phase...[/LIST]Hope this might help somebody, sometimes...

---

### Post by Pumalite on 2008-01-16
It always works fine with Windows installed first.

---

