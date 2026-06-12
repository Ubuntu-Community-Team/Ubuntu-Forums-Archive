---
title: "Guts Gibbon - Freezes during boot at &quot;Loading hardware drivers&quot;"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by annuzzer on 2007-10-31
Hi there,

after the installation of Gutsy Gibbon to my HP Pavilion dv6023ea without any problems the initial boot freezes at
> Loading hardware drivers...
Absolutely no way to get into a console ("Alt + F1" or "Ctrl + Alt  + F1" doesn't work).

Found some similar postings on the w3, some of them with the advice to let it freeze cause it'd unfreeze after 2-3 minutes and continue booting. Unfortunately the freeze actually lasts up to 20 minutes (and up) so I haven't seen the login screen yet.

Any ideas?

Thanks in advance...

Ann

---

### Post by Ayuthia on 2007-10-31
You might try adding noapic noirqdebug to your kernel parameters in /boot/grub/menu.lst.

Since you have an HP laptop, you might want to check out this thread:
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

It might help you in getting things going.

---

### Post by annuzzer on 2007-11-01
@ Ayuthia:

Thanks a lot. I'll try and give a feedback. Especially the hp-thread looks promising. Didn't find it yesterday!

Ann

---

### Post by annuzzer on 2007-11-07
@ Ayuthia:

First of all: once again a big Thank You! for your hints. Unfortunately they didn't work and in the time  since (I didn't spend deedless) my innumerable searches for another way to get Gutsy started haven't opened out to any solution.

I'm not a clinger to conspiracy theories so that I'm at least not sure if [these statements](http://ubuntuforums.org/showthread.php?t=582220) get the point but the way the Ubuntu-people take is a mystery to me. The last issue of Ubuntu that worked on my laptop was 6.10 and against the above cited statement in this forum and the legion of comparable ones on the w3 it'll probably be the last.

Ann

---

