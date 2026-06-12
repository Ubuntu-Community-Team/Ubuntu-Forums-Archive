---
title: "possible run ubuntu off external drive"
date: 2012-08-06
forum: Installation &amp; Upgrades
---

### Post by waterhouse on 2012-08-06
My  laptop computer running ubuntu 11.10 recently crashed and won't boot and I believe the problem is a faulty internal hard drive. I have an unused western digital 1T external hard drive. I was wondering  since my internal HD is useless if there is a way to use this external HD as the laptops HD such that it boots from it and uses it as HD.

---

### Post by oldfred on 2012-08-07
Sure. Install to any second drive, SSD, flash is similar to any install. But you need to use manual install to get the option to choose which drive's MBR to install the grub2 boot loader.

Some use external hard drives, or even flash drives. But USB port is not as fast as a SATA port, but it works even from flash drives that are very slow with writes if you minimize writes and have a fair amount of RAM. Linux loads apps in RAM but does not remove them until it needs the space for something else, so reusing recent apps will still be speedy.

Installer has not changed significantly.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)

I think Herman recently converted to the alternative installer, which is not normally required. Screens then are a bit different, but process is the same.
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Installs to 4GB flash, newer of Ubuntu versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

---

