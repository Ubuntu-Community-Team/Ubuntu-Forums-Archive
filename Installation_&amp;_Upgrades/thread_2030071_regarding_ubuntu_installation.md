---
title: "regarding ubuntu installation"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by divine cutler on 2012-07-20
can a linux operating system say ubuntu 12.04 be installed in a 32gb usb stick and use it, same as installing it in computer system's builtin harddisk...is it possible?if not kindly explain why??
thank you..

---

### Post by mikewhatever on 2012-07-20
Yes, it's possible. The only difference is, you'll have to select "Something else" at the partitioning stage, setup partitions manually, and also select where to install the bootloader (the MBR of the USB drive). It's a bit more advanced because of that, but by still no rocket science.

...another thing to consider, USB sticks are not as reliable as regular hdd.

---

### Post by OM55 on 2012-07-20
+1, it is definitely possible. The best example would be the Ubuntu Live installer - it is an Ubuntu on the USB...
In addition to the requirements mentioned in the previous post (by divine cutler) I would also add that a USB key is considerably slower than a regular hard disk. So unless you have a good reason to have Ubuntu on a USB key, you will have a very very slow working system.
An alternative would be using a regular external USB disk, that would work fast and still be mobile, so you can use it in every computer you want (just remember to change the BIOS settings on any new computer so it will boot from the USB disk = USB HDD).

---

### Post by oldfred on 2012-07-21
If you have a fair amount of RAM, once programs load it still is reasonably fast. Writing is what is very slow, but you can change some settings to reduce system writes.

I have a full install of 64 bit Ubuntu in a 8GB partition on my 16GB flash (other 8GB is just data). I just use it for testing as I do not have a lot of room for another system partition on my laptop. It runs ok on both laptop & desktop. A little slow loading larger apps but functional. One of the lightweight installs like Lubuntu may be better.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

You do want to use manual install for any install to an external device, so you get the option to install the grub2 boot loader to the MBR of the external. Otherwise it defaults to sda which usually is the internal drive.

For me install to external USB flash was no different than any install to a second drive.
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

