---
title: "Dual-booting KUbuntu and Fedora"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by bfr on 2007-08-23
I already have Fedora 7 installed on my computer, but I want to dual-boot it with KUbuntu 7.04.  How would I go about doing that?  Just follow through the installation, and if it asks if I want to overwrite the current partition or something, I would just say no?

---

### Post by eggdeng on 2007-08-23
You need to install ubuntu to a different partiton to the one fedora is on. Your options are basically
a) create a new partition or partions by taking unused space from an already existing partition (fedora or other)
b) create a new partition or partions by using unallocated free space on the disk (if any)
You can either do this before installing using the gparted live cd [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") (recommended), or when you begin to install using the native partition manager.
The usual recommendation is to create at least one / partition and another swap partition (about double the size of installed memory) 
Unfortunately, fedora installs can be a royal PITA because they use logical volumes by default and very few partitioning tools are able to deal adequately with these.
By default, the ubuntu install will overwrite your MBR, replacing your current boot loader with its own (GRUB), although it should recognise the fedora install and include an option to boot to the fedora partition. Alternatively, you can instruct it to install GRUB to the new / partition which will leave your current bootloader intact. You can later perform a simple edit to the /boot/menu.list file to enable booting to ubuntu.

---

### Post by Dark Star on 2007-08-23
Simple creat another partition and install Kubuntu in it :) The grub will automatically be updated :D and you can easily dual boot :D

---

### Post by bfr on 2007-08-23
OK, thanks.

Just wondering, what about the gparted live CD would make it better than the Ubuntu native partitioner, if both work?  

And, just to be clear, I need to:

1. Create a new partition on my hard drive for kubuntu
2. While installing, either tell it to install GRUB to a new / partition (like /kubuntugrub in the file system) or just let Ubuntu's GRUB overwrite my MBR

---

### Post by bfr on 2007-08-23
OK, I've inserted the KUbuntu CD into my computer, and I'm posting from Konqueror right now.  At the same time, I'm also going through the Install wizard. I've chosen to manually partition the disk.  How would I do that?  I have:

/dev/sda1 ext3 /media/sda1 size: 106mb used: 23mb
/dev/sda2 size: 249949mb used: unknown

---

### Post by maybeway36 on 2007-08-23
106MB? Are you sure Fedora is installed?

---

### Post by bfr on 2007-08-23
Yeah.  I thought it was strange too, but what do I know...

---

### Post by eggdeng on 2007-08-23
Could be that sda1 partition is a separate /boot partition, it's about big enough. The fact that the installer can't read sda2 may be because anaconda set it up as a logical volume, which neither the ubuntu installer nor gparted can do anything much with.:( Except delete, that is.

---

### Post by bfr on 2007-08-24
> **eggdeng said:**
> You need to install ubuntu to a different partiton to the one fedora is on. Your options are basically
a) create a new partition or partions by taking unused space from an already existing partition (fedora or other)
b) create a new partition or partions by using unallocated free space on the disk (if any)
You can either do this before installing using the gparted live cd [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") (recommended), or when you begin to install using the native partition manager.
The usual recommendation is to create at least one / partition and another swap partition (about double the size of installed memory) 
Unfortunately, fedora installs can be a royal PITA because they use logical volumes by default and very few partitioning tools are able to deal adequately with these.
By default, the ubuntu install will overwrite your MBR, replacing your current boot loader with its own (GRUB), although it should recognise the fedora install and include an option to boot to the fedora partition. Alternatively, you can instruct it to install GRUB to the new / partition which will leave your current bootloader intact. You can later perform a simple edit to the /boot/menu.list file to enable booting to ubuntu.

OK, I've tried installing kubuntu and then Fedora, and Fedora and then kubuntu - multiple times.  And it hasn't worked.  :(

Maybe it's how I'm partitioning my hard drive (which holds about 200gb, btw)?  Should I just create a single partition that's ~100gb for kubuntu, and in the installer, tell it to use that?  And then Fedora will automatically use the other space?  Or is the problem that I need to create too partitions - one for kubuntu and one for Fedora, and then install them?  Which would yuo recommend installing first?

---

### Post by bfr on 2007-08-25
I finally got it to work!  I ended up doing something like the following to get it to work:  Creating a single partition that was ~100gb with gparted, installing kubuntu there, then installing Fedora in the free space, then removing the kubuntu partition, and then installing ubuntu in its place (re-installing kubuntu in its place probably would have worked too).  


Thanks for all your help!

---

