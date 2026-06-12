---
title: "How to boot from second hard drive?"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by PickPocket8686 on 2007-10-23
I have two hard drives.  One IDE 300GB Seagate, one SATA 150GB Raptor, and I'm using Ubuntu 7.10 64 bit edition.
I partitioned the hard drives like so.
```
Seagate 300GB IDE
/home

Raptor 150GB SATA
/
swap
```
My only problem is I can't boot into Ubuntu from the Raptor.  But if I set the Seagate as the first hard drive to boot in BIOS it works fine.
My question is if I reinstall what do I need to do to make Ubuntu boot off of the Raptor?

Any help is appreciated,
Austin

---

### Post by PickPocket8686 on 2007-10-23
Anyone?

---

### Post by PickPocket8686 on 2007-10-23
Do I just need to change (hd0) to (hd1) in the advanced tab before partitioning the hard drives with the Ubuntu installer?

---

### Post by ssam on 2007-10-23
you might be able to fix it with editing the menu.lst and using update-grub and grub-install. be sure to read the man pages of both and the comments in menu.lst.

i think i had trouble in the past with changing the BIOS boot order, and that effecting the grub disk numbering. it took trial and error to solve

---

