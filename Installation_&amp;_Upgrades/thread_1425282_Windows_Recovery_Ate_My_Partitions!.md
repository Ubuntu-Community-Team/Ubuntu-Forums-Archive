---
title: "Windows Recovery Ate My Partitions!"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by JohnMorrow on 2010-03-08
All:
 
I have an Acer Aspire One netbook with WinXP, Xubuntu, and Ubuntu netbook remix (both version 9.10) on it. Last night after downloading updated which included a new kernel, I accidentally booted into Acer's recovery partition which is inteded to restore the machine to factory defaults. I let the recovery OS finish loading, which evidently was a mistake, then clicked on "Exit".  When I rebooted, no GRUB menu appeared, only a "no such partition" error message and a "Grub-recovery" prompt.
 
I booted from an Ubuntu 9.10 USB drive (no CD or floppy on the netbook), and started looking for solutions. GParted shows an empty 50 Gb extended partition (no detectable file system) where my two Linux Partitions used to be. Windows XP and the Recovery Partition look OK (naturally). Before this debacle, Gparted would show up to /sda10, including the extended partition and three Swap Partitions ( I had an empty partition where eeeBuntu used to be). I used Boot Info Script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) to generate the attached Result.txt to display what I have left.
 
The questions are:
 
1. Can I get my partitions back?
2. What is the best software to do this? Choices:
 
(1) DfSee? [http://www.dfsee.com/](http://www.dfsee.com/)
(2) TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
(3) Something else?
 
Note; the Ubuntu partitions were formatted with ext4.
 
Thanks in Advance,
John Morrow

---

### Post by johnson.d on 2010-03-09
I used testdisk a few times and found it useful. It shows the deleted partitions that were present before. It also lists the files of the deleted partition. You can easily recognize the partitions that were present before.

---

### Post by wally83 on 2010-03-09
Hi John, 

I have exactly same problem. Acer TravelMate 8371 and choosing wrong Windows loader will delete all ext-partitions (don't know whether I used ext4 or ext2, I suppose it was the former).

I tried also recover Windows Vista (and downgrade it to XP), but grub error remains. Linux-partitions (or actually unpartitioned space) remains untouched.

TestDisk seems promising, however it doesn't mention Ext4 at all.

I came across some manual way to recover lost partitions by knowing starting sector and guessing the size.

---

### Post by wally83 on 2010-03-09
At least with TestDisk (I used most recent version 6.12-WIP), it easily founds all my 3 lost Ext4 partitions (I thought I had only 2 of them...), so no guessing is needed.

I'll keep you updated, whether I get my partitions back or not.

Edit:
After writing the recovered partition table back, I'm quite sure that grub error changes. Now it says "error: file not found", previously "error: no such partition". So at least I have to recover grub. Now, let's see if partitions are ok.

Edit2:

At least home partition (most important one) is recovered! So, go with TestDisk.

---

### Post by wally83 on 2010-03-09
SOLVED:

1. Download TestDisk 6.12-WIP and extract it into bootable ubuntu usb stick
2. Boot from that stick (graphical or cli)
3. Run testdisk_static
4. Choose hard disk
5. "Analyze"
6. "Write"
7. Quit & Quit & Reboot

Grub may be still broken, but at least your partitions should be recovered now. You may for instance recover grub or re-install Ubuntu **without formatting** your disks, especially if you have a separate home partition.

---

### Post by JohnMorrow on 2010-03-09
wally83:
Thanks for your detailed replies; instructions and confirmation are always good. I will try TeskDisk out, possibly tonight. I don't want to reinstall Ubuntu without attaempting a recovery, because I had some pictures saved.

At the end of your repairs, were both your linux and windows fully usable (read/write)? Were you able to repair GRUB?

John

---

