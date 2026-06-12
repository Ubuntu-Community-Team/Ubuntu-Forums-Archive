---
title: "Really unnecessary installation trouble"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by SRTS on 2006-06-15
Hi, I'm using Suse 10.1 and was just going to try out Ubuntu 6.06.
However, I encountered relatively silly troubles which I can absolutely not understand neither tolerate. And those are *drumroll*:

1) startup screen doesnt fit on the screen.. some text for F-key options is outside and i discovered it just by chance when i hit the F keys..

2) graphical installer doesnt give me a choice for filesystem.. just wants to format with ext2fs (I'd like a journaling fs though).

3) text installer gives FS choice, but tries to contact all repositories before even asking me to configure my dsl connection.. what the heck.

4) correctly detects my other OSs, and writes the bootloader to the MBR...to the wrong disk! I got 2 old ide drives + 1 sata drive, and the / partition was even on the sata drive, so why does it write the bootloader to a wrong ide disk. Maybe if it cannot recognize it automatically, it could just give me an option to specify a hdd at least?

5) Well, and i wonder why the resolution was limited to 1280x1024 (using 1600x1200 hardware resolution on this TFT).

really, some people appear to have not thought a lot. Sorry, this had to be said.
Well, back to Suse 10.1 for now.

---

### Post by Mr Green on 2006-06-15
#1 is solved by running safe graphics mode or something.
#2 I don't understand, I ran the graphical installer and I formatted with ext3.

No idea about the rest. Enjoy your Suse!

---

