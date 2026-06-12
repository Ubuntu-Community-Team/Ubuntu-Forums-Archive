---
title: "Dell Poweredge840"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by flemi on 2008-04-23
Installation of Ubuntu 6.06LTS Server edition ended in a disappointment!:(

Dowloaded the distribution to CD, 
started a brand new Dell Poweredge840 (empty disks) with the installation CD,
picked install from the menu,
3lines is what I het, after that ... nothing:

Decompressing Linux...done.
Booting the kernel.
Strating system log deamon: syslogd, klogd.

That's all folks!

Any suggestion how to do the installation correctly?

---

### Post by dstew on 2008-04-23
It could be a bad installation disk. Check the disk integrity (menu item on opening screen).

---

### Post by flemi on 2008-04-23
Tried that one already. 
It improves the probelem by 1 line ...
The system stops after "Booting the Kernel."

I did check the cheksum of the image, which was OK. 

Is there a way to check the CD on a Windows system?

---

### Post by flemi on 2008-04-23
Hmmm ... 
when i wait long enough also the third line appears
:(

---

### Post by dstew on 2008-04-23
> Is there a way to check the CD on a Windows system?No, I don't think so, because it has to be booted to be checked. You can try to boot it in another computer. If it boots OK in another machine, it might be a problem with the Live CD drivers working with your hardware. That can sometimes be worked around with kernel parameters, or a Safe Graphics mode boot, both accessed by pressing F6 at the first menu. If it doesn't boot in any machine, then it is probably a bad disk.

If the Md5 checksum of the .iso you downloaded checked out OK, but the disk is bad, it is probably a bad burn. Burn again, but use a slow speed, no more than 4x, with good quality CD-R media.

---

