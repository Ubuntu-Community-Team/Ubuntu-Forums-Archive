---
title: "Editing Grub to dual boot encrypted Windows."
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by u-slayer on 2012-02-23
I'm trying to dual boot encrypted windows and ubuntu using this guide:

[http://www.steve-oh.com/blog/index.php/ubuntu-vista-dual-boot-full-encryption-with-truecrypt/](http://www.steve-oh.com/blog/index.php/ubuntu-vista-dual-boot-full-encryption-with-truecrypt/)

I'm trying to figure out all of the stupid changes grub2 forces you to make. So far I have changed this:

title Windows Vista/Longhorn
rootnoverify (hd0,0)
makeactive
chainloader (hd0,1)/truecrypt.mbr
boot

to this:

menuentry "Windows 7"{
insmod chain
parttool (hd0,1) boot+
chainloader (hd0,2)/truecrypt.mbr
boot
}

Unfortunately Grub won't even show me a menu during boot up (although sometimes It does for unknown reasons and it still doesn't work)

I've confirmed the entry exists by running startupmanager. What am I doing wrong?

---

### Post by raja.genupula on 2012-02-24
ok after doing editing,  are you doing 
```
sudo update-grub 
```


whats the output of it .

---

### Post by u-slayer on 2012-02-24
> **raja.genupula said:**
> ok after doing editing,  are you doing 
```
sudo update-grub 
```


whats the output of it .

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /memtest86+.bin
done

---

### Post by raja.genupula on 2012-02-24
use this tutorial
[http://ubuntuforums.org/showthread.php?t=761530](http://ubuntuforums.org/showthread.php?t=761530)

---

### Post by Mark Phelps on 2012-02-24
Your update-grub output did NOT show Windows 7 Loader -- meaning that the os_prober program did not find any evidence of the loader files on your PC.

If you're setup with the two-partition Win7 arrangement in which the loader files are on one small partition, and the remainder of the OS files and data are on a larger (in this case, encrypted) partition, the os_prober should have found the loader files present on the smaller partition.

Don't use disk encryption (as it is largely a waste of time and a real PAIN when something goes wrong), but I believe you must have this two-partition arrangement in Win7 when you have encrypted the OS partition.

You should consider checking on a Windows 7 forum (sevenforums.com) -- as some of the experts there also run Linux systems.

---

