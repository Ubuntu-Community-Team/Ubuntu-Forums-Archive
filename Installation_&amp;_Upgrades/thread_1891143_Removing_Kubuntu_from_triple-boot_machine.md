---
title: "Removing Kubuntu from triple-boot machine"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by VanceVEP72 on 2011-12-05
I have a desktop with Windows XP Pro, Xubuntu 11.10 and elementary OS Jupiter (Ubuntu 10.10) installed under a triple-boot setup. How can I remove Xubuntu from the machine and reallocate that drive space for elementary OS? :confused:

---

### Post by darkod on 2011-12-05
Which bootloader are you using to boot? If it's kubuntus bootloader, you can't simply delete the partition because it will stop booting. If it's ubuntus, you can go ahead and simply delete the partition, and then resize the ubuntu partition to use the empty space. But this will also depend on your disk layout, whether they are next to each other on the disk or not.
Also, you can't resize the root partition while it's mounted so you will have to do it from live mode of some sort, either booting from the ubuntu cd, or Gparted Live CD, etc.

---

### Post by VanceVEP72 on 2011-12-06
> **darkod said:**
> Which bootloader are you using to boot? If it's kubuntus bootloader, you can't simply delete the partition because it will stop booting. If it's ubuntus, you can go ahead and simply delete the partition, and then resize the ubuntu partition to use the empty space. But this will also depend on your disk layout, whether they are next to each other on the disk or not.
Also, you can't resize the root partition while it's mounted so you will have to do it from live mode of some sort, either booting from the ubuntu cd, or Gparted Live CD, etc.
Sorry... I mis-typed in my original post (which is now edited). I do not have Kubuntu installed... it's actually Xubuntu 11.10.

So, all I have to do is delete the Xubuntu partition and then resize the elementary OS partition to take up the newly free'd up space?

---

### Post by VanceVEP72 on 2011-12-09
Well, that hosed my computer (at least all Linux partitions). At least I was able to fix the Windows XP bootloader. Hopefully, I can get Ubuntu reinstalled on the f'd-up partition that remains!

---

