---
title: "Live CD boot problems"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by ek678 on 2007-08-27
When I burn and boot from the Ubuntu live CD it seems to boot normaly, then for about two minutes it repeats a bunch of I/O buffer and loading errors. Then it seems normal again, but it boots to the regular login screen. I have tried redownloading and reburning a few times, but to no avail.
I really want Ubuntu and I'll get any info you need that I can get.

---

### Post by logos34 on 2007-08-27
Either post your specs or try a text-mode ubuntu intall.  I'd get the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD?highlight=%28minimal%29") and start a network install--that way if you run into hardware detect problems again you won't have wasted time downloading an entire cd.

---

### Post by ek678 on 2007-08-28
I'm using a Compaq Evo N610c notebook with 256mb ram and a pentium 4 processor. I have a Toshiba IDE smart hard drive which holds 30gb. BTW the cd now starts in text mode and it starts and goes along fine until I get to the partitioning. It says that their was an error writing partition table to disk. So I think something happened to my HD. :(
    I used to have Ubuntu installed and working with absolutely no problems, but I wanted to try out PCLinuxOS 2007 and Linux Mint just to see how they were. (I didn't make a backup of my HD because I didn't have much on it.) They both work fine. After a few boots when I installed Linux Mint it started giving me all these I/O errors. Then no live CD's booted correctly and I wiped the hard drive using my windows cd, but still nothing worked. The problem appears to be writing to the HD.

P.S. Net-install didn't work either.

---

### Post by ek678 on 2007-08-28
Sorry for bumping my own post, but I could really use some help. If anyone has even a guess I would like to know, will I need a new HD?

---

### Post by Pumalite on 2007-08-28
You need a new iso: Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
With 256 MB of RAM this is your best bet.

---

### Post by logos34 on 2007-08-28
> **ek678 said:**
> I'm using a Compaq Evo N610c notebook with 256mb ram and a pentium 4 processor. I have a Toshiba IDE smart hard drive which holds 30gb. BTW the cd now starts in text mode and it starts and goes along fine until I get to the partitioning. It says that their was an error writing partition table to disk. So I think something happened to my HD. :(
    **I used to have Ubuntu installed and working with absolutely no problems, but I wanted to try out PCLinuxOS 2007 and Linux Mint** just to see how they were. (I didn't make a backup of my HD because I didn't have much on it.) **They both work fine. After a few boots when I installed Linux Mint it started giving me all these I/O errors. Then no live CD's booted correctly** and I wiped the hard drive using my windows cd, but still nothing worked. The problem appears to be writing to the HD.

P.S. Net-install didn't work either.

Wish I knew exactly what the problem was here, but from everything you've said it appears to be a hardware isssue.  Here is one thing you can do right off: run a memtest86+ from the menu option on the live cd--if your ram is failing it will tell you.  A S.M.A.R.T diagnostic will show the health status of your hard disk, but you'd need to be able to boot a live cd in order to run it.  If you can't even run smart from a utility cd like SystemRescueCD, Parted Magic or UBCD, then you'll have to take it out and hook it up to a known healthy system and run it from there.

---

### Post by ek678 on 2007-08-29
I ran memtest86+ all last night and no errors were found this morning. I tried a few other Linux distro CD's to see if they'd work and none do. The errors are:

Buffer I/O error on device sda, logical block 7325632
ata1.00: exception Emask 0x0 SAct 0x0 SEvr 0x0 action 0x0
ata1.00: (BMDMA stat 0x75)
ata1.00: cmd c8/00:08:00:3e:7e/00:00:00:00:00:00/e3 tag 0 cdb 0x0 data 32768

That just repeats (With different numbers for 'data' and 'logical block')

---

### Post by logos34 on 2007-08-29
> **ek678 said:**
> I ran memtest86+ all last night and no errors were found this morning. I tried a few other Linux distro CD's to see if they'd work and none do. The errors are:

Buffer I/O error on** device sda**, logical block 7325632
ata1.00: exception Emask 0x0 SAct 0x0 SEvr 0x0 action 0x0
ata1.00: (BMDMA stat 0x75)
ata1.00: cmd c8/00:08:00:3e:7e/00:00:00:00:00:00/e3 tag 0 cdb 0x0 data 32768

That just repeats (With different numbers for 'data' and 'logical block')

What is 'sda'?  Do you have a flash drive plugged in or I you using a USB-cdrom with this laptop?

---

### Post by belias on 2007-09-11
I have the same laptop and was having the same issue. I believe the problem is with the standard cdrom drive..too slow or something. This also makes the ¨live cd¨ experience extremely choppy as well. Anyway, the solution for me was to run the alternate text install cd. When you download the ubuntu iso from the official page, there is a check box that asks if you want to download the ¨alternate¨ text  version install. It&#347; very easy, just answer some basic questions. Actually, i´m going to use this version on my other pcs as well, as it seemed much less problematic and to the point.

---

