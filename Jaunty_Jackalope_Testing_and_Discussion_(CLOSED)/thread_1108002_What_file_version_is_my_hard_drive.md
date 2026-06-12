---
title: "What file version is my hard drive?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Daniel_B on 2009-03-27
This morning I updated to the lastest beta of Jaunty 9.10 and followed the commands to upgrade my hard drive to ext4. All went fairly smoothly and things seem to be faster. However, when I use the System Monitor application and view filesystems, my hard drive is still listed as ext3. When I look at my hard drive using Partition Editor (gparted), it is listed as ext4. How do I find out which it is? Is this just the System Monitor program needing to be updated?

Thanks,
 Daniel

---

### Post by macogw on 2009-03-27
Yes, probably that program needs to be informed of ext4's existence. Can you file a bug?

---

### Post by cl333r on 2009-03-27
"Jaunty 9.10" you probably mean 9.04

---

### Post by wjp.reg on 2009-03-29
I was curious about the comments about system monitor in Jaunty 9.04 which I upgraded this AM.  System Monitor reports all my filesystems correctly; I set up separate partitions for /boot (ext3), / (ext4), and /home (ext4).

cheers

---

