---
title: "Just Reinstalled, now can only access NTFS as root"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by NMUrugbysteve on 2005-11-18
Hey all, I just got bored and fed up with the amount of junk i was piling up in my Ubuntu installation so I did a reinstall. In the partitioning section of the installer i mounted my NTFS drive as /Windows. Now I can only access this as root and I can't chown it because it tells me its a read only drive. Anyone know how to fix this?

---

### Post by taurus on 2005-11-18
You can change the permission in /etc/fstab!!!  What does your /etc/fstab currently say?  Maybe you want to add "umask=0" to the field before the last two zeros...

---

### Post by NMUrugbysteve on 2005-11-18
Wow, this makes me feel like a dolt, because i've done this like 6 times and just didn't think of doing it this time. Thanks a lot!

---

