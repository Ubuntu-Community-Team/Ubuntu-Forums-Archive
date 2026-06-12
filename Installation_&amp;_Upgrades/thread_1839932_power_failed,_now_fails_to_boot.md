---
title: "power failed, now fails to boot"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by jimfl on 2011-09-06
Had a brief power failure (I was running a VirusScan at the time). Now I can't boot into Maverick 10.10. (I also tried using Recovery Mode and earlier versions). All of them displayed these error messages:
mounting /sys on /root/sys failed:  No such file or directory
mounting /proc on /root/proc failed:  No such file or directory
target file  system doesn't have requested /sbin/init

I am able to boot into Ubuntu from a removable drive (which has an earlier version--I think 9.10) and a LiveCD, version 10.10.

HELP!  :sad:

Thanks,
Jim

---

### Post by sanderd17 on 2011-09-06
Can you give us the output of this boot info script?

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

And are you using Wubi or a regular dual boot?

---

### Post by drs305 on 2011-09-06
It's possible your filesystem was corrupted by the power loss.

From the LiveCD you could mount the Ubuntu partition and run an fsck check. The Ubuntu partition must be unmounted. Here is what I normally use. Change the XY values to those of your Ubuntu partition:
```
sudo mount /dev/sdXY /mnt
sudo e2fsck -fvy /mnt
```

---

### Post by sanderd17 on 2011-09-06
follow DRS305, he has more knowledge on it.

---

### Post by jimfl on 2011-09-07
An enormous Thank You and drs305 and sanderd17. I'm back in business!!!:smile::smile::smile::smile::smile:

---

