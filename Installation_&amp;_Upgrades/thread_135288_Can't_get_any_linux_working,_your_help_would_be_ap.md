---
title: "Can't get any linux working, your help would be appreciated."
date: 2006-02-23
forum: Installation &amp; Upgrades
---

### Post by event on 2006-02-23
I've tried Ubuntu 5.10, SUSE 10.0, Mandrake 10, and Knoppix but still can't get linux working. Ubuntu, SUSE, and Knoppix all freeze after the boot/install prompt, while Mandrake 10, being so old didn't have my ULi M1575 SATA controller drivers. I was thinking it was because I had an X-Fi card installed, so I removed it only to get the same problem. I tried installing with ACPI off and did safe install in SUSE, but had no luck.

I have an ASUS A8R-MVP with ATI Radeon Xpress200 Crossfire northbridge and ULi M1575 southbridge, 2GB RAM, single ATI X1800XL, Athlon 64 3700+ San Diego, and a Maxtor MaxlineIII 250GB SATA HDD.

Could it be that my chipset is too new? Are there any newer versions of distros that have support for the ATI Chipset?

It seems to pass linux tests, which gives me some hope: [http://www.linux-tested.com/results/asus_a8r-mvp.html](http://www.linux-tested.com/results/asus_a8r-mvp.html)

I appreciate your help.

---

### Post by LordBug on 2006-02-23
On the Ubuntu Live CD (I don't know the rest), you see "boot:" correct?  What happens, exactly, if you hit enter at that?

---

### Post by event on 2006-02-23
I'm not using the live CD, but yeah I do see the boot prompt. No matter what I choose, It freezes at the same point during hardware detection, the one after keyboard. If I could see what it is trying to detect, it would make my life easier, but I can't. :(

---

### Post by ssam on 2006-02-23
if your hardware is very new maybe the next version of ubuntu will support it. try booting the dapper flight 4 (alpha 4) [live cd]("http://cdimage.ubuntu.com/releases/dapper/flight-4/").

report bugs if it does not work

---

