---
title: "install GRUB in Root-Partition"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by cccc on 2006-09-25
hi

howto install GRUB to the Root-Partition instaed of MBR ?
where can I find the GRUB configuration under GNOME ?
I have dapper drake installed.

greetings
cccc

---

### Post by confused57 on 2006-09-25
> **cccc said:**
> hi

howto install GRUB to the Root-Partition instaed of MBR ?
where can I find the GRUB configuration under GNOME ?
I have dapper drake installed.

greetings
cccc

I'm not sure why you'd want to install to the root partition...with Dapper  already installed, you can use the Dapper Live CD:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

You'd need to specify to setup grub on the Dapper root partition.

---

### Post by cccc on 2006-09-26
```
grub-install /dev/hda2
``` 
solved my problem !

I'm using Windows Boot-Loader and **bootpart**:

[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

to start Ubuntu.

and it works well.

knows someone what happens now after kernel upgrade ?
will the new kernel write into MBR ?

---

