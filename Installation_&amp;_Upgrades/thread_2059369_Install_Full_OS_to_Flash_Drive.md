---
title: "Install Full OS to Flash Drive?"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by rosser725 on 2012-09-17
I am trying to bring my old laptop back to life, and it doesn't currently have a hard drive. I know a friend of mine, installed Ubuntu to a flash drive. How do I do that?
I don't mean a live USB, I mean install the OS to the flash drive using a live cd, and then booting from the USB drive everytime.

---

### Post by snowpine on 2012-09-17
Exactly the same procedure as installing to a regular hard drive, as detailed here: [http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)

The installer does not distinguish whether the target drive is inside or outside of the computer case. Unfortunately, however, running from a flash drive tends to be a little slower than from an internal HDD, therefore you might want to consider this a temporary solution. :)

---

### Post by Dennis N on 2012-09-17
You would get much better performance by installing to an USB external hard drive rather than a flash drive if you can do that - not too much different from the internal drive.

---

### Post by oldfred on 2012-09-18
Flash drives are real slow on writes, so you do want to make some changes to minimize writes. If you have a fair amount of RAM system can be pretty good. I have a full install of Ubuntu in a 8GB partition with another 8GB for data on my 16GB flash drive.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Settings similar to SSD:
With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

---

