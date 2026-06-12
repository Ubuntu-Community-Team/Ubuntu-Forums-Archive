---
title: "Grub2 and Multiboot Disk"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kdfuller on 2009-10-16
I clean installed Karmic yesterday using the daily build iso. All is working well except my dual boot. I have windows XP and Vista on one disk and Ubuntu on another. I ran update-grub2 and got it to recognize my other disk and it will boot and give me the option to choose whether I want XP or Vista. If I choose Vista all works well but if I choose XP it immediately reboots without any messages.  I unplugged the Ubuntu disk and the system will boot to XP or Vista without a problem so I don't think it is that disk. Any ideas what is going on? It worked perfectly on the last few versions of Ubuntu so it must be the new Grub2 giving me problems.

---

### Post by VMC on 2009-10-16
Output this:

```
sudo fdisk -l
sudo blkid
sudo cat /boot/grub/grub.cfg
```

---

