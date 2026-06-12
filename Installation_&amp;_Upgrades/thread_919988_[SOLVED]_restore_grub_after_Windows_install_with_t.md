---
title: "[SOLVED] restore grub after Windows install with two hard drives"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by benbelly on 2008-09-14
I have two hard drives, one running Windows Vista, and the other running Ubuntu 8.04.  Until this weekend, the first drive was running XP (I know, I know - the curse of the gamer), but that got messed up with SP3 so I decided to slap Vista 64bit on there (I get it free through school, I didn't pay for it, I swear).

  Now I need to restore grub.  The MBR would be on hd0, right?  And the grub menu itself on hd1?  Or am I mixed up?  I have the live CD ready to go, but I don't know what to tell grub to do.

-Ben

---

### Post by caljohnsmith on 2008-09-14
OK, from your Live CD try:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit
```
That should work, but let me know if you run into any problems.

---

### Post by benbelly on 2008-09-15
> **caljohnsmith said:**
> That should work, but let me know if you run into any problems.

That did it!  Great.  Thanks so much

-Ben

---

