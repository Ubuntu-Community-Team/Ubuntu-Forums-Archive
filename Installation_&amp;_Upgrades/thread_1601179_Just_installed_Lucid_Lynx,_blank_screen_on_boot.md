---
title: "Just installed Lucid Lynx, blank screen on boot"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by ideogon on 2010-10-19
I installed Lucid Lynx 64-bit right over a working Arch Linux installation (to my AMD64 system).  The Ubuntu Live CD works fine (even the network is detected!...using it right now), but when I boot from the disk that I installed Ubuntu onto, I get nothing at all after the BIOS prompt, except a blinking cursor...

I'm clueless now.  How should I proceed?

---

### Post by hwychld on 2010-10-19
I have been having similar trouble with the 32 bit version.  Try restarting the machine and press and hold the shift key just after the bios screen.

With any luck that will get you some Grub options.  I found that if I used the2.6.31-22-generic instead of the 2.6.31-25 that 10.04 would boot.  I have not figured out why 2.6.31-25 doesn't work yet, but at least I got it to boot.

---

### Post by RJARRRPCGP on 2010-10-19
> **ideogon said:**
> I installed Lucid Lynx 64-bit right over a working Arch Linux installation (to my AMD64 system).  The Ubuntu Live CD works fine (even the network is detected!...using it right now), but when I boot from the disk that I installed Ubuntu onto, I get nothing at all after the BIOS prompt, except a blinking cursor...

I'm clueless now.  How should I proceed?

You must wipe the HDD and try again. Looks like a corrupted MBR.

It almost never works right until you clear the MBR and partition table and start over. Sorry. :(

You must zero at least the first 32 KB of the HDD.

---

### Post by hwychld on 2010-10-20
Did you try holding the shift key?  If you get anything by doing that then it isn't a MBR problem.

---

