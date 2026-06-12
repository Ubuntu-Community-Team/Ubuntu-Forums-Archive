---
title: "grub2 as default or out-of the -box option"
date: 2009-04-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2009-04-28
What about GRUB2 in karmic koala? (Grub2 as default bootloader or as an out-of-the-box working option.

---

### Post by Slug71 on 2009-04-28
I'm also hoping Grub2 will be default. Worked fine when i was testing it with Jaunty as long as you had os-prober which did become a dependency but i think they want it to detect other OSs without the help of os-prober. 
Not sure how far it has progressed over the last few months though.

---

### Post by KhaaL on 2009-04-28
is grub2 compatible with plymouth?

---

### Post by Slug71 on 2009-04-28
> **KhaaL said:**
> is grub2 compatible with plymouth?

Not sure but id think that it would be.

---

### Post by DanaG on 2009-04-28
Grub2 is nice for UEFI booting... but as long as it lacks a "savedefault" feature, it fails my acceptance tests.  =þ

Bonus points if Ubuntu can make it so the one grub does as Fedora does: it has both the PC-BIOS version AND the grub.efi version in the same package... and updates the boot menu for both.  Their only problem is that it puts it in the same ext2 partition, and not in my EFI partition.

---

### Post by Slug71 on 2009-05-02
There is a entry for this to be discussed at UDS.

---

### Post by jerrylamos on 2009-06-13
Alpha2 has Grub2 (really 1.96) which as shipped does NOT do multi-boot.  Forget dual boot, backup karmics, jaunty, fedora, suse, ... etc.  Official note in the Alpha2 "it will be in Alpha3".

There is a possible try-it-it-might-work on "Please help test Grub2" thread:

sudo apt-get install --reinstall libdebian-installer4
sudo os-prober
sudo update-grub 

Worked on one of my systems which has jaunty & other karmics (in case "update" kills me again).

Oh,yes, good luck on editing grub.cfg.  Nowhere near as good as Grub Menu.lst.

Jerry

---

