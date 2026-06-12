---
title: "Ubuntu 12.04 LTS CD does not boot after Windows XP PRO SP3 installed"
date: 2013-12-26
forum: Installation &amp; Upgrades
---

### Post by roadrawts on 2013-12-26
Was running Ubuntu 12.04 LTS on 32 bit Dell Dimension (older pc) without problems.  The only OS on the machine.  Needed to convert machine to a dual boot with Windows XP.  So blew away the partitions and started over.  Installed Windows XP with SP3 as the only OS but with plenty of unpartitioned space left for Ubuntu.  Now Ubuntu CD won't boot.  Always restarts Windows XP, which runs fine. All other CD's, i.e. GPARTED, Boot Repair, etc. will boot from the CD. Therefore, the boot sequence of CD first is working. Reimaged the .iso and tried it again but still no help.

Any ideas?  Need to get this as a dual boot with both Windows and Ubuntu on the machine.

Thanks.

---

### Post by mörgæs on 2013-12-27
Are you able to boot the [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD")?

---

### Post by roadrawts on 2013-12-27
No.  With the DVD in the drive nothing happens.  I did see another post about the boot manager and boot.ini files being controlled by Windows.  The curious thing to me is that I can boot GPARTED and other programs, but not Ubuntu.

---

### Post by mörgæs on 2013-12-27
You don't need a DVD for the minimal ISO. A CD is better (and best is a single-use one).

Did you try booting from USB?

---

### Post by roadrawts on 2013-12-27
BIOS doesn't support booting from USB.  Only choices are floppy, CD, or HDD.  I'm trying Ubuntu server instead of desktop now.  The CD spins but nothing happens.  Very frustrated.

---

### Post by roadrawts on 2013-12-27
I downloaded Ubuntu 10.10 iso and it is able to boot.  But not 12.04.03.  Don't know what the differences are.  My plan now is to use 10.10 to upgrade into 12.04 through whatever steps I have to take.  Any other suggestions?

---

### Post by mörgæs on 2013-12-28
Yes, see post #2.

---

### Post by roadrawts on 2013-12-28
Installed ok with mini.iso.  Thank you.  One question.  Should I have selected the mount point as / for root  or boot?  I selected /.  Hope that's correct.  At any rate, thanks for your help.

---

