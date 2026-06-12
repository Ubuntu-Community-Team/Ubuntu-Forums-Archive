---
title: "Fixing partition table before Ubuntu / Windows 7 Dual Boot configuration"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by dabos on 2012-01-18
I'm experiencing some difficulties configuring an Ubuntu / Windows 7 dual boot. In my previous attempts to set this up, I believe I have messed up my partition table. I have a 1 GB RAID drive, which I have previously seen in gparted depicted as one drive. However, now I see two drives, /dev/sda and /dev/sdb, which are both unallocated. When I run gparted /dev/sda from the command line, I see "Can't have a partition outside the disk!".

This contradicts the picture I see in Windows 7 disk management, which displays a single hard drive, with 

[LIST]
[*]a 118 MB "Healthy (OEM Partition)"
[*]a 8.03 GB NTFS recovery partition
[*]a 825.72 GB NTFS partition for Windows
[*]97.66 GB of unallocated space where I hope to install Ubuntu
[/LIST]

Below is my output from fdisk -lu

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      240974      120456   de  Dell Utility
/dev/sda2   *      241664    17072127     8415232    7  HPFS/NTFS/exFAT
/dev/sda3        17072128  1748731903   865829888    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf32e34b4

   Device Boot      Start         End      Blocks   Id  System

```

Below is my output from sfdisk /dev/sda

```

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+     14      15-    120456   de  Dell Utility
/dev/sda2   *     15+   1062-   1048-   8415232    7  HPFS/NTFS/exFAT
/dev/sda3       1062+ 108853- 107791- 865829888    7  HPFS/NTFS/exFAT
/dev/sda4          0       -       0          0    0  Empty

```

I can also provide the output from running TestDisk from within Windows if this would be of use. I have omitted the output from these commands which correspond to my external hard drives. Again, let me know if these will help.

Once this is sorted, I'm hoping to format the unallocated space using gparted. However, I may need some assistance with this as my previous attempts have got me in the sticky situation I'm now in. But one step at a time I guess!

---

### Post by darkod on 2012-01-18
Have you tried installing with the Alternate Install CD which is recommended for RAID installs?

---

### Post by dabos on 2012-01-19
Thanks for the pointer to the Alternate Installer. I will give this a try this evening and report back.

My only concern is that I have previously seen the RAID drive correctly in gparted using the normal installer, so it sounds to me like the partition table does need fixing. I'm not sure how a different installer could interpret it differently. That of course could be a lack of understanding on my part though!

---

### Post by ronparent on 2012-01-19
Normally with the later releases of Ubuntu you would see the RAID drive correctly. The program 'dmraid' takes care of this. The absence of dmraid would more likely account for your not seeing the RAID than a corrupted partition table.

Your more serious problem is that you already have 3 primary partitions. Only four are allowed and you need a minimum of two more (a partition to install to and a swap) to install Ubuntu. I suggest using gparted to create an extended partition for installing Ubuntu to. You are allowed to create as many partitions within the extended that you would likely need or want to install to. 

Note that even when dmraid is running to allow you to see and manipulate your partitions on your raid drive, the individual disks making up your RAID will also apper in gparted as separate unallocated drives. Never try to modify the unallocated drives of you will definitely end up with messed up partition tables.

---

### Post by dabos on 2012-01-19
So on my return home tonight I created a bootable USB pen drive containing the Alternate Installer. I went through all the steps, creating partitions etc. This all seemed to go smoothly until it asked me where to install the boot loader. I tried a couple of locations: /dev/sda and /dev/mapper. The second attempt returned a 'Fatal Error'. I chose to 'Continue without Boot Loader'. This exactly mirrors the problems I experienced in previous install attempts using the regular installer - everything would be fine until the Boot Loader choice, then I would get a Fatal Error. In both cases, the installation appeared to complete despite this error.

Upon rebooting my computer, I am now presented with a grub rescue prompt. I cannot boot Windows or Ubuntu (presumably Ubuntu cannot boot as no boot loader was installed).

I then created a second bootable USB pen drive using my Macbook using the regular installer so I could boot from this in Live mode.

I can now see my RAID hard drive in gparted. However, my Windows partition contains a red exclamation mark. The information screen for this partition contains the following:

<snip>
Checking filesystem consistency...
Accounting clusters...
Filesystem check failed! Totally 1 cluster accounting mismatches. 
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!"
</snip>

Obviously I would run chkdsk if I was able to boot into Windows! And going back to the apparent completion of the Ubuntu install - the partition I attempted to create during the installation remains 'unallocated' in gparted.

If I have to format my Windows partition and reinstall Windows - so be it. Obviously I would rather not have this inconvenience, but I have all my data backed up so it's not the end of the world if this is necessary.

---

### Post by darkod on 2012-01-19
If I remember correctly the bootloader goes to /dev/mapper. But the fatal error prevented it from installing correctly.

If you have a win7 dvd you can try restoring the windows bootloader and avoid reformatting and reinstalling windows.

There are also other tools if you don't have the win7 dvd.

---

### Post by dabos on 2012-01-19
I have a Win 7  DVD but it doesn't give me the option to repair Windows when I boot from it. I only get the option to reinstall.

---

### Post by darkod on 2012-01-19
On the screen where the big Install button is, on the bottom there is no Repair This Computer option?

---

### Post by oldfred on 2012-01-19
If you can get grub to load and give a Windows boot option then using f8 gets you into the repair screen. Many have said the timing from grub to Windows is quick so you have to be quick in pressing f8.

If you know anyone with the same version of Windows 32bit or 64 bit.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by dabos on 2012-01-20
> **darkod said:**
> On the screen where the big Install button is, on the bottom there is no Repair This Computer option?

Nope. When I boot from my Alienware Windows 7 Home Premium 64-bit disc, I always get taken straight into an installation wizard, no matter how many times I hammer F8 at startup.

I have a Windows 7 64-bit PC at work, so I will create a repair USB or CD today and try that tonight and report back.

---

### Post by dabos on 2012-01-20
The good news is I'm now able to get back into Windows, having booted to the repair disc I created at work then following these instructions:

[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

So in essence I'm back where I started. I have a 100 GB unallocated partition that I've reserved for Ubuntu.

The problem is I've been through the Ubuntu installer a number of times, and typically come unstuck when I get to the boot loader installation. Normally I get a fatal error, as described before, and have to use boot-repair from the LiveCD in order to resolve my non-booting issues. (Only when I used the alternate installer did I get into a situation where I was unable to boot any operating system, even after using boot-repair, and then had to create the Windows 7 recovery disc.)

Is there a definitive answer as to where I should install the bootloader? Or will there always be an element of uncertainty when installing to a RAID drive?

---

