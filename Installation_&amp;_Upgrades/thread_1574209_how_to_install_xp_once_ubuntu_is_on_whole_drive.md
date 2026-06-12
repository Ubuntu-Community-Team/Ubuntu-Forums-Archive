---
title: "how to install xp once ubuntu is on whole drive?"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by duhfactor on 2010-09-13
I'm a new user to ubuntu, and want to keep it running on this machine. My business uses quickbooks, and I can't get it to run unless it's on a windows box. I wondered if there is a safe way to partition my current hard drive, so that I can install xp and quickbooks on this same machine as dual boot, leaving ubuntu on it as configured, without changing it as well. Forgive my noobiness, I'm learning as I go...

thanks,

D

---

### Post by oldfred on 2010-09-13
How easy it is depends on how you have partitioned so far and where within the partitions, the space you can make is.

You have to have a primary partition, formated NTFS with the boot flag, or free space and an available primary partition for Windows to install into. Windows will not see your Ubuntu partitions. You may want to consider another NTFS partition for shared data. I have my firefox & thunderbird profiles in the shared partition so I have the same data in both systems and do not directly write into the XP partition.

Post this or a screenshot of gparted
```
sudo fdisk -lu
```Talks about dual boot windows Vista but info applies to all copies of windows:
Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by duhfactor on 2010-09-13
here's what I have;

root@damon-desktop:/home/damon# sudo fdisk -lu
sudo: unable to resolve host damon-desktop

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00017232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   476632484   238316211   83  Linux
/dev/sda2       476632485   488392064     5879790    5  Extended
/dev/sda5       476632548   488392064     5879758+  82  Linux swap / Solaris
root@damon-desktop:/home/damon#

---

### Post by duhfactor on 2010-09-14
By the way, I don't plan on sharing any files between the two operating systems. I'm only needing the xp so I can run quickbooks, connect to the internet, and run an e-mail application. I don't need a huge partition for just that I don't believe. I don't recall having partitioned the drive intentionally when I set ubuntu up origionally. I'm still running 8.04.

thnks,

D

---

### Post by oldfred on 2010-09-14
Using gparted just shrink sda1 and insert sda3. Partitions will not be in order but there is no requirement that they have to be.

Some versions of gparted (Ubuntu's liveCD) may not include the NTFS drivers. If you download the separate gparted liveCD it does, or in the Ubuntu liveCD you can download NTFS tools. Not sure if it is just ntfs-3g and/or ntfsprogs from synaptic. (search on NTFS) Besure to set boot flag on sda3 for windows.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by duhfactor on 2010-09-14
Thank you, I'm beginning the tutorial reading on g-parted. I have one concern, the g-parted tutorial claims that windows and a few other operating systems will claim the primary partition as default, and that it should be loaded onto the hard drive first, before a linux distro. I have already installed ubuntu on the primary partition. Maybe I'm getting ahead of myself here, but how can I load xp if my primary partition is already taken? When I use g-parted and create a new partition, does it use a different filesystem that will be recognized by xp as the primary or only partition?

D

---

### Post by oldfred on 2010-09-14
Windows works fine from any primary partition sda1 thru sda4. If you want more you have to convert one primary to an extended that can hold many logical. You have used sda2 as the extended currently only with swap. If you think you may want even more partitions leave room to expand the extended to add logicals. You still can create sda3 & sda4 as primary partitions.

Some think windows has to be first and it usually is but it is not a requirement. The main reason they often suggest installing windows first is that you have no choice, it will install its boot loader into the MBR, and you will have to reinstall grub. But reinstalling grub2 is easy, just one more step that you would not have to do if windows was first.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by uidb4056 on 2010-09-14
> **duhfactor said:**
> I'm a new user to ubuntu, and want to keep it running on this machine. My business uses quickbooks, and I can't get it to run unless it's on a windows box. I wondered if there is a safe way to partition my current hard drive, so that I can install xp and quickbooks on this same machine as dual boot, leaving ubuntu on it as configured, without changing it as well. Forgive my noobiness, I'm learning as I go...

thanks,

D

You can have another alternative that will let you run an XP OS inside Ubuntu as a virtual machine avoiding to have to restart to select another OS. You can install VirtualBox from repositories (OSE version without support for USB) or PUEL version from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) . After you have installed you can create a new virtual machine and install XP or other OS's on it.

---

### Post by QIII on 2010-09-14
+1 for virtualizing, particularly since you are only interested in one app in particular.

If you need to, you can move files outside of the .vdi by creating a shared folder in VirtualBox.

---

### Post by duhfactor on 2010-09-14
I didn't know about the virtualization option, now I know what people are talking about on the forums about it. If I do use that option, will xp still download service packs, updates, etc automatically? I worry about my capacity to do that kind of thing manually. The disk I have is an older xp os, pre- service pack, so I will need to download updates. Also, when running in xp in a virtual machine, will I need to run compatible antivirus and antispam software?

thanks,

D

---

### Post by duhfactor on 2010-09-15
I guess I'll look for a virtualization tutorial, any advice on where to start?

Thanks,

D

---

### Post by QIII on 2010-09-16
Look at [www.virtualbox.org]("http://www.virtualbox.org").  Their documentation is extensive.

I recommend the PUEL version, which can be downloaded and installed from there.  The PUEL version gives USB support.  It does not offer Virtual Network Computing (VNC) because of licensing issues.

The OSE version you can download from the repos does not offer USB, but you can use VNC.

Yes, you will be able to update.  Yes, you do need to take care to use antivirus software.  Viruses can attack your .vdi (Virtual Desktop Image), which is the virtual hard disk the OS runs on.

You will want to install the Guest Additions to your virtual OS to be able to control things like resolution, text C&P and such.  I also recommend making at least one shared folder with your host OS in case you want to move a file to where it is accessible to the host's file system.

If you find that you have specific questions (I don't want to tell you "RTFM" because sometimes user manuals are inscrutable for the first-time user), then feel free to come back and ask questions.

I'd start a new thread with each question because this thread will eventually get buried.

---

### Post by dmizer on 2010-09-16
> **duhfactor said:**
> I guess I'll look for a virtualization tutorial, any advice on where to start?

Thanks,

D

Lots of great information on Virtualization here -> [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308) At the top of the forums there is a virtualization megathread. I suggest you start there.

With a virtual machine, you need to think of it just as if it were a real, physical machine instead of virtual. So yes, you will need all the updates, antivirus, etc.

---

### Post by odelance on 2010-09-16
For virtualization, you will need RAM for both system: Ubuntu and XP. I used them on a 750MB old computer with any problem. If you have less, be careful. RAM is main virtualization problem.
I use both dual boot (for Windows games) and XP virtual machine on Ubuntu guest and second solution is more user friendly, as you can switch from one Windows application to an Ubuntu one immediately.

---

