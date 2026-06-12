---
title: "Remove Second Unbuntu Install"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by bch36 on 2008-08-22
I dual-booted Ubuntu with Windows XP for a while before deciding I liked Ubuntu enough to kill Windows XP.  I booted on a LiveCD and destroyed my Window's NTFS partition using GParted, but ended up borking GRUB (error 17).

After trying a dozen things over several hours, I finally installed Ubuntu a second time on the old NTFS partition, now ext3 partition.

Doing so ended up repairing GRUB and allowed me to boot back into my original Ubuntu install, but now I have a new Ubuntu partition I don't need.

The new Ubuntu partition is a primary partition, and the boot partition.  My old Ubuntu partition is an extended partition with two logical partitions, the ext3 partition and the swap partition.

Question: how do I remove the newer Ubuntu installation on the primary partition without killing my old Ubuntu installation again?

From my understanding, I need to change my old extended partition with two logical partitions into a primary partition(s) somehow.  How would I do this without killing GRUB?  Similarly, how would I destroy the new ext3 partition without killing GRUB?  How would I need to modify the menu.1st file afterwards, if at all?  How would I update the MBR, if necessary?  Thanks for any information!

---

### Post by coffeecat on 2008-08-22
I'm assuming that the grub menu (and grub stage 2) are on the new Ubuntu partition - the one you want to wipe out. If you have a usable grub menu (and stage 2) on the old partition, all you have to do is reinstall grub stage 1 to the mbr with the correct root reference.

Let's assume your 'old' Ubuntu root partition is sda5, then you would need to open a terminal and"

```
sudo grub
```That gives you the grub prompt (>). Then from the grub prompt, three commands:

```
root (hd0,4)
setup (hd0)
quit
```.. and that should do the trick. Grub's partition counting is different - it starts from 0, and note the use of the comma and brackets.

I was also assuming you had just one drive. If you want, post the output of 'sudo fdisk -l' and we can check this. Don't do the above unless you are sure there is a usable grub stage 2 and menu.lst in the old Ubuntu root partition, otherwise you'll have a large hole to dig yourself out of.

---

### Post by manishtech on 2008-08-22
Additonally you dont merge the primary partitions into extended partitions. 

Apart from this I saw that you mentioned of having put a boot partition too. Which one is this. Can you post the output of

```
sudo fdisk -l
```

Here l is small L
Dont delete this /boot partition, you can again mess up with GRUB!

---

### Post by bch36 on 2008-08-22
The output of "sudo fdisk -l" is below.  Despite what it says, I have a single 160 GB drive.  Thanks for your help so far!


>sudo fdisk -l

Disk /dev/hdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1          13      104391   83  Linux
/dev/hdd2              14       38913   312464250   8e  Linux LVM

---

### Post by coffeecat on 2008-08-22
Now that I've seen your fdisk output, please ignore everything I said about reinstalling grub. You have a [LVM partition]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29"). I understand the square root of hardly anything at all about LVM, so I'm going to duck out gracefully here.

But not before expressing bewilderment at the fdisk output. Have you any idea why it's reporting a 320GB drive when you say it's a 160GB? Also, fdisk is calling your single drive hdd. Do you know what happened to hda, hdb and hdc? :-k

---

### Post by manishtech on 2008-08-23
> **bch36 said:**
> The output of "sudo fdisk -l" is below.  Despite what it says, I have a single 160 GB drive.  Thanks for your help so far!


>sudo fdisk -l

Disk /dev/hdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1          13      104391   83  Linux
/dev/hdd2              14       38913   312464250   8e  Linux LVM
I am also unable to figure out what happened to sda,sdb and sdc. Why is size 320GB. I also dont have much idea of LVM. But can you post the output of

```
ls -l /dev/sd*
```

So that I can find out what are the different partitions in your system on all hard disks . Please remove all removable media like flash drives,SD cards etc before issuing this command.

---

### Post by bch36 on 2008-08-23
Thanks for your help!

Running "sudo fdisk -l" again gives new results today:

[FONT="Courier New"]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3c75

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10684    85819198+  83  Linux
/dev/sda2           10685       19026    67007083+   f  W95 Ext'd (LBA)
/dev/sda3           19027       19457     3462007+   c  W95 FAT32 (LBA)
/dev/sda5           10685       18367    61713634+  83  Linux
/dev/sda6           18368       18700     2674791   82  Linux swap / Solaris
/dev/sda7           18701       19026     2618563+   c  W95 FAT32 (LBA)[/FONT]

Not sure what the deal was last time, but this seems more normal.

Running ls -l /dev/sd* gives the following results:

[FONT="Courier New"]brw-rw---- 1 root disk 8, 0 2008-08-22 02:46 /dev/sda
brw-rw---- 1 root disk 8, 1 2008-08-22 08:50 /dev/sda1
brw-rw---- 1 root disk 8, 3 2008-08-22 08:50 /dev/sda3
brw-rw---- 1 root disk 8, 5 2008-08-22 08:46 /dev/sda5
brw-rw---- 1 root disk 8, 6 2008-08-22 02:46 /dev/sda6
brw-rw---- 1 root disk 8, 7 2008-08-22 08:50 /dev/sda7[/FONT]

---

### Post by Elfy on 2008-08-24
Coffecat has it right I believe - even the partition on which the old install is. Is that installation not available at the end of the current menu list?

I would boot the newer one and then make sure you have a /boot/grub on sda5; once you are sure reinstall grub using the livecd - making sure to pick the old install.

Then once that has booted you will be able to reformat the 'new' install

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by manishtech on 2008-08-24
Since now you have two GRUB installed on each Linux partitions and one of them is pointed by MBR.

First login to any ubuntu, goto grub using the command
```
sudo grub
```now type this command to find out how many copies of GRUB you have on your disk and where are all those located
```
find /boot/grub/stage2
```Now say you got two partitions (hd0,1) and (hd0,6). 
GRUB partitions are numbered sequentially starting from zero. Now is you want to remove partition 1 (second) then deleting that partition point MBR to GRUB on (hd0,6). This can be done by typing this command at grub prompt 
```
root (hd0,6)
setup (hd0)
```Replace (hd0,6) by whatever partition you get in the find command

Note: Take care of the space between "root and ( " and "setup and (". Quite common mistake :D

---

