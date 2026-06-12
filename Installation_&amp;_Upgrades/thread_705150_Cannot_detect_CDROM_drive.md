---
title: "Cannot detect CDROM drive"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by ComStar on 2008-02-23
Hi, i am trying to install Ubuntu 7.10. When i tried to use the LiveCD option, it goes into a console instead of going into gnome.

Then i tried the alternate install disk. It prompts that it is unable to detect my CDROM and is unable to mount it. Well, thats strange considering it booted from it.

I am using a 8800GTS and Benq IDE DVD-RW. My hdd is a SATA Hitachi.

Everything works fine in Windows VMware, but i just cannot get it to work natively.

---

### Post by dstew on 2008-02-23
Try passing the kernel parameter  **hdc=cdrom** (use F6 on Live CD starting menu), assuming that hdc is the correct drive designation. This is to tell the kernel that a hard drive it is detecting is really a cdrom. You have this problem with ide cdrom drives. See[ this]("http://www.mjmwired.net/kernel/Documentation/ide.txt"). You can also try hdc=noprobe along with hdc=cdrom

---

