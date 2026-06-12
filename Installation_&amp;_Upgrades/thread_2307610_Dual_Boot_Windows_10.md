---
title: "Dual Boot Windows 10"
date: 2015-12-26
forum: Installation &amp; Upgrades
---

### Post by misswham2 on 2015-12-26
Happy Holidays.  I just bought a new pc and it has windows 10.  I want to dual boot with ubuntu but I have never installed with windows 10 before.  I have seen youtube videos on the installation but they are going thru to windows first and making a partition there and then doing the installation but my question is, can I bypass that step and just resize the partition directly with the distro installation cd while I install or do I have to go and do the windows part first?

---

### Post by yancek on 2015-12-26
You don't need to make a partition in windows but it is best to resize (shrink) the windows partition from the windows Disk Management tool.  After doing that, reboot windows and run chkdsk and then begin the install.  Kind of pointless to create a partition for Ubuntu in windows since windows doesn't recognize/understand Linux filesystems.  I would suggest you read the page below before beginning, understand whether you have the default UEFI with windows.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

