---
title: "tripple boot xp/scientific linux/ubuntu"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by charstar on 2008-01-19
Hello,

I currently have a system running XP and Scientific Linux.  I would now like to add Ubuntu to the mix.  I have have never tried booting multiple linux distributions before.  Here is the partition table as it is now.

number    Partition            type               label
01            /dev/sda1         ntfs    
02            /dev/sda2         ext3              /boot
03            /dev/sda3         swap
04            /dev/sda4         extended
   05         /dev/sda5         ext3              /
   06         /dev/sda6         ext3              

I have xp on sda1, scientific on sda5, and I want to install Ubuntu on sda6.  

what i am unsure about is what the label on the ubuntu partition should be.  I had at one point labeled it /.  Then found out that scientific will not boot properly if the two partitions are labeled /.  So, what label if any should i give to sda6?

I am also not sure what i should do with grub.  If i tell ubuntu to use /boot to install grub, will it pick up the other linux install? Or is it better to put the ubuntu grub on its own root partition and chainload?

I haven't managed to make it this far in the install because the installer complains that sda6 has not been marked for formatting.  Do i have to delete the partition and have the installer format it? And if this is the case, when i set the mount point, does this mean that is what the partition label will be?

Thanks for your help.

---

### Post by louieb on 2008-01-19
Just tell the installer the mount point for sda6 is / (root) and let the installer format sda6. It likes to have a clean partition for the / (root) file system.  If you want just label it **UbuntuRoot **doesn't really matter what the label is.

As far a the GRUB setup goes. All I going to mention is GRUBS chainloader and configfile options. Thats what I use. Great info on multi booting  here   [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/").

Good Luck.

---

