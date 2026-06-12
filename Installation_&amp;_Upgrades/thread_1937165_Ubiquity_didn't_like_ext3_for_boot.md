---
title: "Ubiquity didn't like ext3 for /boot"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by meanmrmustard on 2012-03-07
Formatting as ext 3 failed so I chose /ext 2 and tried again.
The format completed (or at least was reported as done, 100%) but it stalled at that point.

This is the first time I've used a /boot partition.
Does /boot require a certain file system or should either ext 2 or 3 work?

---

### Post by surfer on 2012-03-07
my /boot is always on ext2. i just don't quite remeber why...

---

### Post by LinuxFan999 on 2012-03-07
> **meanmrmustard said:**
> Formatting as ext 3 failed so I chose /ext 2 and tried again.
The format completed (or at least was reported as done, 100%) but it stalled at that point.

This is the first time I've used a /boot partition.
Does /boot require a certain file system or should either ext 2 or 3 work?
Which version of Ubuntu are you trying to install?

---

### Post by meanmrmustard on 2012-03-07
> **LinuxFan999 said:**
> Which version of Ubuntu are you trying to install?

11.04 64 bit and using gpt to try , yet again, to install on a 3 TB external USB drive.

---

### Post by oldfred on 2012-03-07
With gpt you need the bios_grub partition, do you have that? 

You do not need a /boot and it makes things somewhat more difficult to manage as it is another partition to make sure you size correctly and houseclean. If boot issues you have to remember to mount it also. Many instructions on reinstalling grub do not mention /boot (or just have a footnote) as most desktops do not have a /boot. Often ext2 is uses as the journal is not required for a small partition that is just read from other than updates. Since it is small a file check can still be fairly quick.

I think Herman now does not even have a separate swap partition but uses a swap file.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

If using gpt with BIOS create a 1MB bios_grub partition. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.
Thus, you must make a separate "BIOS boot partition" to hold core.img. 

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

---

### Post by meanmrmustard on 2012-03-07
> **oldfred said:**
> With gpt you need the bios_grub partition, do you have that? 
Yes

> 
You do not need a /boot and it makes things somewhat more difficult to manage as it is another partition to make sure you size correctly and houseclean. If boot issues you have to remember to mount it also. Many instructions on reinstalling grub do not mention /boot (or just have a footnote) as most desktops do not have a /boot. Often ext2 is uses as the journal is not required for a small partition that is just read from other than updates. Since it is small a file check can still be fairly quick.


This is basically an experiment so I'll drop the /boot partition. Never used one before but I'm up for the learning so I thought I'd include it. Makes sense to simply things as much as possible. Maybe I'll play with that later.
> 

I think Herman now does not even have a separate swap partition but uses a swap file.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Thanks!
> 
If using gpt with BIOS create a 1MB bios_grub partition. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Yup, did that.
> 
In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.
Thus, you must make a separate "BIOS boot partition" to hold core.img. 

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on



Can I assume you have done a full Ubuntu  install on a 3 TB or larger drive?

Thanks for your help.

---

### Post by oldfred on 2012-03-07
No I have only used gpt on my 160GB, 16GB flash and my new 64GB SSD. I am thinking about converting my 640GB drive from MBR to gpt but have lots of data and only most is backed up. The only MBR I may keep is my XP drive which is mostly idle.

I do not fully understand the new 4K drives. Some seem to have more issues than others.

---

