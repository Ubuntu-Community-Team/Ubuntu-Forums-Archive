---
title: "creating a usb boot disk for bsd HELLLLP"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by kr651129 on 2010-12-19
I cant for the life of me figure out how to create a freebsd bootdisk onto my usb drive. from ubuntu


help?

---

### Post by wilee-nilee on 2010-12-19
> **kr651129 said:**
> I cant for the life of me figure out how to create a freebsd bootdisk onto my usb drive. from ubuntu


help?

How big is the USB, and do you have a clue about BSD?

---

### Post by kr651129 on 2010-12-19
8GB, not one clue, always wanted to mess with it.  Gonna duel boot ubuntu and bsd

---

### Post by wilee-nilee on 2010-12-19
> **kr651129 said:**
> 8GB, not one clue, always wanted to mess with it.  Gonna duel boot ubuntu and bsd

Good plan but easybsd is not for beginners it is a bit tricky and uses the lilo bootloader I think.

---

### Post by kr651129 on 2010-12-19
# dd if=BootIMG.iso of=/dev/sdc1 bs=64k

---

### Post by kr651129 on 2010-12-19
> **wilee-nilee said:**
> Good plan but easybsd is not for beginners it is a bit tricky and uses the lilo bootloader I think.

Yeah, been using linux for quite sometime, not a n00b, but not an expert so I've got enough wits about me to figure it out, just want a new challenge :)

---

