---
title: "&quot;Error loading operating system&quot; + partitioning"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by DavidCain on 2008-04-22
My PC has two 160g redundant hard drives. When trying to install Ubuntu, I tried the "Guided- use entire disk" option, but following the installation, on reboot I get the error message "Error loading operating system". I suspect this has something to do with partitioning my hard drive(s). If not, any help fixing this error would also be appreciated.

So, what is a good way to partition my drive(s) for a working copy of Ubuntu? The Ubuntu installer recognizes each drive seperately as /dev/sda and /dev/sdbAlso, being able to use both drives would be amazing, I'm running low on storage, even with a 100GB remote server. Thanks in advance.

---

### Post by nightcrawler27 on 2008-04-22
During installation, was a boot partition created/specified? Which drive did the boot loader get installed on? I realize you said you have 160G redundant drives, but it is possible that the drives were not partitioned that way and that the boot loader is not installed on the proper disk, etc.

nightcrawler27

---

### Post by DavidCain on 2008-04-22
Let me just be clear that I don't *want* redunancy, my machine just used to be set up that way. 320GB would be far better than 160GB, I have some storage where I can back up essential things).

Okay, so I can't really answer too much of your question, since I'm pretty unfamiliar with partitioning (Windows set ups are all I've done, and they're pretty unspecific and easily done). I'm pretty sure a boot partition was created. I followed the directions about creating a swap partition larger than 256 MB and a main partition under "/". I'll go check out some help threads on partitioning in the meantime.

---

### Post by Pumalite on 2008-04-22
If you can boot a Live CD, post:
sudo fdisk -l

---

### Post by DavidCain on 2008-04-22
After a failed install, I partitioned the first drive (/dev/sda) with a 4g swap and the rest as my /). I deleted all partitions on my second drive (/dev/sdb), leaving it as free space. This is pretty much just from screwing around aimlessly with partitioning.

output from sudo fdisk -l:
```

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18696   150175588+  83  Linux
/dev/sda2           18697       19452     6072570    5  Extended
/dev/sda5           18697       19452     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System

```


I've been fooling around with different partitioning setups, mostly having no idea what the hell I'm doing (just a few tips like swap should be 2x RAM, make the main /, and that being primary or logical really doesn't make a difference). I no longer get the "Error loading operating system" message on reboot. Instead I get:

No boot device available
  Strike F1 to retry boot Strike F2 for Setup Utility
(I press F1)
GRUB GRUB loading stage1.5
GRUB Hard Disk Error

---

### Post by DavidCain on 2008-04-22
Okay. In what I'm going to call a stroke of genius, I decided to just disconnect the hard drive I'm not using by disconnecting the cables that connect it to the power supply and by disconnecting the cables that lead to the motherboard. It actually worked, and I'm typing this on the fully installed Ubuntu.

So, it does kind of suck that I now have a 160GB drive just sitting in my case, unused. My BIOS detected that "Drive 2" was missing, so this should only be a temporary solution.

I'm perfectly willing to repartition, reinstall Ubuntu, or whatever I have to do. How do I partition the drives (or do whatever is necessary) so I can run Ubuntu on my system with access to each 160GB drive?

---

### Post by Pumalite on 2008-04-22
Do not use Raid. All you have to do is format your 2nd drive after connecting it again. You can use Gparted Live CD. Format it ext3. You can use it for storage or as a separate /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
4 GB of /swap might be too much if you have 2 GB of RAM. I'd use 1 GB.

---

### Post by DavidCain on 2008-04-22
Thank you very much, Pumalite. I heard 2x your RAM may be excessive, but since I have plenty of space, I may stick with it.

---

### Post by Pumalite on 2008-04-23
Happy Ubuntuing!
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

