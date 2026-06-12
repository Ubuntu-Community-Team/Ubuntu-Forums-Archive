---
title: "Install fails to detect CDROM"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by baboulebou on 2008-09-10
Hi there gurus,

I'm trying to install **Ubuntu 8.04.1 - Server** on an oldish i386 PC, using a CD I burned from the ISO image I downloaded from Ubuntu (with MD5 check saying it's fine).

The first thing the install does is apparently check for the CDROM drive, which it can't find. I use an **LG CD-RW 52x24x52x** drive, which isn't all that old, but the install asks for drivers, which I can't locate...

So what can I do? Any ideas where I can find the right driver from? Is this a known issue?

Note that I was able to get a command line (in full screen), and the 'ls /dev' listed all kinds of devices, even one called "cdrom".

I thought this was supposed to be easy, I'd hate to have to go back to XP :(...

Thanks in advance for any help,

./\.

---

### Post by manishtech on 2008-09-10
> Note that I was able to get a command line (in full screen), and the 'ls /dev' listed all kinds of devices, even one called "cdrom".
Then try searching for a device file names **scd0** . This is the name on my computer. Hope its same on your computer also.

```
ls /dev/scd0
```

---

