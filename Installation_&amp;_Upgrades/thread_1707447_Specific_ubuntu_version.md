---
title: "Specific ubuntu version"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by djmondo on 2011-03-15
i am trying to find a download of ubuntu 10.4.1,  but i am trying to find a specific download or installation where the kernel is not higher than 2.6.32-25.  Is that possible if so, where do i go to download it.  Please any help would be greatly appreciated.

---

### Post by sedawk on 2011-03-15
Have you tried the LiveCD (or USB stick) for 10.4?

It should be the oldest version of 10.4 you can get.

If you disconnect (or do not allow?) internet connection
during installation the system will not be upgraded
to the latest kernel.

You can also try to browse the debian-style directory
structure of Ubuntu on the http/ftp server so see which
kernels are (still) available for download
(?somewhere in main/pool/... or similar?)

---

### Post by Frogs Hair on 2011-03-15
One option is to install that Kernel and from System > Administration > Synaptic Package Manager > Package tab lock that version .

---

### Post by djmondo on 2011-03-15
i am very new to ubuntu.  i really never played with this OS.  How would one go about rolling back the kernel version??

---

### Post by Frogs Hair on 2011-03-16
By looking at the kernel number I'm guessing your using 10.04 . look in system> administration > synaptic package manager and locate the Linux generic headers and kernel and install them and when you reboot choose that kernel from the grub menu . Not having downloaded 10.04 since it came out  I'm not sure which kernel it currently comes with.

---

