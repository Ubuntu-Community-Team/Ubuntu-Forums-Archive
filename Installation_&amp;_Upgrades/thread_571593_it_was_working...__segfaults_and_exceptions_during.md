---
title: "it was working...  segfaults and exceptions during boot?"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by soldstatic on 2007-10-09
Well, it was working yesterday, easiest linux to install ever, great stuff, got all the updates downloaded, think it put a new kernel on there, got some more programs downloaded, played galaga for awhile, then this morning i turn on my computer

First thing I get is this:

> ata2.00: exception emask 0x0 SAct Serr 0x0 action 0x2 frozen
ata2.00: cmd 25/00:88:ff:b9:19/00:03:05:00:00/e0 tag 0 cdb 0x1e data 462848 in
ata2.00: exception emask 0x0 SAct Serr 0x0 action 0x2 frozen
ata2.00: cmd 25/00:88:ff:b9:19/00:03:05:00:00/e0 tag 0 cdb 0x1e data 462848 in


repeated a whole bunch of times. then I get what every programmer loves:

> Segmentation fault

repeated about 20 times. then it continues to try to boot and it says this:

> intel_rng: FWH not detected

and then it starts fsck and says more of

> ata2.00: exception emask 0x0 SAct Serr 0x0 action 0x2 frozen
ata2.00: cmd 25/00:88:ff:b9:19/00:03:05:00:00/e0 tag 0 cdb 0x1e data 462848 in

with a dash of 

> buffer i/o error on device sdc1, logical block 170

thrown in too.


am I correct in thinking that my harddrive sdc is bad???

---

### Post by soldstatic on 2007-10-09
well now i'm trying to boot to the live cd and I get this:

> squashfs error: unable to read page, block 272ee67f, size 1b8b
squashfs error: sb_bread failed reading block (mem address)
buffer i/o error on device sr0, logical block 322637

a bunch of times. ideas anyone???

eventually it starts in xterm. wtf. i hate xterm.

---

### Post by cyberfin on 2007-10-09
I've had the same message, however not as a fault when booting. I get to the login screen and after entering the username it takes 5-10 seconds for the password field to show. After a few seconds again it logs in normally. But the problem continues, everything has a delay of 5-10 seconds. It shouldn't be hardware as the same laptop has run previous versions of ubuntu (about half  a year ago).

No I got the same message as you guys when entering ctrl+alt+f1 and trying to log in. After entering username that message came up, seconds later the password query.

I don't get it.

---

