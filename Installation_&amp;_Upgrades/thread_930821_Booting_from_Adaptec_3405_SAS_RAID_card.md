---
title: "Booting from Adaptec 3405 SAS RAID card"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by flainn on 2008-09-26
Hi,

I got my RAID 10 up and running last night on an Adaptec 3405 SAS card. Ubuntu 8.04 installed no problem, but I can't get it to boot from the card.

My BIOS is set to allow booting from the card, and I installed the bootloader on hd0 (not sure exactly which drive that is, as I also have a 500 GB SATA drive on my motherboard controller, mounted as /home).

If I boot off the CD and then select "Boot from first hard disk" it boots from the RAID card with no problem.

Is there a way to make it boot from the card without using the CD-ROM as a stopgap?

---

### Post by flainn on 2008-09-27
No comments from the peanut gallery, huh? :-|

The solution was to install GRUB onto my 500GB SATA drive and tell the BIOS to boot off of it:

[FONT="Courier New"]sudo grub
root(hd0,0)
setup (hd1)[/FONT]

---

