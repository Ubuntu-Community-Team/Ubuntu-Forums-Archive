---
title: "SRST failed (errno=-16) on installation attempt."
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by klanspar on 2008-10-31
I'm trying to install 8.10 from the live cd but not having much luck. I keep getting a "SRST failed (errno=-16)" early on in the install. It also says something about BusyBox. From what little I have been able to find on this it sounds like a SATA driver issue.

---

### Post by 7Sasha on 2008-10-31
try switching in tho BIOS the IDE settings to be RAID

---

### Post by klanspar on 2008-10-31
Thanks for responding. That allowed me to install it. After installation it won't load the grub though. It says something about Media Failure. This error just keeps repeating. I was in a hurry to get back to work so I didn't have long to look at it, but I'm assuming it's the NVIDIA chip set driver complaining about something.
Can you offer any insight on why the change you suggested allowed the installation process to complete?

---

### Post by bjnueva8623 on 2009-02-06
Sorry for bumping this old thread, but I am having the same issue. During installation, I kept getting the "SRST failed (errno=-16)" message. Thats as far as I've been able to get. I've also tried switching the IDE settings to RAID, but that didn't work. 

My system specs:

Pentium 4
2.80 GHz
1 GB of RAM
300 GB HDD
NVIDIA 6600 series

I believe I lost my HDD as well as my WinXP OS. This is extremely upsetting and I'm relatively new to this. Hope someone can help out.

---

### Post by dev-044 on 2009-03-06
Hi 

"SRST failed (errno=-16) on installation attempt."

I had similar problem 
I got is solved by moving HD from secondary to primary slot.
and then i got it resolved.
now I can able to install ubuntu.
I hope it will help you too.

---

### Post by Scott Macdonald on 2009-04-25
Hi,

I solved my problem similarly on a fresh Jaunty Jackalope installation by swapping my boot hard disk to be the IDE primary master instead of the primary slave.

Is this a bug?

Cheers,

Scott

---

