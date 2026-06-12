---
title: "Dual booting of win7 and ubuntu, 64 bits"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by garber on 2012-02-21
Deal all,

I know this subject was already discussed here, but since I am not an expert, I would like to get "an algorithm" step-by-step how to solve the problem, if possible. So please do not send me to the previous thread.

I bought a new computer HP compaq 8200, and I am trying to install ubuntu 11.10 along Windows 7,  both 64 bits.

I installed the Windows, and then when I am trying to install the Ubuntu, it does not recognize the installed win 7 OS.

Can you write me a sequence of operations I should do for overcoming this problem?

Thank you very much,
David Garber
[EMAIL="garberad@gmail.com"]garberad@gmail.com[/EMAIL]

---

### Post by Bucky Ball on 2012-02-21
Welcome. Open a terminal and type (or safer to copy/paste) this:

```
sudo update-grub
```Restart. That should pick up Windows if it is there. Are you sure it is? Give that a try.

---

### Post by garber on 2012-02-21
One moment - when do I do this ?

The problem is that during the installation of ubuntu I am doing the partition for the linux, which might ruin the Windows because it is not recognizing it. 

Thanks, David.

---

### Post by darkod on 2012-02-21
With the ubuntu cd boot into live mode (Try Ubuntu), open terminal and run:
sudo fdisk -l (small L)

Post the results.

EDIT: Have you used this disk in raid before? Or is it running raid now?

---

### Post by jana05 on 2012-02-21
> **garber said:**
> Deal all,
...........
I installed the Windows, and then when I am trying to install the Ubuntu, it does not recognize the installed win 7 OS.
................

Please list the steps you did and the results???

---

### Post by garber on 2012-02-21
here it is. Thanks. 


==============

Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bbccc5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdb: 4007 MB, 4007624704 bytes
32 heads, 63 sectors/track, 3882 cylinders, total 7827392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4d0a68ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     7826111     3913024+   b  W95 FAT32


================

what is raid?

---

### Post by garber on 2012-02-21
> **jana05 said:**
> Please list the steps you did and the results???
When I want to install, it does not ask me if I want to install it along Windows, but just like there is no OS around.

---

### Post by Mark Phelps on 2012-02-21
IF your PC came preloaded with Win7, you need to read through the details below BEFORE you attempt any kind of dual-boot install:

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by garber on 2012-02-21
> **Mark Phelps said:**
> IF your PC came preloaded with Win7, you need to read through the details below BEFORE you attempt any kind of dual-boot install:

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.
Dear Mark, 

Ok. I did it with win7. I have now 2 partitions (all are basics) and one unallocated area.
I will do soon the repair disk. 

What's now?

Thanks, David.

---

### Post by darkod on 2012-02-21
Is there any reason you are using GPT partition table on your 500GB disk? It is used on disks bigger than 2TB.

Also, you might have msdos table with gpt remains which can confuse the ubuntu installer, and because of that it is not detecting win7.

If you have msdos table with gpt remains you can remove them with fixparts:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by roelforg on 2012-02-21
Boot the installer, in the partman, tell it to fill the unallocated area with a partition for ubuntu.
It should work.
 
(Note: at your own peril, whenever you start mucking with partitions, i am not responsible for any results)

---

### Post by garber on 2012-02-21
> **Mark Phelps said:**
> IF your PC came preloaded with Win7, you need to read through the details below BEFORE you attempt any kind of dual-boot install:

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.
Dear Mark,

How do I continue?

Thanks, David.

---

### Post by darkod on 2012-02-21
Did you try fixparts first as stated in post #10?

---

### Post by garber on 2012-02-21
actually no, but now I am in the following situation: 
I have the two OS installed side by side, but it is automatically going to the linux

Best, David

---

### Post by garber on 2012-02-21
and when I am trying to "fix" the booting of the windows by its disk, it tells me that there are no problem with the booting, and it is recognizing that it is installed.

---

### Post by darkod on 2012-02-21
If you installed ubuntu without solving the problem of it not detecting windows first, it is normal that it loads ubuntu directly.
It can't detect windows so it does not create an entry for any other OS in the boot menu, in fact there is no boot menu because it thinks only ubuntu is on the computer.

I would try fixparts unless you know why are you using gpt table, if you configured it like that. In any case it looks weird, fdisk reports it as gpt table but there are no partitions reported. fdisk is not good with gpt but at least it reports the partitions correctly.

Another way to see more details, from live mode you can run:
sudo parted /dev/sda print

---

### Post by Bucky Ball on 2012-02-21
Have you tried simply opening a terminal and copy/pasting this in:

```
sudo update-grub
```?

Sounds a bit like you are missing the grub list of OSs at boot and it is booting the first OS on the list (Ubuntu). This is a setting in the grub configuration which can be adjusted (it is probably set to '0' seconds by default and skipping straight over the list which seems to happen on new installs sometimes, unfortunately) Just after you boot, try holding down Escape (or Shift, depending on the release) and that will take you to the grub list/OS boot options. Windows should be there.

I would try this last fix before bothering with fixparts or anything else. It could be that simple and not the first time I've seen this. ;)

---

### Post by mbuell on 2012-02-21
Since you have now installed ubuntu - it could just be that it is now only a grub issue. However, I think it could easily be related to the GPT issue. 

So, K.I.S.S, method first!  (Keep-it-simple-stupid)  

1st - please tell us - I want to be sure we understand. You have both OSes installed, yes? Windows 7 and Ubuntu?

2nd - watch the computer when you boot it up. Do you get a menu that lists Ubuntu and Windows? This menu would be the GRUB menu. It is usually white on a black screen, with 3-4 arcane appearing listings - but Linux and Windows will be in the choices. A google search will get you pictures of what it looks like. You can use the arrow keys to move from one choice to another. The default is for the menu to show for only 10 seconds, so you must watch!

Now, if you do NOT have this menu, please read on!

3rd - do the update grub command as recommended. Since ubuntu is installed, this can do no harm, and may resolve your problems. 

4th - go with the fixparts. Now, if you need to go this far, I think first you should read a little about what darkod is talking about 
[http://en.wikipedia.org/wiki/GUID_Partition_Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")
[https://www.google.com/search?client=ubuntu&channel=fs&q=GPT+partition&ie=utf-8&oe=utf-8]("https://www.google.com/search?client=ubuntu&channel=fs&q=GPT+partition&ie=utf-8&oe=utf-8")

Personally - my guess is that your issue started because of the GPT partitioning. And, if Ubuntu is still failing to recognize the Windows GPT partitioning - that could cause what you apparently describe is now your 2nd issue. It seems you are telling us that you have no GRUB boot menu, and the machine boots into Ubuntu. But, this is not clear from what you have said. If it is the GPT partitioning - Ubuntu should recognize it, but might not be due to some quirk on your machine.

---

