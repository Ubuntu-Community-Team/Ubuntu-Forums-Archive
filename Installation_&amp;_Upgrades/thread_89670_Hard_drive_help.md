---
title: "Hard drive help?"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by psychofish on 2005-11-13
Hi all,
I'm new at this and I really don't want to mess anything up. I just put in a new 300 GB hard drive and I want to try out ubuntu 5.04 (don't have the 5.10 cd yet-- I got the 5.04 in the mail a month ago) but I also have Windows on a separate hard drive. I partitioned the 300 GB hard drive at about 275 GB for stuff (music, photos etc. -- this is already on the partition), and the other 25 GB to install ubuntu on. I did the formatting process in Windows.

When I do the installation and I get to the hard drive part, I am at a complete loss. First of all I do NOT want to use the guided process and reformat an entire disk; both drives already have things on it which I want to retain.

So if I try to manually edit the second partition of my 300 GB drive (the 25GB I've set aside for ubuntu) I'm not really certain what to do. What should the file system type be? I'm familiar with FAT32 but is that just for windows compatibility purposes? Should I use that or another one which may be better? What's the mount point and why is it telling me "/dos" or "/windows" when I'm not installing either one? And how do I set up something as the "root"?
Do I need to change anything on my other partitions? I'm afraid of touching those at all because I don't want to destroy existing data.

Any help would be appreciated, thanks.

---

### Post by Megatog615 on 2005-11-13
Set the mount point to "/", set the type to "Ext3", and you should be good to go. As long as you don't touch those other partitions you have, you're fine.

You'll need SwapSpace too, I recommend making a partition the same size as the amount of RAM you have, and setting that to Swap.

---

### Post by paddyg on 2005-11-13
I'd like to add a couple of things more.

If you've got windows Partition Magic, just use it to add a swap partition (someone says 2 times your ram, and never bigger than 2 GB each---for example, you need 4 GB swap, so two 2 GB swap partitions)

Never ever use fat32 with linux---bad performance and no journaling. You should only use fat32 on a spare exchange partition---not the system)

Install grub (linux bootloader) to the MBR. Grub will let you boot windows as well.

---

### Post by psychofish on 2005-11-13
Thanks for the speedy replies! I did as you said and proceeded without a hitch. I have another question though, if I am to access the files on my other drives, would I have to mount them as something (ie "/home") in ubuntu?

I can't do it from install anymore since that's already done but how would you do it from within the OS?

---

### Post by Megatog615 on 2005-11-13
Most likely Windows is at /dev/hda1, so make a new folder in the /mnt directory called "Windows" like this:
```
mkdir /mnt/windows
```
Then, mount the Windows partition like this:
```
mount /dev/hda1 /mnt/windows
```
If you are unsure of where Windows is located, try using fdisk -l. It will show you the partitions in a list. The one that is FAT32 or NTFS(or any Windows/DOS filesystem) is likely to be your Windows partition.

---

