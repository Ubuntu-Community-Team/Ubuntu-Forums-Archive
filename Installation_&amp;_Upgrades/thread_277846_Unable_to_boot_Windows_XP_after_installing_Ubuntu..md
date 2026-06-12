---
title: "Unable to boot Windows XP after installing Ubuntu."
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by esaa on 2006-10-15
Hi 

I ve installed Ubuntu 6.06 in my PC which is having Windows XP in D:\(not in C:\). I ve installed Ubuntu with option to Use Continous Space for new partitions. 

After installing i`m getting any OS chooser dialog with out Windows XP option. 

The following is the reading of menu.lst file in /boot/grub. Please note that there is no Windows XP link in the following..

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot 

Please advice me what to do.. i ve many valuable work in windows.. Please help me..

Thanks in advance.

---

### Post by adwait on 2006-10-15
Are you sure you did not choose to delete your windows partition or something? Did Ubuntu detect Windows XP while installing? Anyway, please post the output of
```
sudo fdisk -l
```

---

### Post by nereid on 2006-10-15
Just use the search function to search for the right Windows entry for GRUB. Something like

```

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Beware to change the root directive to the right harddrive.

---

### Post by CalcProgrammer1 on 2006-10-15
For some reason, my Grub menu got reset.  I installed a slave hd to put Linux on and left Win XP alone on it's hd.  After a lot of work, and rebooting for nothing, I found out that for some odd reason hp had installed Win XP on hd(0,1) not hd(0,0).  So check your other hd partitions not just hd(0,0).

---

