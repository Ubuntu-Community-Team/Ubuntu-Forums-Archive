---
title: "Can I install Ubuntu with a portable hard drive?"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by No0bzZ on 2011-10-13
Hello.... Can I install Ubuntu with a portable hard drive?

The portable hard drive has files and videos stored inside it which I can't delete or transfer because it's too big and it's important. I'm wondering if there's a way for me to install Ubuntu with that occupied portable hard drive. The portable hard drive still has a lot of free GBs.

Help!

I almost forgot.... 

I'm going to install Ubuntu on my cousin's PC... They deleted their SYSTEM folder... because someone's post on facebook said so. I know... it's frustrating.

Their previous OS is Windows XP... and their computer is really old...

Anyone??? Help??!!!!

---

### Post by lordfirex on 2011-10-13
Yes it is possible to both run a portable drive as both an Installation Disc (LiveCD) or you can alternatively install Ubuntu onto the portable drive as to have a full Ubuntu installation running off your portable drive.

For your current drive i would recommend doing the following (assuming you want to creating like an installation LiveCD)

1. Back-up your data - no seriously do this, even if it's only temporarily because your going to need to store it somewhere else for the time being

2. Partition your Portable; preferable into two; one for you Files and information and the other partition is where the Live CD is going to be (Not sure if you have to but i've always put the LiveCD image on the first partition, files on the 2nd)


3. Using Unetbootin or similar, put the .iso file of the ubuntu installation onto that partition

You can now use your portable as a ubuntu installation cd!!!!

4. Move your files back to the portable drive and heyh presto!

---

### Post by No0bzZ on 2011-10-13
> **lordfirex said:**
> Yes it is possible to both run a portable drive as both an Installation Disc (LiveCD) or you can alternatively install Ubuntu onto the portable drive as to have a full Ubuntu installation running off your portable drive.

For your current drive i would recommend doing the following (assuming you want to creating like an installation LiveCD)

1. Back-up your data - no seriously do this, even if it's only temporarily because your going to need to store it somewhere else for the time being

2. Partition your Portable; preferable into two; one for you Files and information and the other partition is where the Live CD is going to be (Not sure if you have to but i've always put the LiveCD image on the first partition, files on the 2nd)


3. Using Unetbootin or similar, put the .iso file of the ubuntu installation onto that partition

You can now use your portable as a ubuntu installation cd!!!!

4. Move your files back to the portable drive and heyh presto!

I can't back up my portable hard drive because it is way too big.... Is there another way?

---

### Post by phly95 on 2012-01-30
Upload to 4shared (multiple accounts if many files), install the OS, and download the files again (and delete them frome 4shared if neccessary) if you want a more private solution, get a paid box.com account with 50 GB (or more) and upload, install, and download

OR get tech support to fix your computer for you, it costs money but will ensure all files are safe (or you can sue tech support)

---

### Post by james2b on 2012-01-30
You can use the GParted partition tool to boot to and carefully do the Ubuntu partition preparation, (I use about 15- 20 GB for root and 1-2 GB for a swap file). Your drive can have 3 primary and then an extended area for logical volumes. Or create 4 primary partitions. Here is the site to download and burn a image of the iso file to CD; [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php) Then during the Ubuntu install process you must select the option for custom or something else for partitioning to then pick your just created 15-20 GB partitions then mount as /, (root) and format the EXT4 file system, and select your swap. If your external drive is connected by USB, expect it to be fairly slow.

---

