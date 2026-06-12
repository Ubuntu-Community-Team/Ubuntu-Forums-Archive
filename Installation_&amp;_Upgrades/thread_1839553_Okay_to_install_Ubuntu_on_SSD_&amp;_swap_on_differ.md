---
title: "Okay to install Ubuntu on SSD &amp; swap on different physical drive"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by al111 on 2011-09-05
I'm getting an SSD this week, and wondering if it's okay to install the swap file on my Western Digital storage drive?

I'm dual-booting--

My plan is:

1) First install Win7 on the SSD--

2) Then install Ultimate Edition 2.6 (Ubuntu Lucid Lynx 10.04) on the SSD:

And install the 'Swap File' on the Western Digital drive--

Some of the usual SSD tweaks to follow--

Does this sound okay?  Thanks

---

### Post by Hakunka-Matata on 2011-09-05
No problem at all, check /etc/fstab UUID for the swap partition, if swap doesn't automatically turn on on the other drive.

If you make your swap partition the last one physically on the drive, no empty space behind it, they say it will execute faster as it's the easiest(quickest) part of the disk to read and write from.

---

### Post by al111 on 2011-09-06
Thanks!

---

### Post by 1clue on 2011-09-06
Why not just go without swap?

If you have 4G or so you'll never use it on any normal desktop.

---

### Post by al111 on 2011-09-08
I suppose I could go without a swap, but I decided to put one on my storage drive anyway-

Unfortunately, Linux does not see it-

How can I make it active so Linux knows where to find it?

I don't have a clue-

Thanks-

[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/Screenshot--dev-sda-GParted.jpg[/IMG]

[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/Screenshot--dev-sdb-GParted.jpg[/IMG]

---

### Post by oldfred on 2011-09-08
You need to add an entry into fstab.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

To see UUIDs

sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

This is my entry change to your UUID:
```

# swap was on /dev/sdc10 during installation
UUID=09367687-86d1-4fd0-9b81-2787d3196159 none            swap    sw              0       0

```Anytime you edit fstab you need to make sure is is ok. This remounts and if no errors you know it is ok. If errors you need to correct before rebooting or you may not be able to.

sudo mount -a

---

### Post by docbop on 2011-09-08
I'd say there is more to think about.

How much RAM do you have, is your system swapping a lot already?  How many app's do you tend to run at a time, that means more swapping going on.    The swap is your virtual RAM so speed is important, put your swap on SSD then you swap is almost as fast as your RAM.  A SSD is just big RAM Disk to use the old term for RAM configured to act as a drive.

---

### Post by YesWeCan on 2011-09-09
While you are at it, install Grub to the WD and not the SSD. Grub breaks the MBR system that Windows expects and will repair from time to time and can cause problems with some updates. Just like swap there is no need for the Grub MBR code to be on the same drive as Ubuntu.

Ive set up a system with Win7 & Ubuntu 11.04 on the SSD and Grub on the HD along with swap. Works perfectly. I later modified it so Grub was entirely inside the Ubuntu partition and complies with the MBR system, but that's another story.

---

