---
title: "Help with Install"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by WinLinU on 2010-02-22
[FONT=Calibri][SIZE=2]I recently took an accelerated course on Linux, it was just enough to make me dangerous and it peaked my interest in Linux. I decided that I need to learn more about this OS. After reading an article in Maximum PC magazine, I decided that Ubuntu would be a good place to further my Linux study. I bought an Asus, Eee netbook with a 250GB HDD and 2GB of ram. The netbook came with Windows 7 starter. The magazine article talked about loading Ubuntu Netbook Remix on the Asus. I want to be able to dual boot my netbook. I downloaded Ubuntu netbook remix, burned it to a CD was able to make a USB startup disk but I cannot install it on the netbook. When I do try to install it, it gets to the install part but it wants to format the HD and wipe out Windows. I was able to install Ubuntu on my desktop PC (not Ubuntu Netbook Remix) and that install was a breeze. That computer is a tri-boot, Windows XP, Windows 7 and Ubuntu 9.10 Desktop. Why don’t the Remix load?[/SIZE][/FONT]

---

### Post by vodsonic on 2010-02-22
You need to first resize the Windows partition. I'm not familiar with Windows 7, but I believe the GParted and/or QTParted utilities can resize an NTFS partition. At least one of these should ship as part of the current Ubuntu live CD. If your Netbook remix installer isn't a live version, or if it doesn't include one of the above partitioning utilities, you might have to burn the live .iso to another flash drive to be able to boot from it, but you should be able to resize your NTFS partition that way, and then go back to the Netbook Remix installer and format the free space you've just made.

---

### Post by darkod on 2010-02-22
Win7 is better to be resized with Disk Management. Since vista you can do resize there.
Also check in Disk Management how many partitions you have currently. If you have the maximum 4 (which is unlikely but possible), the ubuntu installer can see that and limits your options for installing.

---

### Post by WinLinU on 2010-02-22
> **vodsonic said:**
> You need to first resize the Windows partition. I'm not familiar with Windows 7, but I believe the GParted and/or QTParted utilities can resize an NTFS partition. At least one of these should ship as part of the current Ubuntu live CD. If your Netbook remix installer isn't a live version, or if it doesn't include one of the above partitioning utilities, you might have to burn the live .iso to another flash drive to be able to boot from it, but you should be able to resize your NTFS partition that way, and then go back to the Netbook Remix installer and format the free space you've just made.
I forgot to mention in my 1st post that I did resize my partition and have over 60GB of free space available, but Ubuntu remix will not do anything, wants the whole thing.

---

### Post by darkod on 2010-02-22
> **WinLinU said:**
> I forgot to mention in my 1st post that I did resize my partition and have over 60GB of free space available, but Ubuntu remix will not do anything, wants the whole thing.

That would happen if you already have 4 partitions because it can't create a 5th one. Either look in Disk Management or use the Try Ubuntu option and open Gparted to look at the hdd.

---

### Post by Sef on 2010-02-22
> That would happen if you already have 4 partitions because it can't  create a 5th one. Either look in Disk Management or use the Try Ubuntu  option and open Gparted to look at the hdd.

That is not accurate.   Only 4 primary partitions can be created.  However, if one of the primaries is an extended (logical) partition, then more than 4 partitions can be made.

---

### Post by darkod on 2010-02-22
> **Sef said:**
> That is not accurate.   Only 4 primary partitions can be created.  However, if one of the primaries is an extended (logical) partition, then more than 4 partitions can be made.

Sorry, but I was trying to keep it short. :) I'm counting only primary and extended ones in the 4 number.
Otherwise I have 5 on my own PC. :)

---

### Post by WinLinU on 2010-02-23
> **darkod said:**
> That would happen if you already have 4 partitions because it can't create a 5th one. Either look in Disk Management or use the Try Ubuntu option and open Gparted to look at the hdd.
 
I thought that I had learned in class that I could have 4 partitions in Windows and still load Linux.  I deleted one of the Windows partitions (down to 3) and the Ubuntu install was a piece of cake.  Thanks for the help, I'll be back soon, I am sure I will need more help in the near future.

---

