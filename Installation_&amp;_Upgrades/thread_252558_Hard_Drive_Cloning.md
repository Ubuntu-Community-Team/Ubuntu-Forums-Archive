---
title: "Hard Drive Cloning?"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by GmAz on 2006-09-07
Is there a piece of software that works like Norton Ghost for Ubuntu?  I just spent several hours setting up one machine and I don't want to go through it all again.  Is there a way to close one hard drive to another?  If so, is there any fallbacks under linux?  I know with Windows, I run the sysprep utility so it can be renamed and rejoined to a domain.  Thanks!

---

### Post by zxee on 2006-09-07
There is g4l [http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)
which is suppose to be like the propritary software you mentioned.

---

### Post by aysiu on 2006-09-07
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) may help.

---

### Post by suhaib on 2006-09-07
Does anyone know how to do this in the command line only?

---

### Post by aysiu on 2006-09-07
> **suhaib said:**
> Does anyone know how to do this in the command line only?
Maybe this?
[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

### Post by zxee on 2006-09-07
> **suhaib said:**
> Does anyone know how to do this in the command line only?

You could use dd e.g. dd if=/dev/hda1 of=/dev/hdb1
The partitions or drives should be equal in size, or the of (output file) should be larger than the input. Take a look at man dd

---

### Post by GmAz on 2006-09-07
VERY helpful.  I will look at it all tongiht after work.  Many thanks!

---

