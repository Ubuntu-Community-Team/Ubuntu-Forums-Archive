---
title: "Possible to run from a flash drive?"
date: 2012-10-16
forum: Installation &amp; Upgrades
---

### Post by dankki on 2012-10-16
Hey.

Is it possible to run Ubuntu on a flash drive? I got a 32gig flash drive, no hdd. Would it be possible to install Ubuntu on the flash drive and run it off it? It would be used only for web surfing :D

If yes: how?

---

### Post by cortman on 2012-10-16
Sure, it's possible. See [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") or [here]("http://askubuntu.com/questions/170454/can-i-install-ubuntu-to-my-32-gb-usb-pen-drive") or [here]("http://shallowsky.com/blog/2011/Oct/28/").

---

### Post by oldfred on 2012-10-16
With a large flash drive you can just do a regular install like to any external hard drive. You do make some settings changes to reduce writes as flash is somewhat slower as is USB when compared to SATA.

I have a 16GB Flash with a 8GB partition for / and 8GB for data. It is functional and once an app loads into RAM it is no different. 

Because you have a large Flash drive I would not suggest persistent install but you can do that also.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Persistent installs:
With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Full install is just like any other install to a second drive.

Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

But you want some changes to reduce writes like you would for a SSD.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

---

