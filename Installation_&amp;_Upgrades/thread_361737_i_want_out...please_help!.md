---
title: "i want out...please help!"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by tr86 on 2007-02-14
long story short - xp imploded, so, in a fit of rage, i installed ubuntu 6.10 edgy eft as the sole OS on my machine (hp zd8000).  after a day of poking around, i want out.  i've grown lazy over the years, and want my buggy, yet comfortable, xp environment back.  now, here's the situation:

i have (1) internal IDE 100GB HD
i have a bootable XP cd that GRUB will not let me boot with
i have no idea how to run a cd out of ubuntu

i'm linux stupid, and i apologize in advance for being a burden.  i've already visited the following threads, and nothing seem to apply to my situation, since windows resides nowhere in my system currently, and i'm only running one HD:

[http://ubuntuforums.org/showthread.php?t=342663&highlight=uninstall+edgy](http://ubuntuforums.org/showthread.php?t=342663&highlight=uninstall+edgy)
[http://ubuntuforums.org/showthread.php?t=341933&highlight=uninstall+ubuntu](http://ubuntuforums.org/showthread.php?t=341933&highlight=uninstall+ubuntu)
[http://www.ubuntuforums.org/showthread.php?t=357199](http://www.ubuntuforums.org/showthread.php?t=357199)
[http://ubuntuforums.org/showthread.php?t=361123&highlight=uninstall](http://ubuntuforums.org/showthread.php?t=361123&highlight=uninstall)

i'm assuming that i should try super grub disk, but i need to know for sure, so i don't worsen my situation.

please help....please.

---

### Post by KAL9000 on 2007-02-14
go into Bois and make your CD drive the 1st boot device. then it will look at the CD before grub even gets a chance to but in.

---

### Post by oilchangeguy on 2007-02-14
make sure the bios is set to boot from the cd drive. and you should have no problem. have you ever done an xp install?

---

### Post by tr86 on 2007-02-14
> **KAL9000 said:**
> go into Bois and make your CD drive the 1st boot device. then it will look at the CD before grub even gets a chance to but in.
i've already tried that...the ubuntu disc will boot, but not either of my xp discs.  thank you, though...i'm aware that the CD may be the actual problem, also.

---

### Post by javaJake on 2007-02-14
XP disks? What kind of disks are they? Are there any instructions about how to use them?

**Edit:** If, uh, this doesn't work, just get Vista - it's the best version of Windows yet IMHO (and let's not start a discussion about that).

---

### Post by KAL9000 on 2007-02-14
If its a prebuilt system are you sure your using a proper recovery CD (the 1st bootable one) not one of the other data ones?

Try making the CD drive the ONLY boot device. it should work...

---

### Post by tr86 on 2007-02-14
> **javaJake said:**
> XP disks? What kind of disks are they? Are there any instructions about how to use them?

**Edit:** If, uh, this doesn't work, just get Vista - it's the best version of Windows yet IMHO (and let's not start a discussion about that).
ahem...they're CDs of "questionable origin" - i.e., i have no idea where my recovery disk is and burnt my own.  have any tips on burning bootable cds?

---

### Post by tr86 on 2007-02-14
> **KAL9000 said:**
> If its a prebuilt system are you sure your using a proper recovery CD (the 1st bootable one) not one of the other data ones?

Try making the CD drive the ONLY boot device. it should work...
does it matter who built the machine? as long as its xp OEM, it should work...right?

---

### Post by oilchangeguy on 2007-02-14
yes, if you can, get a restore disc from a friend who has the same model computer as yours. or a windows xp only disc. has to match your version (home or pro), and use your product key.

---

### Post by KAL9000 on 2007-02-14
I was thinking if he had a prebuild system then the OEM recovery CD's need to be in the right order.

If its just a normal XP boot disk then it should work regard less of the system model.

I can imagine if its a recovery disk for the wrong model system then it wouldnt work but I would expect it to tell you about it and not just ignore it.

Try to get hold of a different OEM CD if you can just to test if it will boot and narrow it down to a problem with that CD.

---

