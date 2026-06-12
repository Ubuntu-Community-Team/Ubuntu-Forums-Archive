---
title: "Installing Ubuntu on USB, booting from the same USB."
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by ByaTsuke on 2012-12-29
So I have installed the 12.10 ubuntu iso on my portable HDD.
It boots up, and it always comes up with the menu saying "try ubuntu" or "install ubuntu".

I tried to Install Ubuntu, but it said my computer has no OS so it said about erasing my partition, I am not sure which partition it wants to erase?

I am using Ubuntu ONLY because my Main "C" partition is in trouble due to Windows Registry Corruption that can't be fixed by the recovery/installation disk. 

So I am looking forward to recover my files using TestDisk (which works but...) but, whenever I reach near 1.8 gb, it says there's no more freespace and doesn't copy the rest.  I went to properties of the "File Systems" partitions and it has a limited freespace of around 1 gb or so. 


I am guessing this is some kind of limitation that can be passed by fully installing ubuntu.

I have 3 main partitions.
1. C drive - Windows OS, corrupt with all my files which I am trying to get.
2. D drive - 50gb back up partition I made long time ago and "was" accessible, but when I started the ubuntu installation it got messed up. It only took 5 seconds before I had to forcefully shut it off.

3. My external HDD which my Ubuntu boots from, and I am trying to install the fully functional bootable version on. 

How do I do this? and how am I able to extract my old files? TestDisk DOESN"T offer an option to copy the files to any other partition other than the existing ubuntu partition. 
The existin ubuntu partition has some limited space, when my HDD has around 450gb of free space. 

Also all files are erased after restart, probably because I am trying and haven't installed it yet.

---

### Post by gnush on 2012-12-29
Are you saying that you want to replace Windows with Ubuntu? If so, do you want to erase everything on the hard drive? If so, you can do the following.

```
# dd if=/dev/zero of=/dev/sda bs=4096
```The command above will completely erase everything on the drive, overwriting everything with zeroes.

**Be cautious!** Make sure that sda is really the disk you want to wipe; if Windows resides on another disk, then change accordingly. Do note that the partition table will also be wiped.

This will probably take several hours, but you could use badblocks which can be slightly faster.

Once that's done, Ubuntu should be able to reconize the disk as empty and ask you if you want to format it, and use the entire disk.

---

### Post by ByaTsuke on 2012-12-29
> **gnush said:**
> Are you saying that you want to replace Windows with Ubuntu? If so, do you want to erase everything on the hard drive? If so, you can do the following.

```
# dd if=/dev/zero of=/dev/sda bs=4096
```The command above will completely erase everything on the drive, overwriting everything with zeroes.

**Be cautious!** Make sure that sda is really the disk you want to wipe; if Windows resides on another disk, then change accordingly. Do note that the partition table will also be wiped.

This will probably take several hours, but you could use badblocks which can be slightly faster.

Once that's done, Ubuntu should be able to reconize the disk as empty and ask you if you want to format it, and use the entire disk.
No no, thats exactly what I am not trying to do, because I have important files in there which I am trying to retrieve through testdisk, but won't let me as the "Try Out" version seems to have space limitation of 1gb eventhough my external usb hardrive is 500gb. 

I want to keep my old computer hard drives and only install Ubuntu on my External portable hard drive which I am also booting ubuntu from. I want to install the full thing on my external hard drive, not just a bootable try out thing.

---

### Post by monkeybrain2012 on 2012-12-29
Do you mean you currently have a live Ubuntu system installed in the external hd and you want a full install to replace it? 

You need to make a different live usb or live cd and use it to install Ubuntu into the external hard drive.

So let's say you get a flash drive and put Ubuntu in there (a live usb), boot into it, then  attach your external hd. Then choose "install Ubuntu".

Choose "something else" when you are prompted to choose a method to install. A graphic representation of all your mounted drives and partitions should appear. Choose the external hard drive you want to install Ubuntu into (in this scenario it would be something like sdc, sda would be the internal drive, sdb the live flash drive, it may be sdb if you use a cd to install etc) Before you do that make a swap partition of about 1.5Xram and format the rest as ext4, mount point should be "/"

*important*, at the bottom of the page it asks you where to install your bootloader. Choose the same external drive where you install Ubuntu in (/dev/sdc or /dev/sdb in this case, default is /dev/sda which is the internal drive)

Then just continue and wait.

Once you finish, boot off the external hard drive and you should be able access the windows partition in your internal drive (remember to remove the flash drive or the cd for installation before reboot)

---

### Post by monkeybrain2012 on 2012-12-29
> **gnush said:**
> Are you saying that you want to replace Windows with Ubuntu? If so, do you want to erase everything on the hard drive? If so, you can do the following.

```
# dd if=/dev/zero of=/dev/sda bs=4096
```The command above will completely erase everything on the drive, overwriting everything with zeroes.

**Be cautious!** Make sure that sda is really the disk you want to wipe; if Windows resides on another disk, then change accordingly. Do note that the partition table will also be wiped.

This will probably take several hours, but you could use badblocks which can be slightly faster.

Once that's done, Ubuntu should be able to reconize the disk as empty and ask you if you want to format it, and use the entire disk.

I think OP has some data he wants to retrieve from the Windows partition first. Moreover it is not necessary to use dd to wipe the disk first if he wants to install Ubuntu in the internal drive. I think that operation is  dangerous and may ground his hard drive.

---

