---
title: "Install 3 operating systems"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by Riverdale on 2008-08-01
Hi

I currently have a dual boot Windows XP and Ubuntu Hardy. I also have an old 40 gigs hard disk which I connect to my system using USB and on which I installed another flavor of linux (fedora). But on rebooting the grub of ubuntu showed up with no traces of fedora grub (I installed it on external disk too).

Is it possible to add fedora booting to ubuntu grub, or maybe 2 grubs installed seperately ?

Thanks,
Rd

---

### Post by Herman on 2008-08-01
I like to add an option to my GRUB menu in Ubuntu for booting a USB drive, I do it something like this,
```
title             Boot MBR of USB
root            (hd1)
chainloader +1

```I add a boot stanza like that to the bottom of my /boot/grub/menu.lst file in Ubuntu.
You need to have a boot loader installed in the MBR of your USB drive for that to work.
If you have more than one hard disk in your computer, you might have to change the (hd1) to some other hard drive number.
You can type anything you like in the top line after the word 'title'.

---

