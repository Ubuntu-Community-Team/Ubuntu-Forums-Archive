---
title: "New install sda hard drive problem"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by emperor on 2005-11-18
Here what I have on the ata-150 sda hard drive before Ubuntu install:

NTFS  Primary 10GB active
Extended Primary 66GB
Fat32  Logical  10GB
Linux Swap  Logical 2GB
Linux Ext3   Logical 12GB
Unallocated Logical 42GB

Note: I created the Linux Swap and Ext3 partions with PM8.

Now when I try to install Ubuntu and get the the manual partioner, my only options are "Software Raid" or "LVM". I do NOT want "LVM". In the past past 10 or more Ubuntu installs, I have always been able to manually create and select the partions I want and did NOT have to enable LVM. 

So, why is the "let me do it myself" option missing from the manual partioner?

I do NOT want to lose my Win2000 installation as this is my office computer and we still need to use windows most of the time. 

The same problem occurs if I do not pre-create the Swap and Ext3 Logical Partions

---

### Post by Kipper on 2006-01-10
To be honest I would not use PM8 on a dual-boot setup as it can lead to trouble which you can see from posts elsewhere on this forum and other places. 

I would tend to do a /fixmbr from your Win2k CD before anything else.  I've not exeperienced this behaviour myself, but I would suspect the Ubunutu partitioner may be having trouble interpreting your BIOS/SATA controller settings and not seeing the SATA as a single disc on which you can create the partitions as you wish.

---

### Post by emperor on 2006-01-10
Thanks for your comments!

I think your right in that there is something goofy going on with the partions created by PM8. I'll move the FAT32 partion to a primary partion and delete the ext'ed and logical partions along with the fixmbr step and see it that helps make the linux partioner happy.

---

### Post by Kipper on 2006-01-11
One thing I did notice about the Ubuntu partitioner is that it seems to have a preference for making primary partitions when it can and making one active. In setting up a dual-boot system I'd be a little weary of this. ( I don't know of any particular dis-advantage of using an extended partition sub-divided inot logical partitions. Linux doesn't seem to care. ) 

If GRUB is used as the bootloder it is fine, as a combination of "makeactive" and "chainload" commands are used to boot your Windows install. But what happens if you install Ubuntu, use it's partitioner, and then for some reason abort the install. Is your Windows primary partiton still active and still bootable?

Maybe I should have said make sure your Windows primary partition is still active before doing a /fixmbr.

---

### Post by emperor on 2006-01-19
The problem was apparently caused by the disk controller configuration being incompatible or not properly supported in the kernel. The motherboard is an industrial single board computer that plugs into a passive backplane and has both an IDE and SATA drive support onboard. When configured for 3 master/slave's, Ubuntu fails to detetect the 80GB SATA drive on #3 Master. However, when setup in compatiblity mode, just two (2) Master/Slave's, Ubuntu detects the SATA drive properly on #2 Master So, I am on my way, installing Ubuntu 5.10 as I write this post on another machine.

PM8 was not an issue in my case!

---

