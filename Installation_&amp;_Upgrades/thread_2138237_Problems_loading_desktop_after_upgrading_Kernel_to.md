---
title: "Problems loading desktop after upgrading Kernel to 3.8.8"
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by alcyonne on 2013-04-23
Hi all,
I installed ubuntu 12.10, and due to a driver problem, I got an advice to upgrade my kernel. As I found in internet, the latest stable version was 3.8.8, so I upgraded my kernel to that version

```
morpheus@ubuntu:/$ uname -a
Linux ubuntu 3.8.8-030808-generic #201304170248 SMP Wed Apr 17 06:58:01 UTC 2013 i686 i686 i686 GNU/Linux

```

The problem is, when I rebooted the system, I got a black screen with only [Ok] in the screen. I switched to a tty, logged myself and launched a **startx** command. My colors were displayed, but the problem is that I think that the desktop thinks my monitor too big for 1280x800....The result is no status bar, no launcher, except the wallpaper....

Any help is appreciated.

Thank you

---

### Post by dino99 on 2013-04-23
how have you installed 3.8.8 ?
you need to download inside an empty folder:
- 2 headers
- 2 images
( dkms, built-essential previously installed )

and then run: sudo dpkg -i *

pay attention to the graphic driver output while installing the kernel

---

### Post by alcyonne on 2013-04-23
Thank you..
That's exactly what I did.....
But i didn't pay attention to the graphic driver output
So I'm getting headaches to solve this

---

