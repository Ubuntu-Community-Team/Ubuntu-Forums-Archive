---
title: "Can I install Lubuntu and Ubuntu onto 1 USB?"
date: 2012-04-08
forum: Installation &amp; Upgrades
---

### Post by twtduck.ii on 2012-04-08
I have a 16GB usb and I want to have both Lubuntu and Ubuntu installed on it (so I can run them from any computer, able to access the files on the USB). Is this possible? If so, how do I do it?
Thanks,
Twtduck
PS Is this possible with the 12.04 beta?

---

### Post by fresnofred on 2012-04-08
I would probably install one system, then boot to the thumb drive and install the other system just like u would with a windows/ubuntu dual boot system.  BUT, i always physically disconnect my hard drive to avoid "grub hell" that can make your system unbootable.  after installation of both on thumb drive, then u can reconnect your hard drive.

---

### Post by oldfred on 2012-04-09
Do you want full install or liveCD/ISO. I have a full install of 12.04 in 8GB on my 16GB flash drive so I can test with my laptop which I did not want to add a partition to. It works from my desktop just as well. I also have several smaller flash drives with just the ISOs which I loop mount with grub2.

Full install to flash is just like any install to a second drive. You have to use manual install or Something Else to have the choice on where to install the grub2 boot loader. You also have to decide which install you want to have in the MBR and install it last or plan on reinstalling from the first install (relatively easy).

You should change some settings to reduce writes, it is functional if not speedy. Install and anything with writes is slower, loading larger programs is slower, but if you have a fair amount of RAM it works well.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

---

