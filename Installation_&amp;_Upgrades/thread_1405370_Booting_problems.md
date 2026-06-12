---
title: "Booting problems"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by guitarhero183 on 2010-02-12
I have install Ubuntu Server 9.1 onto an external hard drive and the installation goes fine but when I reboot the computer grub has and error and says unreadable file system or something similar to that. I am able to boot from that hard drive though from another computer and everything is fine. The computer I am trying to install Ubuntu on is a computer I made. The motherboard is an ASUS ITX-220. Right now there is no internal hard drive in the computer though so I am thinking that installing Ubuntu onto an internal hard drive in the computer would fix the problem.

---

### Post by dabl on 2010-02-12
> **guitarhero183 said:**
> 
 I am thinking that installing Ubuntu onto an internal hard drive in the computer would fix the problem.

Probably so.  Installing on external USB hard drives is a little problematical because USB devices don't always get numbered the same (look at all the posts on this forum on the same topic).

Check your BIOS for the boot device sequence, and that "boot from USB" is enabled.

---

### Post by guitarhero183 on 2010-02-12
I have enabled "Boot from USB device". I guess I'll just get an internal hard drive.

---

