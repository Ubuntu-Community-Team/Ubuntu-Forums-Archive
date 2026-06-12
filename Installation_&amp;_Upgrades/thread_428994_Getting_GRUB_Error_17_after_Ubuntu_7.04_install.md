---
title: "Getting GRUB Error 17 after Ubuntu 7.04 install"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by sethtriggs on 2007-04-30
I'm trying to build a dual-boot system for my friend because WinXP is just absolutely useless. (I am leaving the old system intact and have insalled Ubuntu in the unpartitioned space on the former second harddrive, which is now the master.)

Ubuntu seemed to install perfectly from the live CD, but after a restart I get the dreaded GRUB Error 17, at Stage 1.5.

I'm kind of a newbie to Linux, but I promise you I will do my best to keep up—I want to get Linux for my own machine and it's probably good to just jump in and get my feet wet with an installation problem.

Here's what Gparted (GNOME Partition Editor) says I have here...

------

Partition, Filesystem, Size, Used, Unused, Flags
/dev/hda1, ntfs, 129.12 GiB, 118.10GiB, 11.02GiB (This is the old secondary Windows partition - not bootable by Windows)
unallocated, 3.69 MiB
/dev/hda2, ext3, 19.05 GiB, 2.29GB, 16.76GiB, boot
/dev/hda3, extended, 894.24MiB
/dev/hda5, linux-swap

----

The GRUB seems to be correctly set, I think. Menu.lst reports that the default (Groot) is set to (0,1), and scrolling down the file I am able to see that this one is the Ubuntu, kernel 2.6.20-15-generic. So that seems correct. I am not sure what I am doing wrong with this install here.

Thanks in advance for any help!

-Seth

---

### Post by psusi on 2007-04-30
Try reinstalling grub with the force-lba option.  Boot from the livecd and do this:

sudo mount -t ext3 /dev/hda2 /mnt
sudo chroot /mnt
grub-install --force-lba /dev/hda


If that doesn't work, you will need to make a /boot partition that is on the first 8 gb of the disk.

---

### Post by sethtriggs on 2007-04-30
The last command, grub-install --force-lba /dev/hda resulted in the command:

Not Found or not a block device.

Did I type something wrong?

-Seth

---

### Post by psusi on 2007-04-30
Ooops... that's right... /dev is going to be empty these days since udev is used.  Before the chroot command, do a:

sudo mount --bind /dev/ /mnt/dev/

---

### Post by sethtriggs on 2007-04-30
Welp, didn't work...but thanks anyway!

And now I am in fear, because the first partition on this second master drive is an NTFS partition: the secondary storage for Windows. Now, I have been told that the data on it is expendable, but I would prefer to not lose the data. Is there any way of non-destructively changing this partition?

If not I guess I will have to buck up, go offload its contents and then format the drive.

-Seth

---

### Post by psusi on 2007-05-01
What do you mean it didn't work, and why do you want to change the ntfs partition, and how do you want to change it?

---

### Post by sethtriggs on 2007-05-01
I still ended up with the GRUB Error 17.

I did try running the script again but I found that the Windows wouldn't load. I am now allowed to wipe the drive clean, fortunately. So I will give that a shot. Windows will not load now due to a "disk read error," so I am kinda stuck.

-Seth

---

### Post by psusi on 2007-05-01
Hrm... sounds like your disk may be damaged.  Let's do a read test on it.  From the livecd do:

sudo dd if=/dev/hda of=/dev/null bs=65536

This will probably take a good while but hopefully it will finish without any errors.

---

### Post by sethtriggs on 2007-05-01
Allright, I will try that when I get back home.

-Seth

---

### Post by sethtriggs on 2007-05-01
> **psusi said:**
> Hrm... sounds like your disk may be damaged.  Let's do a read test on it.  From the livecd do:

sudo dd if=/dev/hda of=/dev/null bs=65536

This will probably take a good while but hopefully it will finish without any errors.

Output:

2442845+1 records in
2442845+1 records out
160041885696 bytes (160GB) copied, 2743.51 seconds, 58.3 MB/s

Off to wipe the drive, then will try a new install.

-Seth

---

### Post by sethtriggs on 2007-05-02
On the fresh drive, I now get GRUB Error 18. Which at least is not 17 I guess. Will have to try figuring this out somehow. Will let you know how troubleshooting that goes.

-Seth

Addendum:

Looks like the problem may be the 137GB limitation. Unfortunately, since this PC is a former HP Pavilion 7935, that means an OEM BIOS (yet another danger of proprietary systems right there) and there is no BIOS update for it. And I've searched far and wide on the Internets for it. So I am now trying an install with partitions set up as follows on the 160GB drive (which Linux correctly sees)

Root (/) is allocated 50GB at the beginning of the drive
Data (/data) is allocated 109GB at the middle of the drive
Swap is allocated 999MB at the end of the drive.

Wish me luck!

Addendum 2: **SUCCESS!**

Ubuntu has safely booted. Now I will try to connect the other Windows drive and set it to auto-mount...in order to have accessible files.

---

