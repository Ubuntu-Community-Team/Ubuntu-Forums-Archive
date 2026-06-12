---
title: "NOTHING BUT TROUBLE so far with ubuntu"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by ivandrocco on 2008-10-10
I have a IBM Thinkpad t41 with a Radeon Mobility 7500 video card, this card seems to be the source of most of my problems.

I started with Ubuntu Hardy Heron, which froze regularly and was basically unusable. From there I switched to Xubuntu, with which I had the same problem. I tried changing the video drivers and a bunch of different things suggested in the forums, I even had Compiz working on Ubuntu, but it still froze randomly and often. From here, I decided to try Ubuntu 7.10 which I understood was more stable. Installation went great, until I removed the cd and rebooted the computer, I got the grub loading screen but after that NOTHING BUT BLACK. Ubuntu 7.10 will only run with the livecd, which is what I am using now. Please help me sort this out.

---

### Post by cilkay on 2008-10-10
Hit the escape key when you see the boot manager prompt and select "recovery mode". Select "xfix" and wait for it to finish reconfiguring X. Then select "resume normal boot" and you'll know soon whether it worked or not.

---

### Post by ivandrocco on 2008-10-13
When I go into recovery mode, it scrolls through a boot checklist and then ends in a command prompt. How do i select xfix?

---

### Post by cilkay on 2008-10-13
My instructions above were for booting from the disk. You seem to be doing something different. The "xfix" option is an obvious menu choice when you boot in "recovery mode" from the disk.

---

