---
title: "HP Pavilion P2-1013W - Cant Complete Installation"
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by mykrob on 2013-11-18
I was given an HP Pavilion P2-1013W. Not my first choice in hardware but I figured it'd be fine for the kids for doing papers and things for school.
Went to installation 13.10 on it. The installation goes fine until a certain point, then it just hangs. No clue what part of installation triggers it because it freezes at a random spot each time.

I have tried from Live CD mode and well as Install mode, and get the same results. Doesn't look like the alternate installer exists anymore.
Going to run a memory test on the PC and make sure thats okay.

In the meantime, what can I do to get this to work?

Thanks,
-myk

---

### Post by fantab on 2013-11-18
Is there any other OS in the Pavillion? What graphics do you have in there?

Did you do a MD5Sum Check on the downloaded Ubuntu.iso? Have you tried re-burning the .iso to the DVD/USB?

---

### Post by mykrob on 2013-11-21
Got it resolved. Had to format the hard drive outside of installation. I think the EFI partition was giving Ubuntu (and Linux Mint) a hard time. It was freezing at Grub installation.

---

