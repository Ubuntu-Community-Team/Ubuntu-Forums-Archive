---
title: "Safe way to dual boot Ubuntu 10.04 &amp; Windows 7"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by SaberCat on 2010-10-06
After reading about the major changes in the new GRUB2 I decided not to risk installing 10.04 on my then existing computer. It was set up to dual boot 8.04 and Windows XP, and since I was two generations behind on both of them (and the computer was old), I decided to start over from scratch with a new machine. So I threw some money at the problem in order to avoid bigger problems.

I purchased a Dell Inspiron 570 (~$500) which came with Windows 7 on a SATA hard disk. I also purchased another SATA hard disk (320Gb, ~$50). I opened the 570 and moved the SATA DVD drive from port SATA1 to SATA2 and the Windows drive from SATA0 to SATA1. Then I installed the new SATA drive and plugged it into SATA0 (the primary master).

Then I installed Ubuntu 10.04 from a live CD (downloaded previously from the Ubuntu site and installed on a CD). It installed on the new drive with no problems. Then, when I rebooted, the boot choice screen had entries for booting both Ubuntu 10.04 and Windows 7. Both worked as expected.

I assume that the Windows disk was not touched in this process and that I could go back to the original (shipped) configuration if I wanted to. I haven't tried this...

I hope this is helpful to you...

---

### Post by andrewthomas on 2010-10-06
> **SaberCat said:**
>  SATA0 (the primary master).

Primary master?  I don't believe there exists any such thing concerning SATA.

---

### Post by wilee-nilee on 2010-10-06
Never hurts to be cautious, but millions of us have no problems. Check your information sources for bias.

---

### Post by oldfred on 2010-10-07
I think my system calls the Boot drive primary master even though it is SATA, but has IDE/PATA ports.

Primary master of course refers to IDE/PATA drives and BIOS that could only boot the primary master.

---

