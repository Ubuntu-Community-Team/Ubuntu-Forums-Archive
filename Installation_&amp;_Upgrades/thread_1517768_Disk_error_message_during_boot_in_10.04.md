---
title: "Disk error message during boot in 10.04"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by bughound on 2010-06-25
After updating my motherboard BIOS, I'm now getting these error messages every time I boot up:

[   16.157447] ata3.00: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6
[   16.157488] ata3.00: failed command: SET FEATURES
[   16.157525] ata3.00: cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 0
[   16.157526]          res 51/04:fe:00:00:00/00:00:00:00:00/40 Emask 0x1 (device error)
[   16.157592] ata3.00: status: { DRDY ERR }
[   16.157623] ata3.00: error: { ABRT }
[   16.157661] ata3: hard resetting link

I've got a 200GB hard drive, using an ECS SiS 755 A2 motherboard w/1.1b BIOS.

Anyone know how to cure this?

---

### Post by bughound on 2010-08-19
I root-caused this to some sort of issue with the released version of hdparm (9.15 at the time of this posting).

After manually upgrading hdparm to 9.27, this message no longer appears during boot.

32 bit: [http://packages.debian.org/squeeze/i386/hdparm](http://packages.debian.org/squeeze/i386/hdparm)
64 bit: [http://packages.debian.org/squeeze/amd64/hdparm](http://packages.debian.org/squeeze/amd64/hdparm)

---

