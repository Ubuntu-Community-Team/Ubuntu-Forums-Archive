---
title: "Xubuntu reinstall broke"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by CrunchaliciousCaptain on 2007-11-09
I successfully installed Xubuntu 7.04 on an old computer(P3@500MHz with 128MB RAM) to dual boot with XP on GRUB.  When 7.10 came out, I started to download it via download manager and went to bed.  The next morning when I woke up, I had a "Failure to verify login" error message that kept popping up after I hit ok.  I rebooted, and logged in just fine.  For some reason, the update deleted my network settings, and I couldn't figure out how to fix it.  So I decided to reinstall from a 7.10 from a fresh CD and just overwrite the existing partition.  The process went smoothly, until about 60% of the "installing base system" part.  I got an error message that said something like "There was an error while installing initramfs-tools package.  Check /var/log/syslog."

Then it gave me a menu that let me pick and part of the instalation.  So I jumped to the Install base packages step.  It got to about 83% and just froze.  I hit ctrl+alt+delete for some reason, and the screen says "sending sigkill to all processes ... Please standby while rebooting the system"
The system reboots, and loading hardware drivers step fails.  The screen fills up with an error message, and becomes unresponsive.  Safe mode boot up does the same thing.  Right now I'm running  a memtest, I'll post my results later.

---

### Post by Pumalite on 2007-11-09
You probably have integrated graphics eating at your RAM, so you might not have enough to run Xubuntu 7.10. Please correct me someone if I'm wrong.

---

### Post by CrunchaliciousCaptain on 2007-11-11
You obviously don't understand.  THe system requirements from 7.04 to 7.10 have not changed, and Xubuntu worked after I upgraded it.  I'm asking what the problem is now.

---

### Post by Pumalite on 2007-11-11
Obviously you are in 'limbo' now with your system due to an incomplete upgrade. I'd recommend saving /home and data and do a clean install of a light Desktop.

---

