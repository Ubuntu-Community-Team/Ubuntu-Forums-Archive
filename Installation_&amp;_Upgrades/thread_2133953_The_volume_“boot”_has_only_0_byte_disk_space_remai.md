---
title: "The volume “boot” has only 0 byte disk space remaining"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by wjstarck on 2013-04-09
I'm getting 'The volume “boot” has only 0 byte disk space remaining' whenever I try to run sudo apt-get upgrade. Ubuntu 12.10 64 bits

I can't resize /boot in gparted (it says maximum size 243 MB, which it is). If I try to run a sudo apt-get autoremove it fails because it says there is not enough disk space. I am unable to remove any of the kernel images to increase the free space on /boot because it says they can be removed due to dependencies if I try.

I am running 3.5.0-26-generic

The kernel images sitting in /boot are

3.5.0-17-generic
3.5.0-18-generic
3.5.0-19-generic
3.5.0-21-generic
3.5.0-23-generic
3.5.0-25-generic

What do I do now?

---

### Post by kuifje09 on 2013-04-09
You can if it is impossible to remove by using the gui or other helper, remove kernels by hand.

as example, you could remove kernel version 3.5.0-21-generic    in   /boot  obvoius.

then remove all the files listed with ```
    ls *3.5.0-21*
```

which will give you 6 files then remove them one by one or all together with

```
rm -i  *3.5.0-21*
```       DONT forget the   -i    which will make it ask for deletion.  just say   y   if its okay.

Afterwards you can clean up the libs and modules who needs to be removed.  Try first with the gui.

---

### Post by wjstarck on 2013-04-09
Whew.

I found this thread here: [http://askubuntu.com/questions/171209/my-boot-partition-hit-100-and-now-i-cant-upgrade-cant-remove-old-kernels-to](http://askubuntu.com/questions/171209/my-boot-partition-hit-100-and-now-i-cant-upgrade-cant-remove-old-kernels-to)

So the solution was to manually delete most of the older config, abi and System.map files to free up space.

---

### Post by kuifje09 on 2013-04-09
That can be correct indeed. I sometimes save 1 old kernel after big changes...
To fall back , if something strange happend...

---

### Post by wjstarck on 2013-04-09
Thank you for your responses

---

