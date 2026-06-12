---
title: "Dual Booting"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by UncleMonty on 2010-01-27
What pitfalls are there to avoid when dual booting? What can go wrong?

---

### Post by darkod on 2010-01-27
The biggest is resizing your windows partition and whether you have multiple hard disks or only one.
Scenario 1: single hdd, windows takes all of it either in single partition or more ntfs partitions
If windows is taking the whole hdd you have to shrink its partition to create unallocated space for ubuntu. For Vista and 7, use windows disk management which is able to shrink partitions. Unless you have to, do not do this shrinking with the ubuntu installer (install side-by-side option). After the shrink boot windows few times to make sure it's happy with it and to do any disk checks it might want. DO NOT CREATE ANY PARTITION IN THE UNALLOCATED SPACE FROM WINDOWS!!! For XP, which doesn't have the resize option in disk management, boot the ubuntu cd, Try Ubuntu option, open Gparted (System-Administration) and shrink the XP partition as much as you want. DO NOT CREATE ANY PARTITION IN THE UNALLOCATED SPACE THAT WAS CREATED!!! Boot XP few times todo its disk checks.

After the above is done, boot with ubuntu cd, Install Ubuntu option, and in step 4 use the Use Largest Available Free space option. That will set up ubuntu into the unallocated space. Alternatively, create partitions manually into the unallocated space if that's your plan, but make sure you know what you're doing.

Scenario 2: multiple drives
If you have more than one hdd, and you plan to have both windows and ubuntu on the same drive, the same thing about resizing from above applies. And the following...

With multiple drives it's always BEST to check where the bootloader will be installed. If dual booting with windows and ubuntu on separate drives, you would usually want grub2 on the ubuntu disk. In the last screen during installation, before clicking Install, click on Advanced and make sure the bootloader (grub2) will go to the disk you want it. In step 4 you can note the name of the disk in linux terms, for example /dev/sda, /dev/sdb, /dev/sdc etc. Make sure you don't install it in a partition (/dev/sda1, /dev/sdb3 etc). There should be no number. Unless you specifically want grub2 onto a partition.

That's about it IMHO.

---

### Post by howefield on 2010-01-27
> **UncleMonty said:**
> What pitfalls are there to avoid when dual booting? What can go wrong?

Very little, if you are prepared. :)

Or at least, it is easy to get yourself in a position where if something does go wrong, you can put it right with a minimum of effort.

By that, I mean all your files safely backed up to another disk or media and a system image taken of your disk and backed up on a seperate disk to the one you are working on.

One pitfall is not being able to get into one operating system or another after installing and rebooting, particularly with grub2. This forum has plenty of such support requests. Generally means updating grub.

---

### Post by yogesh.girikumar on 2010-01-28
Hi,


       There are some important things that one needs to be careful about.
       

**1. Partitioning the hard disk.**

       It's good to be careful while partitioning the hard disk. Your existing data in the HDD might be erased if you're not careful while partitioning. I always go for a manual partitioning when installing the OS.
       

**2. Choosing the hard disk partition type.**

       You need to choose a partition filesystem type that suits your needs best. It should preferably be compatible with the multiple operating systems that you might be planning to use ( windows + linux compatible ). You might also want it to support features such as security flags, ACLs, support for large file names and file sizes, journaling, snapshots etc.,
       

The default filesystem type for linux system partitions (like /, /var, /etc, /boot etc..) should be one of the many available formats such as Ext3, Ext4, etc.. And for windows the system partition (the one on which you install the OS) should be FAT32 or NTFS. For any other extra partition commonly shared by both, i.e if you have a partition as a data store from which you want to be able to access files from say both windows and linux, FAT32 is a good choice. If you have exceptionally large files to handle, go for NTFS. Linux has a fairly decent support for FAT and NTFS filesystems.
       

**3. Order of Installation:**

       Also, it's a good idea to install any windows installation before installing linux. Linux recognizes any windows installations already present in the system and add it to the boot menu (GRUB) entry. But windows doesn't recognize any other operating system. Hence it's better to install windows first and linux later.
                   [URL="http://10.10.43.151:3000/issues/show/104#"]
[/URL]

---

### Post by oldfred on 2010-01-28
Just so you can see what it is like here are some links. Even if not the exact version these give some understanding of the screens and process:

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

APC various dual boot graphical install
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)
Installing Ubuntu 9.10 Step-by-step installation tutorial with screenshots
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
Jaunty Jackalope / Windows7 Ultimate MultiBoot 'C' (with checkbox graphic for vista/7) 
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

