---
title: "Boot from CD (ubuntu already installed)?"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by pokerFace12344321 on 2008-01-12
Background:
I recently installed Ubuntu 7.10 Desktop x64 using a CD I burned.
The installation went well, but now I want to reinstall Ubuntu.


Problem description:
I don't know how to boot from the CD.
Each attempt goes straight to the installation already on the hard disk.


Failed Attempts:
1) Put CD in, shut down, then restarted. Result: skips CD and goes boots from hard drive.
2) Set my BIOS settings so the primary boot drive is the CD. Result: skips CD and goes boots from hard drive.

Relevant Details:

All relevant components are new and seem to be working well:
Motherboard: Abit IP35 Pro
CPU: Intel Q6600
CD-drive: Samsung SH-203N (SATA)
Hard drive: Seagate 250G - ST3250310AS (SATA)

This computer is dedicated to Ubuntu and does NOT have any other operating systems on it (no dual boots; nothing complicated).

I am brand new to Ubuntu -- been using it for no more than 24 hours.
There must be something simple I'm missing.

Thank you for your help,
- frustrated ubuntu newbz0r

---

### Post by MobiusNZ on 2008-01-12
Maybe the CD is damaged? Check it for dust, scratches etc that could stop it from being read.

---

### Post by pokerFace12344321 on 2008-01-12
The CD doesn't appear scratched or damaged. In the meanwhile I tried another boot CD (the alternative, text-based installation CD) and have the same result.
I tried the CDs on another computer and the data is visible -- so they're not damaged.
Also, when I boot up the computer, the CD icon is sitting on the Ubuntu desktop. So I know that the CD drive works in the target computer and it can read the CDs without any problems.

I believe the installed Ubuntu takes control. Is there a way to interrupt the loading of this Ubuntu and boot from the CD manually? Possibly through some GRUB command or something?

---

### Post by MobiusNZ on 2008-01-12
Ubuntu can't "take control" until it is booted by your bios. Double check your bios boot order settings.
How did you do it last time?
Also I think CD booting is something grub is working on, but not available yet.

---

### Post by pokerFace12344321 on 2008-01-12
Somehow, the issue resolved itself.

My guess is there was some bug in the BIOS that was corrected by resetting.

I left the computer off overnight, reset the BIOS (the motherboard provides a switch to make this easy), and tried it again this evening. It worked.

I wouldn't have run into this problem on the first installation since the hard drives were blank so the only option to boot from was the CD.

Sorry for the commotion; frustration blows problems out of proportion.

---

### Post by pokerFace12344321 on 2008-01-13
Update:

After trying different settings, I realized that switching the SATA controller to AHCI instead of IDE in BIOS will cause the problem.

In efforts to optimize my system, I changed it to AHCI from the default setting which is IDE after the first installation. Resetting the BIOS changed it back, which is why I finally got it to boot from the CD.

Mystery solved.

---

