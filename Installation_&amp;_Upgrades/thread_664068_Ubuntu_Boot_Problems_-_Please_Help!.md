---
title: "Ubuntu Boot Problems - Please Help!"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by ataxicwolf on 2008-01-10
So I just recently installed Ubuntu onto my external hard drive. I have windows vista on my main hard drive, and I plan to boot ubuntu from the external one. The problem is that when I try and boot, I'll get either one or two errors:

If I boot with the BIOS having the external harddrive trying to boot first:
It simply comes up with "GRUB" and has a blinking cursor after it

If I book with the BIOS having the main hard drive trying to boot first:
It comes up with Grub Loading... (please wait) Error 17

Also, I had this same problem when installing fedora. To fix the problem, I think i may have installed the boot loader on both drives, but I can't really recall.

Thanks for any help.

---

### Post by ataxicwolf on 2008-01-10
Update: I've fixed the problem.

For all the googlers out there, the solution was to boot the hard disk according to the drive order of my bios. (After I had installed the grub loader in the actual external hard drive, rather in my normal drive)

So I installed the GRUB loader into hd1,0

Then I set up my bios to boot the external (hd1) first, then my main (hd0)

Then in the boot loader, it kept giving me an error 17, so I realized I had to change the Ubuntu options to boot into (hd0,0) rather than (hd1,0) where it was, because I had changed the drive order.

Whew.

---

