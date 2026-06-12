---
title: "Install Ubuntu ON a flashdrive?"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by rommieuserxero on 2012-06-05
I was thinking, when I put in my Ubuntu cd, and boot off it, and go into the "Something else" section in the install window, my flash-drive is there when plugged in. I noticed it had one partition. I thought hey, what if I, in that window set the "Device for boot loader installation" to my flash drive ("/dev/sdf"), delete the partition on the flash-drive and make a root ("/") and a home partition and install...

I mean will it work? Well, will what work is probably your question. I mean if I tell it to boot off of the flash-drive, will it act like any normal hard-drive?

I should note here that the flash-drive I had in mind of using is 16GB, so no worry about space.


The reason I haven't tried this is because this requires deleting the partition on the flash-drive, and I'm not sure if it will be usable later when I make a basic data partition on it. And I'm not sure if it will mess something up.

Just a thought
Rommie.


P.s. I know I can use a Linux-live CD or USB, I'm just wondering if this works.

---

### Post by Bucky Ball on 2012-06-05
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by oldfred on 2012-06-05
Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

I have a full install of 12.04 on a 16GB flash drive. I used 8GB for the install and 8GB just for data. It is more for testing and possible emergency boot. USB ports are slower than hard drives, flash is slow writing. My install is functional but not speedy. If you want one to use a lot, a lighter weight version like Lubuntu may be better.

Install to flash is just like any install to a second drive where you need to use manual install to get the choice to install the grub2 boot loader to the MBR of the flash drive, otherwise it just defaults to sda. You do want to make some changes to settings to reduce writes which helps make it less slow.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Installs to 4GB flash, newer of Ubuntu versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Install to external drive 11.04. Also any second drive. Standard LIveCD install.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by gordintoronto on 2012-06-05
I like to install to a flash drive when I'm testing a new distro/version. I recognize that it will run much more slowly, just because it's a flash drive. Perhaps this will be a lot better with USB 3.0.

Note that if you have multiple computers, you will probably not be able to move among them if they have different video adapters, such as Nvidia vs AMD. Even different wireless adapters might result in being unable to get online.

You can do much more thorough testing with a real install rather than a persistent USB.

---

