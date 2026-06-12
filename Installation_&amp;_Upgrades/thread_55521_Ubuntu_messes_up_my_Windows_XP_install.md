---
title: "Ubuntu messes up my Windows XP install"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by van leer on 2005-08-09
For the past 2 days, I have tried four times, a dual install of, first Windows XP, then Ubuntu 5.04.

Every time, after both installs are over and I try and reboot to Windows, I get this message:

[B][FONT=Courier New]Windows could not start because the following file is missing or corrupt:
<windows root>\system32\hal.dll[/FONT][/B]

_This is the install sequence:_
1.Wipe 80 Gb HD using Boot & Nuke.
2.Create Primary DOS Partition of 256 Mb.
3.Install MS-DOS.
4.Install Windows XP on an 8 Gb partition.
5.Install Ubuntu, letting Ubuntu auto-space & create 2 new partitions on the remaining free space.

Ubuntu runs OK, but Windows can't boot.

(I don't try to recover Windows XP through Recovery Console or Repair Install. I just nuke the HD and reinstalling XP).

I like Ubuntu, but this problem is driving me nuts.

---

### Post by BanskuZ on 2005-08-09
Try downloading hal.dll file from [here](http://www.dll-files.com/dllindex/dll-files.shtml?hal).

Edit: Oh..Stupid me.

---

### Post by van leer on 2005-08-11
> Edit: Oh..Stupid me.

You ask for advice... and you get a forum prick.

---

### Post by justinflavin on 2005-08-11
[QUOTE=van leer]
1.Wipe 80 Gb HD using Boot & Nuke.
2.Create Primary DOS Partition of 256 Mb[/QUOTE]

how are you creating this? it seems unusual that you are creating partitions BEFORE the Windows installation.  Whenever i've done an XP/Linux dual boot, i've just installed XP as normal - let it grab as much disk space as it wants. 
THEN do the Linux install.

> 
3.Install MS-DOS.

odd. All i've ever done is just install XP , rather than this separate DOS install.

> 
4.Install Windows XP on an 8 Gb partition
5.Install Ubuntu, letting Ubuntu auto-space & create 2 new partitions on the remaining free space.
Ubuntu runs OK, but Windows can't boot.

did you convert your XP partition to FAT32 before installing Ubuntu?  That what i've done anyway.

there's a good guide (with screenshots) of partitioning in the Ubuntu installer here:
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

i followed it exactly, and it worked just fine. I now have a dual boot XP/Ubuntu laptop.

---

### Post by Buffalo Soldier on 2005-08-11
[QUOTE=van leer]For the past 2 days, I have tried four times, a dual install of, first Windows XP, then Ubuntu 5.04.

Every time, after both installs are over and I try and reboot to Windows, I get this message:

[B][FONT=Courier New]Windows could not start because the following file is missing or corrupt:
<windows root>\system32\hal.dll[/FONT][/B]

_This is the install sequence:_
1.Wipe 80 Gb HD using Boot & Nuke.
2.Create Primary DOS Partition of 256 Mb.
3.Install MS-DOS.
4.Install Windows XP on an 8 Gb partition.
5.Install Ubuntu, letting Ubuntu auto-space & create 2 new partitions on the remaining free space.

Ubuntu runs OK, but Windows can't boot.

(I don't try to recover Windows XP through Recovery Console or Repair Install. I just nuke the HD and reinstalling XP).

I like Ubuntu, but this problem is driving me nuts.[/QUOTE]Have you tried just simply creating the NTFS partition using the Windows XP installation CD? Do you really need MS-DOS? If you don't, how about trying to install just Win Xp + Ubuntu.

What I did when re-installing Win XP + Ubuntu is to pop in the Win XP installation CD, boot, partition NTFS, let Win XP install as usual, then lastly boot using Ubuntu install CD.

p/s: are there any special need for you to use Boot & Nuke?

---

