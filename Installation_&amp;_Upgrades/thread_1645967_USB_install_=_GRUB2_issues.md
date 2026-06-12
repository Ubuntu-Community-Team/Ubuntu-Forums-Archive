---
title: "USB install = GRUB2 issues"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by samandiriel on 2010-12-15
I apologize if my problem is well-documented already, but there is signal-to-noise ratio is too high for me to be able to ferret it out :(

I am installing Ubuntu 10.04 server on a box with no optical drive, using a USB pen drive created using Ubuntu's Startup Disk Creator.  Installation works just fine.

However, instead of installing the MBR/grub2 on the hard drive it is installing it on the usb pen drive - ie, I can't boot without the pen drive being the bootable device.

I tried 'grub-install &#8211;root-directory=/boot /dev/sdb', but that didn't work.
I then tried 'apt-get purge grub-common' and then 'apt-get install grub-common' and THAT blew it out of the water.  There is a known bug where it tells you that there is no bootloader installed and do you want to continue without one Y/N - N just sends you straight back to the same dialog instead of installing.

I'm not interested in recovering as it's a brand new install - easier just to redo it correctly from the start.  So the question is this: how can I install from a USB pen drive and have the bootloader install properly???

Thanks for any advice!

Tyler

---

### Post by apemax on 2010-12-15
yeah i had this problem too. what i did was i used grub4dos to map the Ubuntu minimal cd image to ram then booted from it there. then i just took my usb stick out once the cd's boot menu had loaded. if you need any more info on the way i did it just ask. :)

---

### Post by oldfred on 2010-12-15
If you do partitions in advance, or reuse the ones you have. Then do manual install. Now only with manual install does it give the combo box on where to install grub.

Grub usually defaults to installing to sda. But some USB drives also default to sda when mounted and then you may not get grub installed to the hard drive. You just need to review which drive is the internal drive with the combo box as part of the install.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

If you can boot into your system the grub install command that you did should work. But was hard drive then sda or sdb?

---

### Post by samandiriel on 2010-12-15
> **oldfred said:**
> If you do partitions in advance, or reuse the ones you have. Then do manual install. Now only with manual install does it give the combo box on where to install grub.

Grub usually defaults to installing to sda. But some USB drives also default to sda when mounted and then you may not get grub installed to the hard drive. You just need to review which drive is the internal drive with the combo box as part of the install.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

If you can boot into your system the grub install command that you did should work. But was hard drive then sda or sdb?

Thanks for the advice, although I think it was for 10.10 not 10.04.  It gave me enough hints to get it though.  I had to say no to installing the GRUB boot loader, and then it put me into a dialog box where I could enter the device manually (in this case, /dev/sdb)

Thanks!

---

