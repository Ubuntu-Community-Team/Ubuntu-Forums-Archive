---
title: "GRUB 2.0 eats Win7 line after compilation"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by nicepat on 2010-03-26
My ubuntu 32-bit 9.10 compiles kernel a few times, and now I realized my Win7 lines disappeared. First time when I made the dual boot system, I remember there is a line for Win7, and able to boot up Win7. And then I ran compilations 2 ~ 3 times, and now I see the lines gone. 

I know 'editing GRUB' is risky, and want to hear advice how to fix. - Actually I don't think I can edit grub.cfg file manually. Any help?

In my Ubuntu Desktop menu, I still see and mount the Windows disk (physically different partition)

---

### Post by insecureboy on 2010-03-26
try to boot into recovery mode and there u'll see an option related  to grub. something like "rescan grub" or somethin but if u choose that it will reload the list and it may help

---

### Post by nicepat on 2010-03-29
**Yes it resolved**. GRUB rescanning in recovery mode can find the Win7 in the other partition. thanks for the help.

---

