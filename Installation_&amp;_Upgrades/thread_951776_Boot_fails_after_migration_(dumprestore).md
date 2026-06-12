---
title: "Boot fails after migration (dump/restore)"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by udippel on 2008-10-18
I need to move my install from one SATA drive to the other. Over the years, I came to appreciate dump and restore for this purpose. So I did here, from first to second SATA drive. I even plugged the second drive as first for the reboot, but still it won't boot; it will fail at some kernel boot point, after grub has done the job (so it seems) and the drive is detected,
with these last three lines:
sd 2:0:0.0: [sda] Attached SCSI disk
sr 0:0:0:0: Attached scsi generic sg0 type5
sd 2:0:0.0: Attached scsi generic sg1 type0

and then everything stops.

How can I remedy the situation?

Uwe

---

### Post by udippel on 2008-10-26
Of course, the silly UIDs ...

I do understand the philosophy behind UIDs; and nevertheless it took me simply too long to find out that the UIDs are not only in /etc/fstab, but also in /boot/grub/menu.lst. And the whole thing does not boot.

As a server person, and as someone who installs from 'alternate', I would not want UIDs to happen. I need to simply 'rsync' or 'dump'. 

There is a whole lot of ways to remedy the situation, one of them would be a program to move entries in menu.lst and fstab forth and back. Another one would be for grub to interactively ask where it is going. As of now, the kernel pops. grub could just as well point out the mistake if the UID is unavailable, and even the kernel might be doing so. Even the 'mount -a' might be willing and clever enough in 2008 to ask for the devices instead.

'Solved', but not all in order and not all too good.

Uwe

---

