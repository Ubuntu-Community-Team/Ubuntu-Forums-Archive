---
title: "how to create boot choice xp &amp; ubuntu"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by {RaW}ShrapNull on 2010-03-25
I tried searching forums before posting, but it was hard to search due to the specific nature of what I want to do.

I have one hard drive with windows XP on it. Another with Ubuntu. As it stands there is no link between them. Is it possible to create a dual boot using these disks? - I do not want to reinstall any of them.
Preferably, I would like the boot choice (or booter? - not really sure what I'm talking about) to be on the newer Ubuntu drive.

It is on an old machine with 256MB Ram. So slow in fact, I'm going to change the desktop environment to Xubuntu - but that's mostly irrelevant.

As I understand it, I should make the Ubuntu drive master, XP as slave... but then what?

Thanks in advance,
\m/ shrap

---

### Post by byStanderone on 2010-03-25
...is the xp on the first drive that you mentioned functional...and what flavor of ubuntu it is on the other drive?

---

### Post by {RaW}ShrapNull on 2010-03-25
The XP is fully functional & boots normally, as does ubuntu.
The ubuntu version is the latest (koala I think) 386.

Thanks for swift reply

---

### Post by Mark Phelps on 2010-03-25
OK, then all you should have to do is the following:
1) Boot from the Ubuntu drive
2) Once into Karmic, open a terminal and enter "sudo update-grub"

That should return entries in the terminal window for each kernel and OS it finds.

IF it works properly, it will generate a new GRUB menu, one that contains an entry for XP.

Once you reboot, you should be presented with a GRUB menu containing entries for all your Linux kernels and for XP.

---

### Post by {RaW}ShrapNull on 2010-03-25
Thanks a million!! Much appreciated. Trying to wean my in-laws away from XP to ubuntu while giving them a safety net!

This community is great.

Thanks again
Shrap \m/

---

### Post by {RaW}ShrapNull on 2010-04-25
Just an extra on this. I did what was recommended above, however when I tried to boot into windows I got an "error: invalid signature".

To fix this, in the terminal I typed: sudo grub-mkdevicemap
THEN typed: sudo update-grub

Just in case anyone runs into this error, this might help.

Thanks again all

---

