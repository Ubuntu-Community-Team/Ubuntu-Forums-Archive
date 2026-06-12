---
title: "Ubuntu is hanging."
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by santhakumar on 2008-02-07
I am new to Linux and i installed ubuntu 7.04 version. it got installed successfully. But while using the OS, it is hanging after sometime. I tried 7.10 also it is also hanging.  i have formatted the drive as ext3. i gave 2 GB space for swap and 10 GB space for the primary drive. What may be the problem?

---

### Post by Partyboi2 on 2008-02-07
where is it hanging? eg when you are booting, loading the desktop etc

---

### Post by santhakumar on 2008-02-07
It is getting booted properly. Sometimes it is hanging as soon as i boot. sometimes it is hanging in  ten mintues. I am able to work for one hour sometimes before hanging.

---

### Post by daengbo on 2008-02-07
This sounds suspiciously like a hardware problem, though it could be a proprietary driver, I guess. You should reboot and use the grub bootloader to run the memtest program. If that goes OK, look at your video card and CPU fan to make sure they aren't overheating.

Finally, if that doesn't work, try disabling any proprietary drivers (like the NVidia driver) and see if the problem persists.

---

### Post by santhakumar on 2008-02-07
How long will that memtest program will take? it Already ran for two and half hours. what is the use of that?

---

