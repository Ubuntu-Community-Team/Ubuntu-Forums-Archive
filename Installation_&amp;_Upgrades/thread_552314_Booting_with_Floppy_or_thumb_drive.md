---
title: "Booting with Floppy or thumb drive"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by algree on 2007-09-16
I have A 2nd HDD 80gig I want to put ubuntu on it but I don't want to change the MBR for win XP. can I install on the hdb 2nd HDD (ubuntu) and put the grub mbr on the 2nd drive with linux and then make a floppy or thumb drive to boot up ubuntu? if so how do I make it?

Thanks for any Help
algree

Compaq Presario
S5000CL

---

### Post by logos34 on 2007-09-16
Using the ubuntu live cd:

When you come to the 'Ready to install' screen, click 'Advanced' button lower right.  Replace '(hd0)' with '**(fd0)**'  (-->sends grub to floppy)

Alternate CD:

Towards the end of the install process you will be be prompted where to write grub bootloader.  use (fd0) or **/dev/fd0**

Boot into ubuntu via the floppy and write grub to the mbr of the 2nd drive:

**sudo grub**
**root (hd1,x)** -->replace x with linux root partition #
[B]setup (hd1) 
quit[/B]

Now you have the option of either using grub on the floppy to boot ubuntu, or changing the Bios drive order so that you boot to grub menu on hdb.

Here's a link in case you need to make the floppy again and/or back up mbr:
[https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28grub%29)

---

