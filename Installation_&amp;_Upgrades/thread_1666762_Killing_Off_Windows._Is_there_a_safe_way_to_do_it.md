---
title: "Killing Off Windows. Is there a safe way to do it?"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by jackharvest on 2011-01-14
It's a typical story:

Has Windows 7.
Installs Ubuntu 10 on separate Partition.
Likes it better than windows.
Wants all the space of the Solid State Drive.
Says "ta-hell with Windows".

So, my idea for doing this is as follows:

Boot to PartedMagic (basically gparted) - and then delete the partition that is Windows 7, followed by resizing the Linux partition to take the entirety of the SSD...

The only flaw here is... where the hell is GRUB2 located? I'm scared it's on the Windows partition, and wont boot after I do this. The windows partition IS flagged with "boot" within parted magic, so I'm going to bank on that being the case.

Is there a way to either move GRUB2 beforehand, or reinstall GRUB2 after all hell breaks loose from killing off the windows partition?

Thanks, all help is welcome. Many posts related to this one, but... not quite exact. :popcorn:

---

### Post by coffeecat on 2011-01-14
> **jackharvest said:**
> Boot to PartedMagic (basically gparted) - and then delete the partition that is Windows 7, followed by resizing the Linux partition to take the entirety of the SSD...

That should work. If you haven't already downloaded Partition Magic, don't bother. Gparted comes on the Ubuntu live CD. If I need to do any partitioning work from a live CD I always use the Ubuntu CD. A few points about resizing your Ubuntu partitions.

If your Ubuntu root partition is a logical partition, you'll have to enlarge the extended partition that contains it first. If you are enlarging a partition "backwards" - that is to the front of the hard drive - this can take a very long time indeed. Moving/resizing partitions carries the risk of something going wrong. **Very** wrong. Backup first.

And if your swap partition is a logical one, the Ubuntu live CD (I don't know about Partition Magic) will automount that, so that you won't be able to resize the extended one. Simply right-click on the swap partition in Gparted and "swapoff".

> **jackharvest said:**
> The only flaw here is... where the hell is GRUB2 located?

Grub stage 1 is in the mbr. Some more code is in the embedding area - that's between the partition table and the start of the first partition. The rest of grub is in /boot in your Ubuntu root partition. Removing the Windows partition(s) won't affect grub, but if something does go wrong, bookmark this:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

... and/or post for help here.

> **jackharvest said:**
> The windows partition IS flagged with "boot" within parted magic, so I'm going to bank on that being the case.

The boot flag is only needed for Windows. Linux doesn't need a boot flag to boot.

Once you've removed Windows and got yourself a single-booting Ubuntu system, simply run this terminal command to refresh the grub menu and remove references to Windows:

```
sudo update-grub
```

---

### Post by dino99 on 2011-01-14
you are right to think about grub2 indeed. What you can do is:

sudo dpkg-reconfigure grub-pc

that will popup a dialog box showing you where it is actually installed, simply check the ubuntu partition to be sure to boot on after winblow removal.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by jackharvest on 2011-01-14
Perfection. Thanks Coffee Cat.

I guess I had the right idea. I was just cautious cause you know how it is when the boot loader (whatever it may be) dissapears. Frigg'n nightmare.

**All went smoothly!**

---

