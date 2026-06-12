---
title: "Ubuntu server installer can't mount CD-ROM drive!"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by stweston on 2008-09-22
I'm having trouble mounting my CD-ROM drive in Ubuntu Server. It's a CSA CDR-1300A drive, works just fine in Windows 98, but when loading Ubuntu Server, it always fails to mount. The CD can be read just fine, but the Linux kernel apparently doesn't detect it.

---

### Post by cariboo on 2008-09-22
You could try:

```
ls -l /dev/cdrom
```

to see if it is linked to a device. In my case I get:

```
ls -l /dev/cdrom
lrwxrwxrwx 1 root root 4 2008-09-22 14:23 /dev/cdrom -> scd0
```

To mount it manually:

```
sudo mount /dev/scd0 /media/cdrom0
```

Jim

---

### Post by stweston on 2008-09-23
Well, I tried the "ls -l ..." but it simply gives me a "no such file or directory" message.

Furthermore, I tried "sudo mount ..." and it says "~sh: sudo: not found" Even worse, I don't even know what sudo means! (I'm a real newbie at Linux...)

---

### Post by hasan.akgoz on 2012-01-14
> **stweston said:**
> Well, I tried the "ls -l ..." but it simply gives me a "no such file or directory" message.

Furthermore, I tried "sudo mount ..." and it says "~sh: sudo: not found" Even worse, I don't even know what sudo means! (I'm a real newbie at Linux...)
last reply sory
```
mkdir cdrom0
```

---

