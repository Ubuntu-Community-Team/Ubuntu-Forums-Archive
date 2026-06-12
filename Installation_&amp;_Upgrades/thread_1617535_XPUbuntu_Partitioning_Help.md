---
title: "XP/Ubuntu Partitioning Help"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by drifter2502 on 2010-11-09
I have 2 partitions in XP, C drive  has 40 GB used and 30 unused and is boot. D drive has not been used and is empty according to 'My Computer/ D Drive/ Properties.  I want to install Ubuntu on this partition but when I examine this partition with GParted it shows 3 GB used !  I don't know if this is a 3 GB hidden file of some sort, perhaps for XP recovery or back up. The rest is 37 GB of empty space. Can I use 36 GB of this for the Ubuntu partition in ext 3 , perhaps extended with a root and swap for Ubuntu , leaving  4GB in ntfs for XP to do whatever it wants to do? 

Gparted indicates a red triangle with  exclamation markmfor C drive and I don't know what it means.

Also, do I have to elect boot under  'Flags` in GParted or leave boot as is in XP C drive ?


I would be grateful  for suggestions as to a layout. Many Thanks.   Drifter

---

### Post by dabl on 2010-11-09
Win XP does not require a "rescue" partition, and if the computer OEM had put one on it, it would not be as large as the one that you have, so I don't think it is for that purpose.  I would want to know for sure what data are there, however.  Hopefully the alleged 3GB is just for filesystem overhead.

Is it a NTFS filesystem?  If so, you can mount it and take a look at whatever data is there, from a running Ubuntu Live CD. In the terminal, first:

```
sudo fdisk -lu
```

This will tell you the /dev/sdx number for the partition that you want to look at. Let's say it turns out to be /dev/sda2.

Next, make a mount point:

```
sudo mkdir /mnt/temp
```

and then mount it:

```
sudo mount -t ntfs-3g /dev/sda2 /mnt/temp
```

now have a look at the contents:

```
ls -la /mnt/temp
```

Once you're sure you don't need a backup (or alternatively use nautilus and back it up), then you can use GParted to format that partition to ext4, and go ahead with the Unbuntu installation.

Leave the "boot" flag set on the Win XP partition, unless you have a finicky BIOS that requires it to boot Linux.  It's easy enough to change it after installation, if that's the only issue  you have.

If your system doesn't have at least 2GB of memory, you would be wise to make a small third partition, for swap.  Make it 1.5X your memory.

---

