---
title: "grub help"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by brickbat on 2005-04-21
Hi,

I have a triple boot system with xp installed first, then ubuntu and then suse.

I installed suse 9.3 yesterday to compare to ubuntu.  It is VERY BLOATED and slow on my poor little 500mhz P3.

My problem now is that suse /boot is doing the booting so if I delete the suse partition I will lose my boot to ubuntu.  My ubuntu boot is still in my ubuntu root dir but it is not being accessed any more.  How do I tell the boot mbr that I want it to use the /boot in hdb5 (ubuntu) instead of hdb6 (suse)?

btw, the suse boot system is prettier than the ubuntu one even though they are both grub.

ciao
bb

---

### Post by tonym on 2005-04-21
The answer depends on what is on the master boot record - the DOS boot manager or GRUB and which disc you boot from originally.  If your /boot's are on hdb5 and hdb6 then it sounds as if it is GRUB.  Where do you boot from,  hda or hdb?

Assuming it is hda then you need to interupt the GRUB boot and enter the following commands

root (hd1,4)
setup (hd0)

That should work if my assumptions are correct.

---

### Post by brickbat on 2005-04-21
thanks.  

my only question is - if this all goes very wrong, and it fails to boot, how can I recover?

I understand I could boot from the live disk, but what would I need to change to at least get it booting from either suse or ubuntu.

ciao
bb

---

### Post by tonym on 2005-04-22
You need to keep a note of what system is in each partition,  where your /boot's are and the full names of your kernel and initrd files.  Then whatever happens you can boot into grub from a livecd and enter parameters manually to boot the correct system.  Again,  if you look at your existing /boot/grub/menu.lst files you can get details of what you will need to enter.

---

### Post by brickbat on 2005-04-22
i took the plunge - it worked perfectly.  thanks.

---

