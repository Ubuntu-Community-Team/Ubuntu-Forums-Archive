---
title: "btrfs - Anyway of installing as / filesystem?"
date: 2009-12-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Bike-and-snow on 2009-12-23
Hello

I have been testing Lucid recently.

Does anyone know if it is possible to install Lucid onto a / filesystem that is btrfs?

I must stress I am doing testing using a virtual machine and I don't care about the data on the machine.

It's not an option in the disk partitioner.

Are there any console commands I can run to do it?

Thanks.

---

### Post by farrell on 2009-12-23
This should still work for Lucid (was written for Karmic Alpha 3) but takes quite a few step:

[http://howtoforge.com/boot-on-btrfs-with-debian#comment-15153](http://howtoforge.com/boot-on-btrfs-with-debian#comment-15153)

I'm highly interested if this (still) works or if there are easier ways of doing it nowadays.

Cheers

---

### Post by VMC on 2009-12-23
> **farrell said:**
> ...I'm highly interested if this (still) works or if there are easier ways of doing it nowadays.

I'm interested too. I've read recent articles saying its much faster than Ext4. Don't ask me for the articles, I just read them in passing. If anyone here has used btrfs before on any system, I would like to know your results.

Here's one [link]("http://oss.oracle.com/projects/btrfs/dist/documentation/benchmark.html"). Not sure of its age, but btrfs is not too impressive on their results.

---

### Post by kev000 on 2010-02-19
It should be as easy as using btrfs-convert on the drive.  the lucid kernel already has btrfs built in.

I'm trying to figure out a way to do post convert compression on the whole drive.  The only way I can think of is to boot to a live lucid instance and do a cp -pr / /mnt/foo; cp -pr /mnt/foo /.  Anyone see any hangups I may run into trying that?

---

### Post by Ibidem on 2010-02-19
GRUB2 can't boot/recognize btrfs.  Grub legacy never supported it.
So you'll need to put /boot on ext2/3/4 or something else that works.
You'll also need to change /etc/fstab so the fs type is recognized.

Ibidem

---

### Post by Kenny_Strawn on 2010-02-19
Supposedly, BTRFS puts Linux on par with Mac OS X as far as file system features.

OS X's Time Machine operates as an automatic backup and snapshot utility for OS X. BTRFS also has its functionality - only this time, built into the FS itself - very innovative indeed.

You can see a list of plenty of other features [here]('http://btrfs.wiki.kernel.org/index.php/Main_Page'):

[quote="BTRFS Wiki"]
The main Btrfs features include: 
 
[LIST]
[*] Extent based file storage (2^64 max file size)
[*] Space efficient packing of small files
[*] Space efficient indexed directories
[*] Dynamic inode allocation
[*] Writable snapshots
[*] Subvolumes (separate internal filesystem roots)
[*] Object level mirroring and striping
[*] Checksums on data and metadata (multiple algorithms available)
[*] Compression
[*] Integrated multiple device support, with several raid  algorithms
[*] Online filesystem check
[*] Very fast offline filesystem check
[*] Efficient incremental backup and FS mirroring
[*] Online filesystem defragmentation
[/LIST]
[/quote]

---

### Post by iggykoopa on 2010-02-20
I've been running it as root on lucid for a little while now, it's been going pretty well. The only real problem I've run into is I installed it mainly for the compression since I have a 32gb ssd, but I've run into the bug that the filesystem appears full even though it is reported as only being about 65-75% full with df. It's something to do with the way it allocates the meta-data. I guess from the threads I've read on it they plan to fix it once the filesystem is considered ready for production, but it kinda sucks now.

---

### Post by Jordanwb on 2010-02-20
I'm going to try btrfs in VirtualBox using a 5 disk Raid 5 array. Why include RAID? Because I can. If btrfs is really fast I may use it on my laptop.

It took an hour to install and grub won't install to the boot partition. All it says is "This is a fatal error."

---

### Post by antiram on 2010-02-20
[http://ubuntuforums.org/showthread.php?t=1389279](http://ubuntuforums.org/showthread.php?t=1389279)

---

### Post by falconindy on 2010-02-20
I've been running btrfs as root for about 2 months now. I can't honestly say it's **that** much faster (if at all) than ext4.

However, I will admit that I made the mistake of not enabling 'compress' option when I copied my files back over during the switch. I recently converted my build partition to btrfs, made sure to enable compression, and i **do** notice a distinct speed increase as far as basic file operations goes. Of course, full disk compression is recommended only if you have clock cycles to spare.

---

