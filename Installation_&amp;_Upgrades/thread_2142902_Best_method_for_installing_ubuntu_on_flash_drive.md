---
title: "Best method for installing ubuntu on flash drive?"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by JoinTheRealms on 2013-05-07
Hey guys, its my first post here, i hope its in the right place.

I've recently built a pc out of my spare parts, quickly realized that i didn't have a spare hdd lying round. I'm building this pc as a media pc for streaming etc, and i'm aiming to install ubuntu on a 8gb flash drive (not a live cd) that boots the whole system into ram, has a few gb of persistent storage and be able to permanently mount shares on a smb network

My system:

Amd Phenom ii x6
8gb ram
on board graphics (nforce)
no optical drive
no hdd

i tried installing directly on to a flash drive but the performance was awful (many freezes) because i couldn't get boot to ram to work (necessary packages would install, maybe no compatible with 13.04?), i tried a live usb with "toram" parameter but persistent storage would not work, plus im really looking for a full install so i can change window managers etc.

Ive used other distros like knoppix(really good performance but lacking the necessary software) but im really wanting an ubuntu based distro.

I feel like there should be an easy way to go about this but ive yet to find it.

Any help is much appreciated!

---

### Post by TenPlus1 on 2013-05-07
Try Bodhi Linux 2.3.0 and installing that to your USB flash drive, for best results I'd recommend using an SDHC card reader with the fastest card you can buy which will increase performance on the installed system...

Also, make sure you do NOT have a swap partition and add the following line to the /etc/sysctl.conf file:

vm.swappiness = 0

For further tweaks you could also add the 'noatime' flag to your partitions inside the /etc/fstab file and add these lines to the end of the same file to use your memory as a tmp folder instead of the usb flash:

tmpfs /tmp         tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log     tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp     tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log/apt tmpfs defaults,noatime,mode=1777 0 0

---

### Post by oldfred on 2013-05-08
Did you change some settings to reduce writes and improve performance on flash drive. I have full install in a 8GB partition on my 16GB flash drive and it runs well. Not particularly fast but once program is loaded into RAM then it is just as fast as any system.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)


 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)

      
 With SSD or Flash (trim do not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler
But per this noop may not now be best.
[http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1)
noop may not be best scheduler for SSD, deadline may be better
[http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance](http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance)

I only have USB2 ports but recently bought my first USB3 flash drive from Microcenter (their housebrand). It is about 10% faster even with just USB2 port.

---

### Post by JoinTheRealms on 2013-05-09
A big thanks for the helps guys, i ended up buying a cheap hdd for the pc, but im using what you guys said to have a portable distro that i can carry around :cool:

---

