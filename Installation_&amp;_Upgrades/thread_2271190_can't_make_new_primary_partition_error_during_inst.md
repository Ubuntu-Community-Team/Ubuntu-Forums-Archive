---
title: "can't make new primary partition error during installation"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by ashok_saini on 2015-03-28
hii,
i am new to ubuntu and trying to install --  ubuntu-14.10-desktop-amd64 ..
on this laptop  [http://goo.gl/czmMR2](http://goo.gl/czmMR2)  a lenovo laptop with toshiba HDD.

during installation it gives an error  saying that it is not possibe any more primary partition .

currenty running win8.1 pro

wants to dual boot win8 and ubuntu  

[IMG]http://i58.tinypic.com/2vcuzpc.jpg[/IMG]

what should i do .
the laptop came with freeDOS free loaded and i installed win8.1

---

### Post by dino99 on 2015-03-28
maybe you already have the maximum possible 4 primary partitions set.
in such a case the solution is to boot with usb/cd iso and then modify actual partitions (shrink) to get some free space to set an 'extended' partition where you then can install as many partitions as you want (note that formatting need to be done on non mounted partitions, so the booting with usb/cd)

[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by Bucky Ball on 2015-03-28
Well, there are only three partitions, so that is not the problem ... directly. If you are going for 'Install alongside Windows' install, that could be the problem as Ubuntu will want to create at least two partitions, and you already have three. Then you have the problem of trying to create five partitions. The limit is four.

I suggest you either make a plan and see if you can shrink some of your  existing partitions to make room for more unallocated space at the rest of the drive in which to install Ubuntu, or, if you're happy with installing to a 29Gb space and linking to existing personal files on existing partitions (I do this kind of setup myself), then:

... boot from the install media>'Try Ubuntu'>Launch Gparted and create an extended partition with the 29Gb of unallocated space>boot the install media>choose 'Something Else' when it comes to the partitioning section of the install>create a 27Gb partition for Ubuntu (with the mountpoint /) and a 2Gb /swap partition at the end of the drive, both inside the extended partition.

See if that works. The mountpoints / and /swap are available as defaults when creating the partitions using 'Something Else'.

---

