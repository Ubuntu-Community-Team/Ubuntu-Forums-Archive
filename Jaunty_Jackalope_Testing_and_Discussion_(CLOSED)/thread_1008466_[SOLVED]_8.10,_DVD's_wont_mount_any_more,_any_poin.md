---
title: "[SOLVED] 8.10, DVD's wont mount any more, any pointers. Works fine on testing Jaunty"
date: 2008-12-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-12-11
Suddenly it wont mount dvd's. Worked perfect before. nothing appears on desktop. Trying to play it with any media player gives errors.

VLC spits this out.
Playback failure:
DVDRead could not open the disk "/dev/scd0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/scd0'. Check the log for details.

If I reboot in Jaunty it plays fine and mounts as expected so no hardware failure.

---

### Post by LowSky on 2008-12-11
Phil check your /media folder you may be able to access the drive from there.
its not a fix but a workaround
EDIT:
whats the contents of
/etc/fstab

---

### Post by philinux on 2008-12-11
Nothing in media. First thing I checked.

I'd also checked fstab nothing to worry about there. 
```
UUID=3c1915c2-7f19-449d-9c12-ee8a2b6628cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I rebooted in Jaunty tested fine. Rebooted back to 8.10 with the disc still in and it mounted. :confused:

All I can think of is that its a resume from suspend issue. Sound also went squiffy. I'd suspended a few times. Oh well still bleeding edge then.

---

