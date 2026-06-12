---
title: "How to install Ubuntu on a 32GB usb drive"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by emuba on 2012-01-17
Hi,

I want to install ubuntu 11.10 amd64 on a 32GB usb drive. I have tried Universal USB Installer from windows but it only allows me to create a persistent file of 4GB maximum.

What other ways are there? Can I just run the usual ubuntu installation from a live cd?

thanks,
eumba

---

### Post by WasMeHere on 2012-01-17
Hi emuba,

I think the limitation for the casper-rw file to 4GB is because the FAT32 file system is used, and it cannot handle bigger files. I have not tried, but I think it is worth testing to use ext2 or ext3 file system instead on the USB drive, and to make the casper-rw file manually.

See also this description by *sudodus*
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

Have fun finding out :-)
Olle

*Edit: A problem with standard install is the frequent read/writes that will wear out a (standard pen) flash drive. This is not a problem with a USB hard disk drive or SSD drive.*

---

### Post by oldfred on 2012-01-17
Since your Flash drive is so large, you should just do a full install.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

I did a full install of Ubuntu following these instructions. I have a 16GB flash and used 8GB for the install and 8GB for data. But some have posted that Lubuntu may be better since flash drives are slower.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler


Full install of 11.04 to USB device C.S.Cameron post
[http://ubuntuforums.org/showthread.php?t=1824194](http://ubuntuforums.org/showthread.php?t=1824194)
Full install of 11.10 to USB device C.S.Cameron post
[http://ubuntuforums.org/showthread.php?t=1908107](http://ubuntuforums.org/showthread.php?t=1908107)

---

### Post by snowpine on 2012-01-17
Journaling is a good thing, it will help prevent data loss if your battery runs down or the power is interrupted. I do not recommend ext2 for this reason. I tried ext2 once and it was a failed experiment (forced to fsck after battery run-down). :(

---

### Post by oldfred on 2012-01-17
I also agree with snowpine. 

But with a USB flash writes are slow, and there may be limited life with too many writes. And on a smaller partition on a flash drive fsck still can run fairly quickly. It becomes a trade-off of speed & life versus reliability. For my hard drives I always go for reliability, but I look at my flash drive as an emergency boot or as I am using it now as a test of 12.04 (which then are lots of writes with so many updates:)). 

If using as your main system you then may want to leave journaling on.

---

### Post by emuba on 2012-01-17
Thanks people for all the interesting information. Actually I will try using a full install on the drive. I keep you posted.

---

