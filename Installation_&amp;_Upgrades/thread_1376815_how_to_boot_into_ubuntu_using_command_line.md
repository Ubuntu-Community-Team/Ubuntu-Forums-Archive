---
title: "how to boot into ubuntu using command line?"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by redace25 on 2010-01-09
Hi,

I used LVPM and this guide ([http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)) to transfer my wubi ubuntu installation to a new partition. The problem I am now having is that I cannot boot into ubuntu because the bootloader is not setup properly. I know this because I was able to boot into ubuntu fine after transferring it to a separate partition.So I uninstalled wubi from windows xp and now I can't boot into ubuntu. I know I installed it properly because     setup (hd0,2) is successful. When i enter the boot command it says "Kernel must be loaded before booting". So, if anyone can help me with how to boot into ubuntu using command line and then how to fix the bootloader, I will be very grateful.

---

### Post by sisco311 on 2010-01-09
if you are using grub2:
```

insmod ext2
set root=(hd0,2)
linux	/boot/vmlinuz-<**hit tab to auto-complete**>  root=/dev/sda2  ro quiet splash
initrd	/boot/initrd.img<**hit tab to auto-complete**>
boot

```

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

if you are using grub legacy:
```
root (hd0,2)
kernel /boot/vmlinuz-<**hit tab to auto-complete**>  root=/dev/sda3  ro quiet splash
initrd	/boot/initrd.img<**hit tab to auto-complete**>

```

---

### Post by nick_goodfate on 2010-01-09
> **redace25 said:**
> Hi,

I used LVPM and this guide ([http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)) to transfer my wubi ubuntu installation to a new partition. The problem I am now having is that I cannot boot into ubuntu because the bootloader is not setup properly. I know this because I was able to boot into ubuntu fine after transferring it to a separate partition.So I uninstalled wubi from windows xp and now I can't boot into ubuntu. I know I installed it properly because     setup (hd0,2) is successful. When i enter the boot command it says "Kernel must be loaded before booting". So, if anyone can help me with how to boot into ubuntu using command line and then how to fix the bootloader, I will be very grateful.
i think this can help you too...
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by nick_goodfate on 2010-01-09
> **sisco311 said:**
> if you are using grub2:
```

insmod ext2
set root=(hd0,2)
linux	/boot/vmlinuz-<**hit tab to auto-complete**>  root=/dev/sda2  ro quiet splash
initrd	/boot/initrd.img<**hit tab to auto-complete**>
boot

```

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

if you are using grub legacy:
```
root (hd0,2)
kernel /boot/vmlinuz-<**hit tab to auto-complete**>  root=/dev/sda3  ro quiet splash
initrd	/boot/initrd.img<**hit tab to auto-complete**>

```
hi sisco311 ! can you explain what this code does ? i m new in linux... i dont need it now , just to know... thnx !

---

### Post by sisco311 on 2010-01-09
> **nick_goodfate said:**
> hi sisco311 ! can you explain what this code does ? i m new in linux... i dont need it now , just to know... thnx !

[uhelp]community/Grub2#Rescue Mode[/uhelp]

---

### Post by nick_goodfate on 2010-01-09
thank u for the reply !!

---

### Post by redace25 on 2010-01-09
> **sisco311 said:**
> if you are using grub2:
```

insmod ext2
set root=(hd0,2)
linux    /boot/vmlinuz-<**hit tab to auto-complete**>  root=/dev/sda2  ro quiet splash
initrd    /boot/initrd.img<**hit tab to auto-complete**>
boot

```[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

if you are using grub legacy:
```
root (hd0,2)
kernel /boot/vmlinuz-<**hit tab to auto-complete**>  root=/dev/sda3  ro quiet splash
initrd    /boot/initrd.img<**hit tab to auto-complete**>

```
 
Thanks sico311, now I am going to work on fixing the bootloader

---

