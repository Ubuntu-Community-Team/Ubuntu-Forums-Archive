---
title: "Problem with installing Xubuntu, it didn't see Windows"
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by hankster2 on 2014-07-19
Hello,
at first i'm sorry for my english. I try to describe my problem as best as possible.
I had problems with ransomware - it blocked my Windows 7 Starter netbook. Photo - [http://i.imgur.com/y9hhbJS.jpg](http://i.imgur.com/y9hhbJS.jpg) (if you want to unlock the computer, send SMS worth ~10$). 
Firstly i downloaded Xubuntu - i used this distribution few months ago and i trust it, then i made live USB. Next step - i plugged pendrive with Xubuntu to USB input and booted Xubuntu. Of course i used option with using Xubuntu without installation, because it didn't see my W7 installation.

Some screens:
[http://imgur.com/hcnx3DT](http://imgur.com/hcnx3DT)
[http://imgur.com/ow6dNVM,hPwIEAk,vma2V7a,VICNhX9#3](http://imgur.com/ow6dNVM,hPwIEAk,vma2V7a,VICNhX9#3) - four screens. Adnotation for second screen: i made it after installing "mtools".
[http://imgur.com/ra3UEk4](http://imgur.com/ra3UEk4) - i tried with mounting /dev/sdb and /dev/sdb2

My netbook is - Samsung N102S. Windows 7 is, i think, 32 bit version. I tried WinRE too, but WinRE didn't see windows installation too.
Certainly Xubuntu is booting without any problems and installing it is a solution for my problem. But it need format.

I think that i said everything. I can't format this disk (but it's the easiest method), because i have all of my photos and videos that i made over the last few years. I didn't made any rescue copy and i'm really regretting...

---

### Post by Mark Phelps on 2014-07-19
If the Win7 boot loader and/or OS files got damaged, it's likely a Linux installer will then "not see" the Windows install because it can't find the files that tells it that Windows is already installed.

My own personal experience has been that Linux utilities do a poor job of finding stuff on a damaged Windows filesystem partition because, they can't mount the filesystem.  Others may tell you different, but I've not found Testdisk to work particularly well in recovering files from Windows filesystems.

This means you will need to consider Windows solutions.  One thing you could try is recovering the previous Windows filesystem partition.  You will need a working PC, internet access, and the ability to both burn a CD and to boot from CD on this PC.  IF those are available to you, then download and burn the ISO of the Minitool Partition Wizard boot CD, boot from it, and see it it can recover the former Windows filesystem partitions.

If it can't, then you would need to connect this drive to a Windows PC and consider using Windows data recovery apps to recover the files from the drive.  Recuva is such an app and is available for free.  RecoverMyFiles is a commercial app, but you can install and run it for free -- to see if it finds your files.  You have to then go online and purchase a license to actually recover the files.

Good Luck

---

### Post by at_first_light on 2014-07-20
In your screenshots of Gparted it shows only 1 partition on drive sdb, yet in your terminal commands you attempt to mount sdb, sdb2, but never sdb1. You should try mounting sdb1 after installing mtools, and dosfstools. In the Gparted screenshot it lists FAT16 as the filesystem type? Is that what _you_ had it formatted as?

The ransomeware must have done something to the partition to make it unreadable so users wouldn't easily be able to recover files. To my knowledge FAT16 and even FAT32 doesn't support filesystem level encryption so we can rule that out, so perhaps the virus has simply damaged the filesystem to make it unreadable. Assuming this is truely ransomware (not just masquerading as ransomeware) we can assume that this process is reversible easily.

---

### Post by hankster2 on 2014-07-20
Big thanks for respond. 

Good news. Partition Wizard Home Edition (booted from USB) found all of my partitions. I can explore them, and now i know that all of my files are in a safe place. 
Now i can copy partition to other place, but i don't have portable drive, and before payday i can forget about it, but i think this is the best solution.
I'm trying to set Windows Boot Partition, but program said "Failed to find Windows directory". Folder "Windows" exists and it isn't empty - looks like normal Windows folder, with all subfolders and  files. 

You're right at_the_first - virus was really harmful, because partitions have status "lost / deleted". Of course partition wizard can recover them. 
FAT16? I don't know why Gparted show this, it's NTFS partition. 
I tried to mount sdb1, but console shows the same error - special device /dev/sdb1 doesn't exist. 

The same virus infected my PC, but i don't have any important files on disk, so i formatted it, then i installed Xubuntu. It helped. 

Xubuntu still doesn't see any of partitions.

---

