---
title: "grub install fatal error"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by starman38 on 2007-06-23
I'm trying to install grub on my / partition, /dev/sda9, but at 93% complete get a fatal error, can't install grub on (hd0,9).  I' m not sure if I am denoting the location of the sda9 logical partition correctly in grub talk.   I have a Dell Inspiron 9300 with 1 physical hd.  I use BootitNG to boot to Win xp, Xandros, and am trying for Ubuntu.  XP is on hd0,0 and Xandros is on sda7 but  uses lilo.  On the final window before the installer writes I press the "advanced" button and change the default grub install location from (hd0) to (hd0,9).  Is this correct?  I'm no expert but have rtfm.  Thanks in advance for any light you can shed.

---

### Post by merlinus on 2007-06-23
IIRC, numbering for these things begins at zero, so (hd0,eight) would be correct.

Use numbers, not text, for eight.  My html settings turned the 8 into a smiley....

-merlin

---

### Post by starman38 on 2007-06-25
Thanks Merlinus, that was the answer, duhhhh!:popcorn:

---

