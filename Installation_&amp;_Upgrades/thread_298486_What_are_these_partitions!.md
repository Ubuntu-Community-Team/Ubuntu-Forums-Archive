---
title: "What are these partitions?!"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by Yayzik on 2006-11-12
I'm trying to install Dapper on my girlfriend's new laptop, and when I got into the partition editor (she wants an XP and an Ubuntu partition), there were a number of partitions already set up, and I have no clue what any of them (except the NTFS one) are. There are:

/dev/sda1     fat16      47.04 MB

/dev/sda2     ntfs       78.13 GB   boot

unallocated              26.98 GB

/dev/sda3     extended   2.00  GB   lba
  /dev/sda5     fat32      2.00 GB    (caution sign beside fat32)

/dev/sda4     fat32      4.64  GB

I tried to create a new partition out of the unallocated space for Ubuntu, but it said that I could only have 4 partitions set up at a single time. Problem is, I don't know what to get rid of!

Can anyone tell me what the other partitions do and which one(s) I can get rid of to install Ubuntu? Thanks!

-Yayzik

---

### Post by chriscando on 2006-11-12
My Dell laptop had a few simular partitions. One contained some recovery drivers, and another one contained some media direct software. When I got my laptop I wanted a clean slate and erased everything which worked fine for me.
I dont know if you are in a simular situation. But my rule is if I dont know what it is, its probably not important (not always the case thought).

It said you can only have 4 partitions, it probably means you can only have 4 logical partitions, try making an extra on that is an extended partiton.

---

### Post by Velotix on 2006-11-12
I'm probably not much help on this kind of thing (yet - I love to learn ^^) but here's the first (obvious) point that you haven't made clear:

Do these partitions show up in Windows?

(That FAT16 partition is a surprise, I must admit.)

The second point: have any recovery images or the like been made on the laptop? Windows has a feature that allows you to restore a previous configuration of your computer if something goes wrong, but to do that it has to save an image file somewhere - I'm guessing it makes a partition for it that is hidden in Windows but lights up like a christmas tree in Linux.

The third, semi-relevant point: you'll probably end up with three partitions when this is all over: Windows, Ubuntu and Ubuntu's swap partition, which is set up during install.

---

### Post by RRS on 2006-11-12
/sda's 1, 5, and 4 are most likely the various "restoration" partitions used to reinstall windows instead of using a cd.

The limit of 4 primary partitions on a drive seems universal no matter the system.

You should be able to use gparted from your live cd to enlarge the extended partition (/dev/sda3) to include the free space. Then create a swap (1 to 1 and 1/2 X your ram) and an ext3 partition inside it.

After saving any important data and defragging XP you may also have enough empty space in /dev/sda2 to shrink it and then also include this space in /dev/sda3 to create another fat32 partition to share files between windows and Ubuntu.

If gparted from the Dapper live cd protests you might try the latest version of gparted on its own. Check [here]("http://gparted.sourceforge.net/index.php").

---

### Post by confused57 on 2006-11-13
> **Yayzik said:**
> I'm trying to install Dapper on my girlfriend's new laptop, and when I got into the partition editor (she wants an XP and an Ubuntu partition), there were a number of partitions already set up, and I have no clue what any of them (except the NTFS one) are. There are:

/dev/sda1     fat16      47.04 MB

/dev/sda2     ntfs       78.13 GB   boot

unallocated              26.98 GB

/dev/sda3     extended   2.00  GB   lba
  /dev/sda5     fat32      2.00 GB    (caution sign beside fat32)

/dev/sda4     fat32      4.64  GB

I tried to create a new partition out of the unallocated space for Ubuntu, but it said that I could only have 4 partitions set up at a single time. Problem is, I don't know what to get rid of!

Can anyone tell me what the other partitions do and which one(s) I can get rid of to install Ubuntu? Thanks!

-Yayzik

My dell has a 40 mb FAT16 utility for troubleshooting on the first partition.
Your sda3 is an extended partition containing the sda5 logical partition and sda4 is probably a Windows OS recovery partition.
Ubuntu can be installed on a logical partition, so you "should" be able to use the Ubuntu installer and make logical partitions in the sda3 extended partition to install Ubuntu on, without having to delete any of your other partitions.
  I've done this on a Linux machine, but I'm not sure about extended partitions created by Windows.
  During installation, you'd select the unallocated space to install Ubuntu on and since you already have 4 primary partitions, Ubuntu will automatically make logical partitions for your installation.

I don't know, but installing Linux on a new computer may affect the warranty coverage...before installing, make sure you read over how to uninstall Ubuntu or repair the Windows mbr(need a floppy drive, or the actual Windows install cd, not a recovery cd):
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

