---
title: "Allocating drive space for Installation"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by daviede on 2012-01-21
Installing Ubutu, I downloaded, got my USB ready, and booted my computer from the USB...
My plans were to install Ubutu alongside Windows 7.  I chose this option in the installation, but accidentally did not allocate enough space for Ubutu, so the installation crashed... so, I retried, but it was no longer giving me the option to install alongside Windows 7.  I even reformatted my USB to go through the whole process again, but,
Under step 4 here, [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download), where I choose the installation type, it does not give me the option to Install alongside Windows 7 now.

Is something about my crashed installation preventing me from being able to choose this option? 
How can I get it to have this option again?  I have not been able to find anything from the help site, so if you prescribe a link please make it specific.  I don't know much about computers, I've been working on this for seven hours now, so bear with me please.

Thank you.

---

### Post by darkod on 2012-01-21
Depending in what phase it crashed, it might not recognize now that you have win7 at all. Hence it's not offering option to install along side.

To start with, boot with the cd/usb in live mode (Try Ubuntu option), open Terminal and post the output of this command:
sudo fdisk -l (small L)

---

### Post by daviede on 2012-01-21
> **darkod said:**
> 
To start with, boot with the cd/usb in live mode (Try Ubuntu option), open Terminal and post the output of this command:
sudo fdisk -l (small L)
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x89e789e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   217263059   108631498+   7  HPFS/NTFS/exFAT
/dev/sda2       217263060   226628204     4682572+   7  HPFS/NTFS/exFAT
/dev/sda3       226629630   234440703     3905537    5  Extended
/dev/sda5       226629632   230381567     1875968   83  Linux
/dev/sda6       230383616   234440703     2028544   82  Linux swap / Solaris

Disk /dev/sdb: 2096 MB, 2096103424 bytes
24 heads, 23 sectors/track, 7416 cylinders, total 4093952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8ab39ac8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64     4093951     2046944    c  W95 FAT32 (LBA)

---

### Post by darkod on 2012-01-22
OK, doesn't look too bad.

At this moment, does win7 boot successfully when you start the computer? Or it can't boot?

---

### Post by daviede on 2012-01-22
Windows can boot.

---

### Post by darkod on 2012-01-22
Excellent. Now lets make more space for ubuntu.

Boot the ubuntu cd in live mode and open Gparted.
In live mode the swap partitions is usually mounted, you can see this next to /dev/sda6, it should have like keys symbol. That means it's mounted and locked for changes.
Right-click /dev/sda6 and select Swapoff. The keys symbol should be gone.
Then, delete one by one sda6, sda5 and then sda3.
Make sure you DO NOT touch sda1 and sda2.
After you have deleted them, to apply the changes in Gparted you need to click the button with the big green tick mark. Until you do, no changes are applied.

That will delete the ubuntu partitions created during the failed install.
Restart and let win7 load.
Open Disk Management and shrink /dev/sda2 to make more unallocated (unapartitioned) space for ubuntu. You should have at least 8-10GB, even better 15GB if you can spare that. I see that sda2 is quite small, if you can move all the data from it to sda1 and in Disk Management simply delete sda2 instead of resizing. That should gibe you enough unallocated space.
Restart win7 few times so it can do any disk checks if it wants (sometimes it does want to do checks after resizing partitions). This is very important step, let it do the disk checks it wants to avoid being confused by the resize.

After that start again the ubuntu install, select to install side-by-side with win7 and it should offer to install into the unallocated space existing.

For the future, it's always best to use win7 Disk Management to shrink windows partitions if you need unallocated space for ubuntu, and not to do it with the ubuntu installer.

---

### Post by daviede on 2012-01-22
Ok.  It's been successfully installed, now.  Thank you so much, Darkod! :)

---

### Post by darkod on 2012-01-22
No problem, enjoy it. Please mark the thread as Solved. You can do this in Thread Tools above the first post.

---

