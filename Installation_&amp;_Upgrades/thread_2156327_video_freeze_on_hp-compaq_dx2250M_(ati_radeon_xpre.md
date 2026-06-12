---
title: "video freeze on hp-compaq dx2250M (ati radeon xpress 200 video)"
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2013-06-21
After clean install of 12.04 64-bit, video keeps locking up.  Will lock up with mouse movement (especially vertical), and sometimes just on its own.  Have separete HDD with Win XP Pro SP3 and that works fine.   Output of lspci -nn | grep VGA is 01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS482 [Radeon Xpress 200] [1002:5974].  I have not done anything to video drivers that Ubuntu installed.  Monitor is Dell 2410 (1900 x 1200) operating in portrait mode).

Would like tohear from anyone who has 12.04 64-bits installed on hp-compaq dx2250M.

Thank you,

John

---

### Post by gordintoronto on 2013-06-21
The dx2250m appears to be a family of computers. Could you please tell us more about the computer? (CPU, RAM, hard drive partitions.) Is the RS482 an add-on card? (If you look at where the VGA cable is plugged in, you can tell.)

Is there some reason you described it as "video locks up" rather than "system locks up"?

---

### Post by cigtoxdoc on 2013-06-22
video freeze on hp-compaq dx2250M (ati radeon xpress 200 video) 

Thank you for your reply.  Video freezes is more appropriate as mouse is still active and you can see the HDD drive indicator go on and off in manner that would appear to show some background tasks still active.  Indeed, a download continued for a while before stopping.

The output from System Profiler and Benchmark is attached.  The output from the last boot-repair is also attached.  Another problem is that sometimes trhe next screen after the GRUB menu will be a TTY login instean of the Ubuntu login.  Whether or not you get one or another seems to be radom event.

John

---

### Post by cigtoxdoc on 2013-06-24
This problem is solved.  The recommended BIOS settings caused the problems with Ubuntu.  When I corrected the BIOS settings, Ubuntu worked correctly and Win XP Pro worked correctly.

John

---

### Post by yurivict on 2013-07-08
In this thread you said you solved the problem by "correcting the BIOS settings", but you didn't say which one.
I have a different laptop, Toshiba L305D-S5895, with similar Radeon, and it also freezes.

Radeon Xpress 1200/1250/1270 (ATI RS690M)

Could you please tell what BIOS setting caused the issue?

---

### Post by cigtoxdoc on 2013-07-08
Advanced chipset function part of BIOS had selections for initial video of on-board VGA, PCI, and PCIExpress.  Win XP worked on the default of PCIExpress, but Ubuntu 12.04 wanted to see on-board VGA.

John

---

### Post by yurivict on 2013-07-08
Thank you for this information.
Mine doesn't have such BIOS option.

---

