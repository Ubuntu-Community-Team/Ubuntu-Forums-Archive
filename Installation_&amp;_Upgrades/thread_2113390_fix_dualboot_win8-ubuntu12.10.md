---
title: "fix dualboot win8-ubuntu12.10"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by dumble on 2013-02-07
Hello,

I am trying to install ubuntu 12.10 next to my win8 installation. But after a couple of tries I messed up my bootloader a bit.

Can you guys help me fix my bootloader problems. Currently I installed 12.10 on a new SSD, I put swap on a harddisk. Win8 was allready installed on second SSD. 

I just installed it, and I installed the grub bootloader on ext4 ssd with ubuntu 12.10. But it boots now into win8 when I restart. I dont get into grub..

I am currently on the live-usb, and installed boot-repair. Here is a summary. You'll probably notice 2 windows8 bootloaders because of previous install attempts. How do I fix and make a 'clean' boot-menu for my dualboot?


Boot-summary:
```
http://paste.ubuntu.com/1620808/
```

---

### Post by oldfred on 2013-02-07
If you set BIOS to boot sdc the 120GB drive does grub/Ubuntu not boot? That looks correct. If you are booting Windows you must be booting the sdb 128GB drive.
The install of grub in sda is incorrect, as it is looking for a partition that now does not exist.

---

### Post by dumble on 2013-02-07
I figured it out. My mistake, fixed it now with boot-repair. ALthough there are still 2 windows 8 bootloaders, one of them is not working. And also there is not the option of memtest anymore (not that I use it, so it doesnt really matter)

---

