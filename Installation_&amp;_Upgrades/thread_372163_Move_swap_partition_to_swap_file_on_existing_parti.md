---
title: "Move swap partition to swap file on existing partition"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by idn on 2007-02-27
Hi, I have installed ubuntu successfully on a macbook pro (edgy), here is my partition layout:

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2   *          26        5248    41943040   af  Unknown
/dev/sda3            5248        5503     2048000+  82  Linux swap / Solaris
/dev/sda4            5503       12161    53487372   ef  EFI (FAT-12/16/32)

```

I wanted to install another distro on system, but because of EFI (macbook pro uses this instead of a BIOS) I can only have 4 partitions max. What I want to do is remove the swap partition (/dev/sda3) and resize the osx partion (/dev/sda2) so I have a big enough partition to install a second LInux OSX (for bleeding edge unstable hackery) on /dev/sda3

I then want to create a swap file and install that on my existing Linux partition (sda4). I found this on the ubuntu wiki for tripple mounting

```

sudo su 
mkdir /mnt/linux
mount -t ext3 /dev/sda3 /mnt/linux
sudo dd if=/dev/zero of=/mnt/linux/swap bs=1024 count=2097152
mkswap /mnt/linux/swap
swapon /mnt/linux/swap 

```

But this is what you do when your in the live CD I believe not booted in the existing intall. So basically I want to know how to do this when running on my distro installed on /dev/sda4, as mentioned this is edgy. I could try and figure this out buts iuts not really somethign I want to play with :)

Cheers

---

### Post by Kateikyoushi on 2007-02-27
You have to add it to your fstab as swap partition.

---

### Post by tgalati4 on 2007-02-27
The reason you want to do it from a Live CD is you don't want to mess with the swap partition of a running system.  That could cause a kernel panic.  Just as you can delete /usr and /bin of a running system, it won't be running for long and it won't reboot!  

The 4 partition limit is a drag.  Perhaps there are some other work-arounds, like using Firewire external drives and putting your distros on that.  Keep one swap partition on the internal drive (small one) and put another on the firewire drive.  Linux will detect them both and use them.

Since drives are cheap these days, I wouldn't jeopardize a working system by  moving partitions.  Get another drive instead.

When you want to experiment, plug in a new drive.  Paint it test-dummy orange first, as a reminder.

Good luck.

---

### Post by idn on 2007-02-27
> **tgalati4 said:**
> 
Perhaps there are some other work-arounds, like using Firewire external drives and putting your distros on that.  Keep one swap partition on the internal drive (small one) and put another on the firewire drive. 

The external drive is a good idea, although its a laptop so it would suck that I couldnt use any other distributions unless I'm at my desk because i wont be able to use the external drive on the move. It is an idea I havent considered before for my desktop system tho, no more messing around with partitions if I want to test out a new distro such as the latest and greatest ubuntu lol

> **tgalati4 said:**
> The reason you want to do it from a Live CD is you don't want to mess with the swap partition of a running system.  That could cause a kernel panic.  Just as you can delete /usr and /bin of a running system, it won't be running for long and it won't reboot!  
.

OK cool maybe the best approach is to do this through the live CD, would there be a risk that I mess up my existing install?

---

### Post by Kateikyoushi on 2007-02-27
As much as usually with partitioning. I do not think swapon is dangerous did on gentoo installs.
Someone whose swap did not work yesterday just activated it and did not write back he had problems.
Of course you can not resize or move mounted partitions.

---

### Post by tgalati4 on 2007-02-28
Moving partitions is always risky.  That is why you get warnings before committing to write the new partition table.  Normally it should be OK, but there is a small chance for error, and when it goes you can kiss your install goodby.

You can buy some small external drives these days.  Check out LaCie's Porsche drives.  Smaller than a pack of smokes.  You can also use an iPod, which you probably carry anyway.

Charge your iPod, listen to new music, and check out a cool new distro all from one device.  Uber cool.  Take an 8 GB nano, partition it 4 GB for music and 4 GB for a new distro, have fun.  Use the existing swap partition on the internal drive.  Be sure to max out the ram in your notebook.  Anything less is cheating Linux big time.

---

### Post by idn on 2007-02-28
hey, i managed to do this now, I created a swap file on my linux partition and now removed the swap partition and everything works ok :) I did it through the live CD. I now have a free partition to install another OS, it was going to be vista or XP so i can play games but to be honest I'm probably gonna install another linux distro lol :)

thanks for the help

---

