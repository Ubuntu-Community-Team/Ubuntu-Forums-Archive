---
title: "[SOLVED] Error while installing ubuntu 7.10"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by Mashashi on 2008-06-10
Hi!

I'am new in the Linux, world so today a I decided to install linux ubuntu 7.10 but unfortunately whene the kernel is loaded the following error (I Think) showed up:

```

udevd-event[2236]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in Shell (ash)
Enter 'help' for all list of built-in commands.

(initramfs)_

```

PC info.
```

Pentium 3 1 Ghz 
20 Gb (HDD)
256 Mb (Ram)
Windows XP (Previous SO)

```

I did a reserch but it was in vain :confused:, what can I do to fix this?
Thanks!

---

### Post by wpshooter on 2008-06-10
Are you attemting to install from the Live CD version or the ALTERNATE (text based) CD version ?

---

### Post by Mashashi on 2008-06-10
It is the live CD version, the weird thing is in my laptop the graphical interfaces loads with out any problem...

---

### Post by dstew on 2008-06-10
This is often caused by a problem with the driver that the Live CD uses to access the hard drive. There are a few ways to fix it. The simplest is to use the kernel parameter **all_generic_ide**. To use a kernel parameter, hit F6 at the opening menu. Type the kernel parameter at the end of the line, and hit return.

---

### Post by Mashashi on 2008-06-11
Well, it seem that worked, the pc started doing some kind of memory test, and has been doing it for 15 hours don't know if it is normal.

---

### Post by dstew on 2008-06-11
Perhaps you picked the memory test boot option somehow. Make sure when you go to F6 to put in the kernel parameter that you are doing a normal boot.

---

### Post by Mashashi on 2008-06-11
lolz, that is why I was having the problem of memorytest xD...
Then I could install ubuntu with out any problems.
Thanks man!

---

