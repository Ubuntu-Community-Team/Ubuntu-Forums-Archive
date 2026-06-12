---
title: "UEFI windows logon - Legacy Ubuntu logon"
date: 2017-07-10
forum: Installation &amp; Upgrades
---

### Post by mlempenau on 2017-07-10
Just bought a new Dell Inspiron 5567 with windows 10 loaded.  After a couple days of burnin I turned off secure boot, selected Legacy boot list and enabled legacy option ROMs.  Then I installed Ubuntu 16.4.2 using a DVD.  I made four partitions, one for root, one for home, one for swap and one for boot loader.  Everything went ok and I exited the install program.  Now when I set bios to Legacy I get Ubuntu with no grub and when I set bios to UEFI I get Windows 10.  It's consistent, done it several times.  Should I leave it like that and not take a chance on messing it up or should I try to get grub to work?  Altho I have used Ubuntu for many years I'm still not a very astute user.  Thanks for your help.

---

### Post by slickymaster on 2017-07-10
*Thread moved to **Installation & Upgrades**.*

---

### Post by yancek on 2017-07-10
Based on the information you posted, it is working exactly the way it was designed.  If you want both windows/Ubuntu showing on the Grub boot menu, then you would have needed to install Ubuntu UEFI.  The link below is to the official Ubuntu documentation on dual booting windows/Ubuntu UEFI.  Read it and decide if you want to change.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

