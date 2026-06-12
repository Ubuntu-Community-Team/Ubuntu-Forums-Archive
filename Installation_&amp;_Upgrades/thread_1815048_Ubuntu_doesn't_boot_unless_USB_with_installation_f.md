---
title: "Ubuntu doesn't boot unless USB with installation file plugged in"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by Ljuslykta on 2011-07-30
Hi.
I recently installed Ubuntu 10.04 on my laptop with an USB-drive. The problem is, like the title says, that it doesn't boot unless the USB is plugged in. I've searched on internet and found one solution
```

sudo fdisk -l
# identify your hard drive e.g. /dev/sda 
sudo grub-install /dev/sda

```

But it doesn't work.

Thanks

---

### Post by jerrrys on 2011-07-30
sudo grub-install /dev/sda

must be followed by 

sudo update-grub

---

### Post by Ljuslykta on 2011-07-30
> **jerrrys said:**
> sudo grub-install /dev/sda

must be followed by 

sudo update-grub

It doesn't even find /dev/sda without the USB plugged in. Only 


/dev/sdb1               1       37714   302936064   83  Linux
/dev/sdb2           37715       38914     9632769    5  Utökad
/dev/sdb5           37715       38914     9632768   82  Linux växling / Solaris

---

### Post by jerrrys on 2011-07-30
with your usb drive plugged in, open a terminal and enter **df -h** and please post the results.

---

### Post by oldfred on 2011-07-30
If the drive is sdb then the correct place to install the grub2 boot loader is the MBR of the sdb drive.

When you did the listing from fdisk it said sdb not sda so you are supposed to change to that drive.

sudo grub-install /dev/sdb
sudo update-grub

---

### Post by MetalMusicAddict on 2011-07-30
You know, slightly off-topic but this could be a neat security feature for some. While not a total show-stopper it would slow folks down who didn't know you needed the thumb drive in. :P

---

