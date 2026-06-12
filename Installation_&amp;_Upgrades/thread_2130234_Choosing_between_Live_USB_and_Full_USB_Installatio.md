---
title: "Choosing between Live USB and Full USB Installation"
date: 2013-03-28
forum: Installation &amp; Upgrades
---

### Post by alexrdavies on 2013-03-28
I want to run Linux from a USB stick without affecting the data on the computer.

I need persistence, but I can achieve that through either a Live USB stick, or a full USB installation.

Other than that, my top priority is speed. I believe that with the Live USB stick, all of Linux is loaded into RAM and so it runs quite quickly. I am not sure whether this also applies (or can easily be made to apply) to a full installation.

Having more space and being able to upgrade would also be nice, but are not as important to me as running quickly.

---------

Given the above terms, would it be better for me to use a Live USB or to install Ubuntu fully (possibly with some custom settings to force it to load into RAM)?

---

### Post by JLeon85 on 2013-03-28
A live USB of Ubuntu doesn't load into RAM without a lot of work. You would be best using Knoppix or Puppy Linux to do that. As for speed, I didn't notice any improvement when I installed onto the USB. Also, the full install created problems with installing new software which I didn't have with a persistent USB. I think what you want is a fast USB drive, and if possible a USB 3.0 port.

---

### Post by fantab on 2013-03-28
Running LiveUSB/DVD is slow compared to proper install. USB will be faster than the DVD. The speed of the USB will matter. Installing Ubuntu on USB (atleast 8gb- recommended 16GB) will be faster compared to LiveUSB with persistence. But it won't be as fast as ubuntu installed on a HDD. I haven't tried it with USB 3.0, it may be better than USB2.0.

---

### Post by oldfred on 2013-03-28
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)
 Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

    
Lighter weight gui may load a bit quicker.
       HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

You do want to turn off journaling, reduce writes, and maybe change scheduler. Linux normally caches your activity into RAM, so the more RAM you have the quicker it will seem.

Flash does not support trim, so that does not apply.

 With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler

---

### Post by C.S.Cameron on 2013-04-01
I recently tested a number of types of USB flash drive installs, for speed, using 12.04:
Full install, no swap.
Full install, swap.
Full install, separate ext2 home partition.
Full install, swap, separate ext2 home partition.
Full install, swap, separate ext2 home partition, FAT32 partition.
Persistent, casper-rw file.
Persistent, casper-rw partition.
Persistent, casper-rw + home-rw partition.
Persistent, casper-rw + home-rw partitions with Try/Install screen removed.
Iso boot, Persistent, casper-rw + home-rw partitions with Try/Install screen removed.

I tried again after removing journaling and adding noatime on the Full installs.

Bootchart, Full install vs Persistent, 22 seconds vs 145 seconds, persistent with try/install removed, 114s.
Hardinfo, All install types had similar scores.
All shutdown times similar.
I did not notice a difference in speed in the little time I played with each.

I did not try tuning to the extent Herman has:
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

### Post by alexrdavies on 2013-04-02
It seems most people (here and elsewhere) have found that a full install can be just as quick as a Live USB image. As it also confers other advantages, like being able to fully update, I chose a full install.

To begin with, when I installed to a USB stick from a (different) Live USB stick, my new system wouldn't boot. It said that /dev/disk/by-uuid... does not exist. Somebody suggested that the problem was installing from USB to USB... they were correct and re-installing from a Live *CD* gave me a working system.

The advice given above was very helpful in getting me started on Ubuntu - thank you. The link given by C.S.Cameron was also useful for deciding how to tune, now that everything is up and running.

---

