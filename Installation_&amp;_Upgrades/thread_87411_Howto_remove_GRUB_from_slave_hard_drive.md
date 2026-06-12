---
title: "Howto remove GRUB from slave hard drive"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by stoleyourbike on 2005-11-08
[edit: it turns out this problem could be solved simply by restoring the bios to its default settings. Yay.]

This is kind of complicated:

To try linux out, I installed Kubuntu 5.10 into an external USB drive, using a walkthrough I found on these forums, and it worked great.

However, my desktop does not support booting from USB. So, I took the IDE HD with Kubuntu on it, installed it as the slave on my PC, and formatted it so I could reinstall Kubuntu and have a sweet dual-boot setup.

The problem is that since I installed the external HD internally and formatted it (using XP), I can no longer boot from CD. Thus, I cannot remove GRUB from the MBR of the now-slave HD using fixmbr and reinstall Kubuntu from CD (I told you this was complicated).

Is there a way to fix this using Windows XP, given that I can"t boot from CD, and this PC does not have a floppy drive? (I do not mind paying for software if that will solve the problem.)

I appreciate that this is a uniquely stupid situation; nonetheless, I"d be grateful for any help.

---

