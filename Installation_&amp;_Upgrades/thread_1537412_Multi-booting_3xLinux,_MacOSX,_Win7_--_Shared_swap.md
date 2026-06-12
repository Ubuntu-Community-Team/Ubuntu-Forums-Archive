---
title: "Multi-booting 3xLinux, MacOSX, Win7 -- Shared swap?"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by HuckBerry on 2010-07-23
I've dual booted Ubuntu and Windows for years now and I've installed OSx86 on a separate drive which Grub2 picked up automagically and everything has been working great -- except I'm out of space.

So I bought a 1.5 TB drive and installed win7 into sda1 (100MB NTFS bootloader for windows) and sda2 (50 GB NTFS windows drive). I now want to install two or three flavors of Linux. I'm thinking Ubuntu 10.04, Debian 5.05, and (if I'm bold enough) gentoo. each in 50GB partitions. I've already partitioned the drive a bit putting a 1.2 TB shared NTFS partition at the end (sda10), and a 2 GB swap parition just before that(sda9)

My questions are:
(1) can all my linux distro's share that 2GB swap, or does each need it's own dedicated swap partition (installers generally assume you do)?
(2) can I re-partition space in the middle of the drive without messing with windows(sda1&2) and the shared part. (sda10)?

---

### Post by oldfred on 2010-07-23
If you do not hibernate you can share swap. Obviously if you try to save data into the swap for hibernation and boot another system then you overwrite the data in swap.

You can add your partitions anywhere. The order may not match the order on disk but that is not critical.  Of course they all will be in your extended partition.

I would think about a /data partition so you can have all your common data easily available in each install. I still have some data in a shared NTFS but most of my data is in /data and I run a small script to link it into my /home for every install. I only have Ubuntu versions so far so I do not know if my script would even work for other installs.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by HuckBerry on 2010-07-24
Thanks for the reply, having data in /home isn't really critcal for me as I'm the only user of this box. I generally leave everything on the NTFS partition (because windows will can read/write NTFS) and just set the bitmask in fuse to 777. Mounting that into home wouldn't be terribly hard.
 
What I'm most interested in is the procedure for telling the ubuntu-installer to use the pre-partitioned space. It gives you three options during the normal install "side-by-side", "Erase / use entire disk" and "manual". The first two aren't going to work for obvious reasons. Using the third is my best bet.
 
During the manual partitioning, (I don't have it in front of me so don't murder me if I can't remember this exactly) I remember that I was unable to alter pre-formatted partitions in anyway other than erasing them. Once I erased the partition I could of course tell it to format it and mount it at / or use it for swap. My question is why do I have to delete the partition? Can't ubuntu-installer just format and use the partitions as I built them before I started?

---

### Post by oldfred on 2010-07-24
I always set up partitions in advance and use manual install. I do not remember having to delete them. 
Just choose what to use it as, and what format.

---

### Post by HuckBerry on 2010-07-25
Yepp you're right, I ran through the installer last night and there is an option for using existing partitions. I might have been thinking of a previous version of ubuntu... or maybe I didn't look close enough during my last install attempt.

But so long as I don't hibernate a linux OS and then boot another I should be fine. Thanks. That being said, anyone know of an installable file system for ext4 for windows?

---

### Post by oldfred on 2010-07-25
I do not know of an installable file system for ext4 from windows. There is one for ext3 but I would never use it.

I generally do not want to write into system partitions from another system. I keep data both for windows & Ubuntu separate from system partitions and try not to write (but do read if available) from another system. Only when I have to repair windows do I write into my windows system partition.

---

### Post by HuckBerry on 2010-07-25
I can see where you are coming from with not wanting to access system partitions from a non-native OS. But if I found a reliable IFS for windows I wouldn't access partitions in which linux needs to boot, rather I would create separate ones solely for data.

To be honest, it isn't really often that I would run into a situation where I would need to access data from another OS. It's more of a convince thing than anything. That and if I should need to remotely reboot the unit into an OS other than grub's default, I need to edit a file that exists on an ext4 filesystem.

---

### Post by oldfred on 2010-07-25
You use linux, as almost all the repair CDs are linux based, to repair windows not the other way around. But Ubuntu does take a bit of learning as it is different.

---

### Post by HuckBerry on 2010-07-26
Maybe you misunderstood what I meant.

Imagine you're using VNC to work on a linux desktop from a remote location. But then need to use a windows program on a NTFS partition on the same drive as the linux. You can reboot the machine remotely but when it reboots, grub will default to linux

of vise-versa if you had windows set as the default OS

If you had access to the other OS, you'd have to alter grub's configuration to set the other OS as the default OS. This can easily be done in linux as grub's conf is on a linux partition. But it is impossible to do from windows without and IFS.

---

### Post by oldfred on 2010-07-26
Grub does not have to be in a ext partition. You can create a grub or grub2 only partition with just about any files system and use that to boot. I use grub2 to loopmount ISOs from my USB, it is in effect a grub only partition that is FAT32.

Herman has info on both grub & grub2 partitions
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")
Chainbooting grub2, install to partition & Make CD or floppy - saikee
[http://www.justlinux.com/forum/showthread.php?threadid=152790](http://www.justlinux.com/forum/showthread.php?threadid=152790)
Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)
grub2 partition
[http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/](http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/)

---

### Post by HuckBerry on 2010-07-26
a grub partition is something I've been meaning to do, but had held off because I assumed it had to be ext-based. An ext based grub partition didn't make a whole lot of sense to me since my Ubuntu install is pretty stable. But now that I know it can be made from, say, NTFS, that changes things quite a bit.

---

