---
title: "Unallocated space is not visible during ubuntu 14.04 installation ?"
date: 2014-11-03
forum: Installation &amp; Upgrades
---

### Post by 22990atineshgmail on 2014-11-03
Hello, I've windows 8.1 installed on my PC and I'm trying to install ubuntu 14.04 along with windows (Dual Boot). For that I've un allocated 15gb of space from windows, But after doing that both "C drive" that I've shrinked and un allocated space are not visible during ubuntu installation. I've tried many times but it just doesn't show those partitions.

[[IMG]http://s8.postimg.org/sli8zpntt/image.jpg[/IMG]]("http://postimg.org/image/sli8zpntt/")

[[IMG]http://s30.postimg.org/hgy3prfe5/DSC_1447.jpg[/IMG]]("http://postimg.org/image/hgy3prfe5/")

---

### Post by Rrory on 2014-11-03
Here is a super helpful link with screenshots give it a try:
[http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)

---

### Post by mastablasta on 2014-11-03
do you maybe have MBR partition table? if so then there can't be more than 4 primary partitions. so you would need to change one of those into secondary (extended).

edit: nevermind... your problem is likely casued by dynamic partitions scheme

[http://msdn.microsoft.com/en-us/library/windows/desktop/aa363785(v=vs.85).aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa363785(v=vs.85).aspx)

---

