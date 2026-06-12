---
title: "Dual boot install keeps freezing"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by verynewbee on 2010-10-10
[B][I]Emachines D525 Laptop
Windows 7 Home Premium 64 bit
3 GB ram
250GB HDD
3 Ghz celeron processor[/I][/B]

Really need some help here...
I'm not doing something right but I don't know what I'm doing wrong?
I am trying to install 9.10 to dual boot with OEM Windows 7 home premium already on it.


_Here is what I've done so far_:
1. Went into boot menu and set to boot from CD/DVD drive
2. Allocated 104 GB from C drive to new unallocated partition using Windows 7
3. Formatted new allocated partition in NTFS
4. Popped in Ubuntu CD & booted
5. Got the initial Ubuntu screen
6. Chose install 
7. freezes & does nothing with Ubuntu screen still showing the "install" highlighted.

Now I done  what's listed as far as using WIndows 7 to allocate a portion of C drive and format it after I read in the wiki to do so.
I've been at this for 4 hrs now and have searched for a similar problems others have had but can't seem to find anything on this.

The CD I'm using I've used for other installs without a problem.
This 9.10 is 32 bit and my Win7 is 64 bit...not sure if this is my problem?

P.S. Before I did any allocating I first popped in the CD and the same thing happened, that is why I tried allocating C drive.....just figured I'd add this info in case of any questions as to why I did what I did.

---

### Post by verynewbee on 2010-10-10
^ Anyone?

---

### Post by verynewbee on 2010-10-11
I downloaded Ubuntu 10.0.4 64-bit on a new CD and I got the Ubuntu screen and then it _goes blank , then shows :_




[B]No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _[/B]



I still don't know what's wrong?:confused:

---

### Post by verynewbee on 2010-10-11
A little more info.
I pressed Esc while the Ubuntu name came on and was able to get to the installation options and still can't get it to install to HDD or LIveCD...It still comes up with what I had put in the prior post and stays at the ** (initramfs) _ **  prompt.


I found others with this problem but no answers.
I searched Google and haven't found any answers.
I searched Ubuntu Forums and found no answers.

I guess this one is a mystery unless it's something I am overlooking...which won't be the first time for me.](*,)

---

### Post by verynewbee on 2010-10-13
I was trying to get Ubuntu loaded on my kids laptop to introduce her to an alternative to Windows. I tried for many hours and couldn't get it to work.

I downloded Linux-mint 9 and everything loaded and it's up & running without a problem.

I would like to know why I couldn't get Ubuntu to work on this laptop so if anyone could help, I would appreciate it.

---

### Post by Mark Phelps on 2010-10-13
BEFORE you do anything else, boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  You will need that later to repair the Win7 boot loader should it become damaged during your dual-boot setup.

Please note that Ubuntu does NOT install in NTFS partitions; instead, it need Ext3 (of other Linux filesystems) to install.

Boot from the Ubuntu Live CD, open Partition Editor, confim that the partition you want to change is unmounted, and see if you can change it to Ext4.  If it won't let you change it, then remove it and recreate it as an Ext4 filesystem.  

Ubuntu should then find it and be willing to install to that partition.

---

### Post by verynewbee on 2010-10-16
> **Mark Phelps said:**
> BEFORE you do anything else, boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  You will need that later to repair the Win7 boot loader should it become damaged during your dual-boot setup.

Please note that Ubuntu does NOT install in NTFS partitions; instead, it need Ext3 (of other Linux filesystems) to install.

Boot from the Ubuntu Live CD, open Partition Editor, confim that the partition you want to change is unmounted, and see if you can change it to Ext4.  If it won't let you change it, then remove it and recreate it as an Ext4 filesystem.  

Ubuntu should then find it and be willing to install to that partition.








Thanks, I will try that....hopefully that will do the trick.

P.S. Since I already installed Mint-9 ....is it possible to triple boot?

---

