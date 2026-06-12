---
title: "Messed up with partition"
date: 2016-02-28
forum: Installation &amp; Upgrades
---

### Post by ubu10 on 2016-02-28
My desktop has dual OS, Win 7 and Ubuntu 12. I tried to upgrade to Ubuntu 14 using a DVD with ISO. In the process, I messed up with the boot files. Now I can't boot into anything. However, the command prompt grub_rescue comes up. I looked up with few other threads and tried but none worked. Here is what I tried


ls outputs (hd0) (hd0,msdos8) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos4) (hd0,msdos1) (fd0)


I tried ls (hd0,msdos8), all msdos 1- 7 gave unknown filesystem, but not msdos8.
So, I guess, this partition has Ubuntu files.
I tried these
> set root=(hd0,msdos8)
set prefix=(hd0,msdos8)/boot/grub/
insmod normal


I get this message
file not found


I don't get how to proceed from here.

---

### Post by deadflowr on 2016-02-28
Follow [this guide to use boot-repair]("https://help.ubuntu.com/community/Boot-Repair").

since it is unclear what the outcome will be.
(whether you reset grub properly or not)
it will probably be best to post the link to the pastebin it generates.

---

