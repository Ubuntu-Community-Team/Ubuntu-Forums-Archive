---
title: "starting ubuntu"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by zikmoshe on 2010-08-07
I have xp, vista and w7 installed on my pc's hard disk
I installed ubuntu 10 on the usb disk but I dont see how to start it

---

### Post by rcchume on 2010-08-07
[FONT="Arial"][SIZE="1"]Did you change the boot order in BIOS, to boot from USB first?[/SIZE][/FONT]

---

### Post by kellemes on 2010-08-07
My system has it's own bootmenu you can activate at boot, in my case pressing F8. Maybe your system has it too?
Otherwise you need to change the bootorder indeed, so the stick will be started when available at boot.

---

### Post by zikmoshe on 2010-08-08
> **kellemes said:**
> My system has it's own bootmenu you can activate at boot, in my case pressing F8. Maybe your system has it too?
Otherwise you need to change the bootorder indeed, so the stick will be started when available at boot.


In my case its f11, but it didnt start from the usb disk 
No stick,external disk

---

### Post by dino99 on 2010-08-08
grub-pc (grub2) need to be installed on this usb drive (mbr), then into a console:

sudo grub-mkconfig
sudo update-grub

---

### Post by zikmoshe on 2010-08-08
> **dino99 said:**
> grub-pc (grub2) need to be installed on this usb drive (mbr), then into a console:

sudo grub-mkconfig
sudo update-grub

Can you elaborate pls?
What is Grub, where to  get it and how to install and make it work?

---

