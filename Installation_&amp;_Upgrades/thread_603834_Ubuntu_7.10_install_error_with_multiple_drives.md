---
title: "Ubuntu 7.10 install error with multiple drives"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by thechump on 2007-11-05
At the end of the install, grub is instructed to use (hd0) as the drive to write boot info...
However, it wants to use hd4  instead (I have 5 drives in the system).  As a workaround,
I gotta mount and edit the grub config from LiveCD to point it at the right drive.

FYI, I'd assume that HD0 should be the same as what Windows XP recognizes as the
first drive.  My other 4 drives are part of a NTFS RAID on the Windoze side attached
to a different controller.

---

### Post by mrvertigo on 2007-11-05
are you mixing scsi and ide drives?

---

### Post by thechump on 2007-11-05
No, not mixing.  All my drives are SATA.....also, although the RAID is configured and controlled from the motherboard (Asus A8N), it's actually a soft raid.  Ergo, Linux is actually seeing 4 individual drives on
that controller.

---

