---
title: "Help! My pc doesn't work! Problema with grub"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by ViviPB on 2010-06-07
Hi!

I was messing around with the partitions and accidentally y deleted the ubuntu partition! I have Windows 7 as a dual boot but I can't access to that OS anymore.

The message that I get is:
error: no such partition.
grub rescue>

What should I do? All my info is backed up.  

Thanks!

---

### Post by darkod on 2010-06-07
Depends what you want to do.

1. You can try to get the ubuntu partition back, it will probably work.

2. You can install windows bootloader to the MBR so you can at least boot win7. But if you plan to install ubuntu again that's pointless.

3. You can install ubuntu again in the place of the deleted partition.

If you want to try and get the partition back, most people have reported success with Testdisk.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Their How-to for recovering deleted partitions:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by ViviPB on 2010-06-07
Hi!

I do eant to reinstall ubuntu...I was messing around with the partitions because I  was trying to extend the Ubuntu partition, obviusly I did it wrong.

I will try with the TestDisk, if it doesn't work I could reinstall Ubuntu from the USB stick as I did it on the first time, right?

Thanks for your help :)

Viviana.

---

### Post by drs305 on 2010-06-07
> **ViviPB said:**
> I will try with the TestDisk, if it doesn't work I could reinstall Ubuntu from the USB stick as I did it on the first time, right?

Yes you should be able to reinstall it if TestDisk fails.

If you have to reinstall, perhaps you can resize your partitions before you begin the installation. 

If you get TestDisk to restore your original installation and still need to resize Ubuntu, perhaps this link will help:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")
Start reading about half way through the first post for resizing tips. The first portion describes a bug that was present in Jaunty.

---

### Post by ViviPB on 2010-06-07
I have a doubt about TestDisk, how can I use it if I can't run it as it says onthe step-by-step guide? Anyway, I think I'm going to reinstall Ubuntu, seems easier and I can resize my HD.

Thank you guys very much...

Viviana.:D

---

### Post by darkod on 2010-06-07
> **ViviPB said:**
> I have a doubt about TestDisk, how can I use it if I can't run it as it says onthe step-by-step guide? Anyway, I think I'm going to reinstall Ubuntu, seems easier and I can resize my HD.

Thank you guys very much...

Viviana.:D

You can run testdisk from ubuntu cd in live mode.

---

