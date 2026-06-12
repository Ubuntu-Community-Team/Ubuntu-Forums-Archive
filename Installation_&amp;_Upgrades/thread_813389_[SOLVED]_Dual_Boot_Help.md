---
title: "[SOLVED] Dual Boot Help"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by khanoftartary on 2008-05-30
Okay, I'm running Hardy on most of my system. I resized that partition, and created 10 Gb empty space, on which I installed Windows XP (Pro, though I doubt it matters). I then lost my ability to boot Ubuntu, automatically booting XP when I turned on the computer. To remedy this, I reinstalled GRUB using my live CD, and now I can only boot Ubuntu. My XP File system is only accessible when mounted on Ubuntu, and I can't boot the XP OS itself. I'm looking for a way to be able to choose which to boot on startup. I used to have two separate Ubuntu partitions, and I could select either on startup from a menu within the GRUB. I would LOVE for the same tool to work with my XP partition, and that's the ideal if there are reasonable instructions to set that up. But I'm really looking for any similar option of having a boot menu with both my Ubuntu and XP partitions as options.

   Thanks

---

### Post by lukydude on 2008-05-30
i suggest a clean reformat and re-install, xp must come before installing ubuntu then partition for ubuntu afterwards it should display grub at boot asking what to boot (this is what i did)

---

### Post by Pumalite on 2008-05-30
Post:
sudo fdisk -l
cat /boot/grub/menu.lst
You can edit menu.lst yourself and add:
title Windows XP
root (hd?,?)
chainloader +1

---

### Post by khanoftartary on 2008-05-31
> sudo fdisk -l

the partition I want to boot from is > /dev/sda2

what do I put into the question marks in 
> root (hd?,?)?

thanks

---

### Post by Sef on 2008-05-31
> Quote:
sudo fdisk -l 

Applications > Accessories > Terminal 

Then type in this code:

```
sudo fdisk -l
``` Small L

Paste the results here.

---

### Post by meierfra. on 2008-05-31
root (hd0,1)


(Grubs starts counting at 0, so (hd0,1) is the  2 partition on the first hard drive)

---

