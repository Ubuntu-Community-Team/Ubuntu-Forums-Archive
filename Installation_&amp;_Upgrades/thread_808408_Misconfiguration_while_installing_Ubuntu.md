---
title: "Misconfiguration while installing Ubuntu"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by liono14 on 2008-05-26
Hi Guys, 

I think during installation something went wrong(my bad), now I cannot access my Window's Partition, Even after trying some issues explained in other threads didnt worked for me. I know it would simple but can anybody point out where i am wrong? 

```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d7ccee75-d7b4-4e8e-9d4b-d1091c89cc89 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d7ccee75-d7b4-4e8e-9d4b-d1091c89cc89 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title              Windows XP
root               (hd0,1)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```

```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008b2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        5593    44917740    f  W95 Ext'd (LBA)
/dev/sda2   *        5594        7174    12699382+  83  Linux
/dev/sda3            7175        7296      979965   82  Linux swap / Solaris
/dev/sda5   *           2        5593    44917708+   7  HPFS/NTFS

```

as you can see Windows is in extended version but its not picking up 

Any Suggestions?

---

### Post by Pumalite on 2008-05-26
I imagine you are getting an error 12...You cannot boot Windows from a logical partition. Windows needs a primary partition. If you want to, you can wait for Herman to give you a hand. I know he has booted Windows from a logical partition, but is rather convoluted.

---

### Post by liono14 on 2008-05-26
> **Pumalite said:**
> I imagine you are getting an error 12...You cannot boot Windows from a logical partition. Windows needs a primary partition. If you want to, you can wait for Herman to give you a hand. I know he has booted Windows from a logical partition, but is rather convoluted.

Thanks for reply I am getting Error 13 
Never mind i Will wait for more replies, I don't really mind if i cant use Windows, I think i will rarely use Windows ;) now on.

---

### Post by element12 on 2008-05-26
try:
```

title              Windows XP
root               (hd0,1)
chainloader        +1

```

for your xp in the menu.lst

---

### Post by Pumalite on 2008-05-26
[http://users.bigpond.net.au/hermanzone/p15.htm#13](http://users.bigpond.net.au/hermanzone/p15.htm#13)

---

