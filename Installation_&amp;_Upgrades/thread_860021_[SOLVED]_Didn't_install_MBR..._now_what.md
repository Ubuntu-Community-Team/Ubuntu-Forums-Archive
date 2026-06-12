---
title: "[SOLVED] Didn't install MBR... now what?"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by Ambush Commander on 2008-07-15
Hello all,

I recently re-partitioned and installed Ubuntu as a dual-boot on my laptop. During the process, the tutorial I was following instructed me to make sure Ubuntu didn't install anything to the MBR. So I didn't. Now I can't boot into Ubuntu. :-(

I've been doing a little research into getting the Windows Vista bootloader to work with Ubuntu, and getting information overload. Given these requirements:

1. Windows should still boot first
2. Any action I take should be reversible
3. I don't have a Vista recovery CD
4. I have an Ubuntu Live CD/Install CD

What options are on the table? Thanks!

---

### Post by logos34 on 2008-07-15
> **Ambush Commander said:**
> the tutorial I was following instructed me to make sure Ubuntu didn't install anything to the MBR. So I didn't. Now I can't boot into Ubuntu. :-(
...

What options are on the table? Thanks!

The easiest solution is to reinstall ubuntu (~30 min), but this time when you get to 'Ready to Install' screen, press 'Advanced' button, then replace default Grub location '(hd0)' with **/dev/sda?**, where ? is the linux root partition #.  That will install Grub to the boot/first sector of the ubuntu root, not overwrite the vista bootloader on the MBR.  OR if you have a floppy drive, write grub to a floppy by entering **(fd0).**

Now that grub is installed, you have a few (reversible) choices:

1) If you put grub on a floppy you can boot into ubuntu immediately. There should also be a vista entry, which hopefully will work.  If it does you have the option of either continuing to use the floppy or else overwrite the vista bootloader on the MBR by running this in a terminal:

sudo grub-install /dev/sda

2) If you put grub on the linux root, you can then use [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Linux") to have Vista dual boot ubuntu. (within easybcd you have a further choice of using the Neogrub boot method).

3)  Finally there's this v[ista repair download]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD") for those without a vista install dvd, in case you get into trouble.  (I'm not sure if it's limited to HP and Dell users , or for everyone.  You'll have to check). 

Good luck

---

### Post by Ambush Commander on 2008-07-15
After mucking around with the grub-installer python scripts for a little bit, I finally bit the bullet and did what you suggested. It worked like a charm :-) EasyBCD is an excellent piece of software. Thanks!

---

### Post by logos34 on 2008-07-15
Sounds good.  Mark thread as 'solved' (>thread tools).

have fun!

---

