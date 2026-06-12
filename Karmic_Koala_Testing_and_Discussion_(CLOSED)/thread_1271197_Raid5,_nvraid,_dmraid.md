---
title: "Raid5, nvraid, dmraid"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by seamuso on 2009-09-20
My original post on this would be feeding mis-information after the updates that I installed today. After I installed the updates and rebooted, my raid5 was no longer detected. I reverted the scripts I had previously modified so they were defaulted back to original as installed by the dmraid packages, rebooted again and my raid was detected and mounted correctly.

---

### Post by whoop on 2009-09-20
> **seamuso said:**
> There's still a typo in the 2 scripts that dmraid uses to detect arrays -

/sbin/dmraid-activate
/usr/share/initramfs-tools/hooks/dmraid

out of the box (fresh install, alpha6)


/sbin/dmraid-activate - line 55

should be
```

modprobe -q dm_raid45

```


/usr/share/initramfs-tools/hooks/dmraid - line 23

should be```

force_load dm-raid45

```


I just got around to setting up raid5 on my desktop system and ran into this a couple of days ago with Jaunty. Hope this helps anyone else who might be having issues with their dmraid setup.

Is there already a bug-report on this? If not, did you file one?

---

### Post by seamuso on 2009-09-20
> **whoop said:**
> Is there already a bug-report on this? If not, did you file one?

There is a bug report on this, but I believe it's still just for Jaunty. I only thought to look for this in the scripts because I had fought this beast a couple of days ago.

I list nvraid in the title, but it's probably affecting anyone who is trying to setup a fakeraid with dmraid.

---

