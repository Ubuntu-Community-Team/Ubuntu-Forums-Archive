---
title: "Need to ReInstall Ubuntu 12.04 on my linux partition, but need to retain my files"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by straitjacket525 on 2012-09-06
I had Ubuntu and windows 7 installed on seperate partitions on my laptop, well windows crashed, of course forcing a reinstall of 7, well after i installed 7 i no longer had the option to boot into my linux partion when i turned the laptop on, so i was just going to load up the live cd of ubuntu and do a reinstall, but i need to keep my files and i cant just copy them over using the live cd because it says permission denied can anyone help me get my files?
or tell me how to reeneable the boot selection screen so i can just boot into the already installed ubuntu on my hard drive?

---

### Post by VMC on 2012-09-06
You should still have the ubuntu partition. No need to re-install.

Run the live cd, then out put the result of this command:

```
sudo blkid

```

---

### Post by straitjacket525 on 2012-09-06
this is what i got after inputing that command

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9cff088f-a5be-43e5-ba2d-8b6d0533e3cf" TYPE="ext4" 
/dev/sda2: UUID="C48212D28212C8B6" TYPE="ntfs" 
/dev/sda5: UUID="5325a1be-49a4-4311-9e56-c5189d988984" TYPE="swap" 
/dev/sr0: LABEL="Ubuntu 12.04.1 LTS i386" TYPE="iso9660" 
/dev/sdb: UUID="3281-1890" TYPE="vfat"

idk what this means though, im really new to ubuntu, i love it but i have some problems adapting

---

### Post by Buntu Bunny on 2012-09-06
Couldn't he just reinstall grub?

---

### Post by VMC on 2012-09-08
Yes, just re-install grub.

Booting from the livecd, use the following commands from a terminal:

```
sudo mount -t ext4 /dev/sda1 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

