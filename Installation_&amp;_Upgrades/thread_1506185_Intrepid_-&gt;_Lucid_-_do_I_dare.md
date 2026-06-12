---
title: "Intrepid -&gt; Lucid - do I dare?"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by jolindbe on 2010-06-10
Hi!

I have been running Intrepid for a year and a half, and it is mostly running smoothly, even though I am still quite much of a newbie to Linux. As I am an astronomer, I have lots of funny software which different people have helped me to install - usually these installations have been tricky processes taking an hour or two for an experienced user, and this is nothing that I could repeat myself. (If it is relevant, the programs are Iraf, Miriad, DS9, xs, ...)

However, I have recently bought a mobile internet device, which does not work in Intrepid (it is a Huawei E122). When running the Lucid Live CD it works just out of the box without problems. Because of this, I am considering to upgrade.

The problem is that I am afraid that some/all of the programs mentioned above will not work after an upgrade. I don't really know how to test it, since they need different shells/terminals that I cannot install from the Live CD (csh, xgterm, tcsh, etc).

So my questions are:
Can you find out a way to test these programs without making any changes to my system?
Can I backup my system so I can restore it completely in case an upgrade messes things up (my /home folder is on a separate partition, if that helps)?
Would you recommend an upgrade (Intrepid->Jaunty->Karmic->Lucid) with my current situation?

Thanks a lot for any help!

---

### Post by dino99 on 2010-06-10
you can upgrade from:

- previous to next
- LTS to LTS

you can test with a cd or usb (unetbootin) defore installing on hdd
clonezilla or other backing tools are ok, but as you have a /home (if you dont format it of course) your data are safe

---

