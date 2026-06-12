---
title: "ubuntu server installation and existing partition"
date: 2019-10-14
forum: Installation &amp; Upgrades
---

### Post by emanuelemx on 2019-10-14
I need to install ubuntu server on a disk where partitions are already present.
What I want to do is not to lose the sdb6 partition, then install ubuntu on the remaining disk and then after installation do the sdb6 mount.
But during the installation I can't set the partitions.
Help?

Thanks

---

### Post by oldfred on 2019-10-14
What brand/model system?
Post this:
sudo parted -l

---

### Post by TheFu on 2019-10-14
We need much more data and facts to help.  How are we supposed to know what sda7 is?

Boot into a Live-Boot desktop environment and install "boot repair".  **Don't let it actually perform any repair.** THAT IS IMPORTANT!  Center bottom of the screen, there is a "gather info" button. Press that and post the URL back here.

If here is anything you don't want to lose, be certain to make a backup.  Dealing with partitions is a common way to wipe entire disks by accident.

If you are new to Linux, it would be safer to use virtualization.  This doesn't risk your current partitions and if properly tuned, you can get 90-95% of the performance that running directly on the hardware would provide.  Just depends on the hardware and settings.  I first started running Linux inside VMs around 2006 at home.  It is a great way to learn more about Linux with very little risk (zero?).

---

### Post by SeijiSensei on 2019-10-14
> **emanuelemx said:**
> But during the installation I can't set the partitions.
The installer has an option (the one at the bottom of the list) that lets you specify exactly how and where you want the system to be installed.

---

### Post by emanuelemx on 2019-10-15
Ubuntu server 18.04

parted -l

num----    start-------end ---------dimension    -------type------    file sys
1         ------512B ------526MB-- ----    526MB----------       prim------     ext3
2 -----        526MB- --  17,7GB------   17,2GB------- -      prim------     linux-swap
3        ------17,7GB---   36,6GB-- ---   18,9GB--------    prim      
4 -----       36,6GB---   1000GB -----  964GB--------      extend  
5 -----       36,6GB----    115GB------    78,7GB-------    logic--------       ext4
6 -----       115GB ----    1000GB-----  885GB-------      logic -------     ext4

---

### Post by emanuelemx on 2019-10-15
in the installer it allows me to choose manual partitioning, but only to personally create partitions, without showing me the existing partitions

---

### Post by TheFu on 2019-10-15
Looks like you need to shrink at least one of the logical partitions to make room for 1 ,2, 3, or more partitions for the new installs.  The size of sda4 is the limiting factor. sda5 and higher numbered partitions must fit inside sda4.  That's a limitation of using MSDOS partition tables, like it appears this system does.
[B]
About that huge swap .... [/B]
BTW, 17G is way, way, way too large for swap.  4.1G is the size needed, pretty much always. The old rules about 2-3x RAM for swap was valid when systems had 8MB of RAM.  As more and more RAM became common, the sizing of swap became less and less important.  

There are 2 reasons to have more 4.1G of swap:
a) you run a VPS and don't like your customers much, so you over-subscribe the users to the available RAM by a huge amount.
b) you use hibernation (which only makes sense for desktops, inside a controlled, physical, location). Never use hibernation for a laptop, if you care anything about security.

IMHO.

---

### Post by SeijiSensei on 2019-10-15
> **emanuelemx said:**
> 
num----    start-------end ---------dimension    -------type------    file sys
1         ------512B ------526MB-- ----    526MB----------       prim------     ext3
2 -----        526MB- --  17,7GB------   17,2GB------- -      prim------     linux-swap
3        ------17,7GB---   36,6GB-- ---   18,9GB--------    prim      
4 -----       36,6GB---   1000GB -----  964GB--------      extend  
5 -----       36,6GB----    115GB------    78,7GB-------    logic--------       ext4
6 -----       115GB ----    1000GB-----  885GB-------      logic -------     ext4

If you boot this system and run "df" we can see the mount points and the amount of space in use.  I'm guessing sda1 is boot and sda3 is the root filesystem?

What's in /dev/sda5 and /dev/sda6?  

I forgot you were installing the server edition which is text-only and doesn't offer as much flexibility as the GUI installer. You might consider booting from a desktop version and running gparted to examine the drive graphically. Then you can decide whether to lop off some of /dev/sda6 and create a new partition.

---

### Post by emanuelemx on 2019-10-16
I have no problem deleting all the partitions, except sda6, that would keep it intact.

---

### Post by TheFu on 2019-10-16
> **emanuelemx said:**
> I have no problem deleting all the partitions, except sda6, that would keep it intact.

Before you do anything, please make backups of anything that cannot be lost.  From here, we cannot tell what any of those partitions holds except the swap.  

Backups are needed anyways.

---

### Post by yancek on 2019-10-16
What operating system do you currently have installed and which release version?
What is on sda6, is that a data partition?

Using an msdos partitioning scheme as you are, you have an Extended partition (sda4) which contains sda5 and sda6.  If you delete the other partitions, particularly sda5, the sda6 partition will be changed to sda5 and will not be accessible without making changes to the /etc/fstab file.

sda6 is a very large partition.  You could use GParted to shrink that partition and create other partitions in that space.  Post the output of df -h as suggested above before you do anything.

---

### Post by SeijiSensei on 2019-10-16
If /dev/sda5 is dispensible, you could install the new version there and leave /dev/sda6 filling the rest of the extended partition. If /dev/sda1 was used as /boot, continue to do that.

As TheFu says, you have way too much swap. You could delete both it and /dev/sda3, then allocate maybe 4 GB to swap as /dev/sda2, and create a new /dev/sda3 comprising the rest of the old swap partition and the current /dev/sda3.  If you don't have a dedicated /home partition, I'd install Ubuntu to that new /dev/sda3, which should be about 30GB, and use /dev/sda5 for /home.

---

