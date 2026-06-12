---
title: "Install Problem"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by DavidBarkhuizen on 2008-03-29
Hello,

I tried to install GG on a intel x86 system, but after I select the install/run Ubuntu option from the first menu screen on booting from the live disc, the install fails - giving me the following error message

(initramfs) [55.891870] ata 2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[55.891870] ata 2.00: cmd a0/01:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x5a data 128 in

then the message repeats a few times, with the numbers in the square brackets changing, e.g:

[96.674090]
[137.456324]
[178.238561]

Any advice would be appreciated.

btw:  6.10 install fine

Thanks.

---

### Post by dstew on 2008-03-29
Did you check the CD integrity? This kind of error is usually a bad CD, or a hardware problem. Do the CD integrity test (menu choice), and if that passes do the Memory test. If it passes that, post back here for more advice.

---

