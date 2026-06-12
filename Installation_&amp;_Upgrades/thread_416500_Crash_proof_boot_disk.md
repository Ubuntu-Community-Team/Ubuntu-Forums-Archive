---
title: "Crash proof boot disk?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by fenderuser on 2007-04-21
I have a dual boot setup with Windows XP on my  1st drive and Ubuntu 7.04 on my 2nd drive. What I would like to know is how to be able to still login in and run Ubuntu should the 1st disk crash (it is a few years old now).  Can I create a separate boot disk, say on a floppy or a cd that I can use to boot from and then run Ubuntu?

thanks.

---

### Post by BoneKracker on 2007-04-21
Install GRUB to the second disk's Master Boot Record instead of the first disk.  Then switch which disk is designated as the "boot disk" in your BIOS.  

(You know, when you boot up, you see "press F2 to enter setup" or something like that.)  That way, it matters naught if the first disk crashes, you computer will still boot and present you with the menu (you just won't be able to select "Windows" and have it work.

---

