---
title: "Possible bug installing on 2nd physical drive"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by TheTank on 2006-08-28
This seems like a bug:
I have a server set up with
IDE 1: CD-Rom & HDD 1 (20gig but might break soon)
IDE 2: HDD 2 (more or less reliable)

I tried installing vanilla debian and got the problem. Presumed it was a debian bug and tried ubuntu-server.
Same thing. :\

When installing the OS to the second phyiscal (hdd1) it was mapped to hd0, hdd2 -> hd1.
But grub is set to boot the first physical drive, i.e. hdd2 -> hd1.

I got it working by waiting for the system to go to grub, then temp edit the grub entry to hd0 then let it start.
When I got a console, not possible to change it before because I didn't have the rights, set it permanently with
```

sudo vi /boot/grub/start1

```

Note: Once I could not even get to grub because it was complaining about my file system. Shame on my I forgot what I had to do. (was happy to get it working in the first place)

---

