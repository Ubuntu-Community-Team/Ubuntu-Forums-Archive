---
title: "Installation failure."
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by igotmybfg on 2007-08-22
Hi,
I'm trying to install Ubuntu for the first time. I used RedHat a few years ago, so I have some linux knowledge, but I'm no expert. OK, hardware config:

Asus M2N32-SLI motherboard
Nvidia 590 chipset
AMD 64 X2 4200+ proc
RAID 5 array (Sil 3012 chipset)
Geforce 7950GX2 (2 of these in SLI)
Samsung DVD burner

If there's any other hardware info you need, just let me know. I've got Windows up and running on it, so that info is easily available.

Anyway, what happens is that I boot from the CD and get the ubuntu install/boot screen. I pick the run/install ubuntu option, and the kernel decompresses. The ubuntu logo comes up, the status widget goes back and forth. Then... nothing. Blank screen.

I can ctrl-alt-f1/2/3 to the console, which looks fairly normal and is responsive, but ctrl-alt-f7 just gets me a blank screen again. I've tried ctrl-alt-bksp to restart X, but that doesn't seem to do anything.

So it seems like everything up until X boots up fine.. is this an issue with my gfx card(s)? I did some searches for geforce 7950 GX2, but found little.

Any help would be appreciated... I'd really like to get back into the linux world!

---

### Post by Pumalite on 2007-08-22
Remove one card and see what happens. That will tell you if it's the SLI array or not. It could be a different hardware problem. Start eliminating possible causes.

---

### Post by igotmybfg on 2007-08-22
Some detail about the hard drive/raid layout:

I've got 6 400gb Samsung disks in a Raid 5 array, which amounts to about 1.9 TB usable space.

I've got Windows in the first 1.1 TB, leaving about 800 GB for the linux install (those 800gb are contiguous, but not explicitly partitioned or formatted).

---

### Post by Pumalite on 2007-08-22
Check into the Raid Array too.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

