---
title: "Ubuntu 6, GRUB Error 18, partitioning scheme - seeking confirmation"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by dogugotw on 2006-10-08
I recently had a HD failure so went out and bought a new 300 gig drive.  At the same time, I decided to switch from Mandrake to Ubuntu.  The PC is about 5 years old (HP) so as one might expect, after doing the install I got a GRUB Error 18.

I've read any number of posts on how to fix the problem but want to make sure I have the process right before starting.

Use expert mode for the partitioning.
Remove all partitions.
Create a smallish (I'll probably go 1 gig) partition labeled /boot
Create another small partition labeled / (I'll probably go 5 or 6 gig)
Create a swap partition (1 gig)
Create other partitions as desired.  I'll do a 5 gig partition for /tmp and another for /var.
If I'm ok to here, now I'm stuck again.  What is the remaining partition called?  /root or something else?

Thanks for any tips.

Doug

---

### Post by dogugotw on 2006-10-08
Sorry, forgot one other question.

If the Error 18 is related to the BIOS not being able to see all of the HD, does this mean I need to keep ALL partitions below the max for my BIOS or just the /boot partion?

Thanks.

Doug

---

