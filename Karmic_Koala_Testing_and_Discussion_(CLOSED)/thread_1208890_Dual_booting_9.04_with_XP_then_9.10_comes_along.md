---
title: "Dual booting 9.04 with XP then 9.10 comes along?"
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kirk M on 2009-07-09
Let's see if I can make this clear. After having an install of Ubuntu 8.10 and (upgraded to) 9.04 on my PC I went back to a Windows only install intending to dual boot WinXP with a clean install of 9.04. However, I'm concerned with what will happen when version 9.10 comes out in that it's supposed to have an updated Grub loader which, by what I hear, will overwrite the installed grub loader (as it should) and wipe out the dual boot option in the process leaving me without the ability to boot into Windows.

My question then is, if I have 9.04 dual booted with WinXP and 9.10 arrives, will upgrading still allow me to dual boot or will I have to wipe out 9.04 entirely and start clean (I wish to check out the upgrade feature between 9.04 and 9.10 if I can). I'm using Ubuntu for testing/experince purposes so I really don't mind having to start fresh but I'd rather not if I can avoid it.

Of course I could always download the latest dev build of 9.10 if I had to. :p

---

### Post by Herman on 2009-07-10
Upgrading from GRUB Legacy to GRUB 2 doesn't wipe out your Windows XP boot option, I don't know where you could have picked up that idea from but it's simply not the case.

GRUB 2 (or GRUB 1.96 so far), comes with a much more advanced 'sudo update-grub' command, which is capable of automatically searching your hard disk for other operating systems and creates a new boot menu for you with a menu entry for each operating system. It's really cool and it works great, you have nothing to worry about and everything to look forward to! :)

---

### Post by Kirk M on 2009-07-10
> **Herman said:**
> Upgrading from GRUB Legacy to GRUB 2 doesn't wipe out your Windows XP boot option, I don't know where you could have picked up that idea from but it's simply not the case.

GRUB 2 (or GRUB 1.96 so far), comes with a much more advanced 'sudo update-grub' command, which is capable of automatically searching your hard disk for other operating systems and creates a new boot menu for you with a menu entry for each operating system. It's really cool and it works great, you have nothing to worry about and everything to look forward to! :)

Thanks Herman. Can't quite remember where I picked up that info whether it was here or a comment thread on one of the many Ubuntu flavored blogs. Glad to know that the upcoming GRUB 2 has some smarts built into it. Still learning the ropes of Ubuntu BTW. Gives an old geek something new to peak his interest.

---

