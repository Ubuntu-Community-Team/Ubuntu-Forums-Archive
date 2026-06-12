---
title: "Installer Can't Detect My Hard Drive"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by superawesomepanda on 2011-11-19
I tried installing 11.10 just now and the installer can't seem to detect my desktop hard drive but it detects my external hard drive. When I unplugged the external hard drive, then it doesn't give me the first option to install alongside Windows 7.

Any fix? Or should I just do it manually, as in the third option?

---

### Post by darkod on 2011-11-19
1. I always prefer doing it manually, you have best control of the partitions.

2. If it's what I think it is, even the manual partitioning will not see the hdd as present. Usually this happens if the disk has been used in raid earlier because it keeps raid meta data on it and the ubuntu installer ignores it.

If you are NOT using raid, boot with the cd in live mode (Try Ubuntu), open terminal and execute:

sudo dmraid -E -r /dev/sda

If that asks you whether you want to remove raid data, this was the problem. Just confirm and reboot again with the cd and do the install.
Note that if you ARE running raid this command will destroy your array, so DON'T do it! For installing on raid there is different procedure.

---

### Post by superawesomepanda on 2011-11-19
I got this: 

root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4bab6698

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       25497   204696576    7  HPFS/NTFS
/dev/sda3           25497       40795   122880000    7  HPFS/NTFS
/dev/sda4           40795       60802   160705536    7  HPFS/NTFS
root@ubuntu:/home/ubuntu# dmraid -E -r /dev/sda1
no raid disks and with names: "/dev/sda1"
root@ubuntu:/home/ubuntu# dmraid -E -r /dev/sda2
no raid disks and with names: "/dev/sda2"
root@ubuntu:/home/ubuntu# dmraid -E -r /dev/sda3
no raid disks and with names: "/dev/sda3"
root@ubuntu:/home/ubuntu# dmraid -E -r /dev/sda4
no raid disks and with names: "/dev/sda4"

---

### Post by darkod on 2011-11-19
That's because you are using a partition and not the whole disk. Look in my post again, it said /dev/sda not /dev/sdaX.

/dev/sda is a whole device, a hdd

/dev/sdaX is the partition with number X on that device

---

### Post by superawesomepanda on 2011-11-19
Sorry, I did that first actually:

root@ubuntu:/home/ubuntu# dmraid -E -r /dev/sda
no raid disks and with names: "/dev/sda"

Same thing.

---

### Post by darkod on 2011-11-19
OK. According to fdisk you have 4 primary partitions on the disk. The ubuntu installer will need to create new partitions during the install but since 4 is maximum I guess that's why it does not give any option to install.

You will need to move all the data from one partition, preferably the last one, then delete it and create it again but as Extended (Logical), not Primary. When creating it do not take the whole space again, leave unallocated unpartitioned space where you want ubuntu to be installed.

Then you could install it with manual partitioning or with some of the auto options.

---

### Post by Mark Phelps on 2011-11-21
If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

After that, you will have to look at your partitions again, and decide which one you can delete -- to allow for the creation of a new one (Extended) to hold Ubuntu.

---

### Post by superawesomepanda on 2011-11-26
Sorry for the late follow-up. Distracted by Skyrim.

Anyways, I didn't leave any free space on my hard drive for Linux. So I just delete one of my Windows partition and its fine.

Thanks guys.

---

### Post by mercury80 on 2012-03-28
> **darkod said:**
> sudo dmraid -E -r /dev/sda

Sweet this did the trick for me. On Ubuntu 11.11...

---

### Post by tralla76 on 2012-04-12
Hi there !
It seems I have a similar problem, but none of the previous posts helped me solving it.
 
I've been running Ubuntu 10.4 LTS on an old Acer TravelMate 2702WLMi for almost 2 years now,  and without any serious issue. 4 days ago my laptop decided to not switch on, showing me a message of which I do not have any record.
I decided to reinstall everything again, using a USB to reboot (same as I did previously), but now GParted and Disk Utility can't see my Hard Disk at all.
 
I already reset the BIOS to factory defaults and then try again to Boot...same as before, but if I switch on the computer without accessing the BIOS, it gives me this message: [SIZE=1]"PXE-E61 Media Test Failure, Check Cable"[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]What am I missing here ?![/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Any help very much appreciated....Thanks[/SIZE]

---

### Post by darkod on 2012-04-12
Dead hdd?

Take out the hdd and connect it to another machine (you can also connect it to a desktop if it is SATA). See if it can be read or not.

---

### Post by mercury80 on 2012-04-13
> **tralla76 said:**
> Hi there !
It seems I have a similar problem, but none of the previous posts helped me solving it.
 
I've been running Ubuntu 10.4 LTS on an old Acer TravelMate 2702WLMi for almost 2 years now,  and without any serious issue. 4 days ago my laptop decided to not switch on, showing me a message of which I do not have any record.
I decided to reinstall everything again, using a USB to reboot (same as I did previously), but now GParted and Disk Utility can't see my Hard Disk at all.
 
I already reset the BIOS to factory defaults and then try again to Boot...same as before, but if I switch on the computer without accessing the BIOS, it gives me this message: "PXE-E61 Media Test Failure, Check Cable"

To me this sounds like a hardware problem. The best way to proceed would be to try the hard-disc in a working computer, like darkod suggested. 

But I would check if the disc is listed somewhere in your BIOS-settings first. Haven't decided what it would tell you, but it could be useful information.

---

