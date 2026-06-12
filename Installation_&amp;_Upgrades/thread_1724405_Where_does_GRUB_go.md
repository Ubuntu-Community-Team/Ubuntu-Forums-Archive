---
title: "Where does GRUB go?"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by yanom on 2011-04-08
I'm just curious... when you install dual-boot Ubuntu and Windows, does the Ubuntu Installer put GRUB on the Master Boot Record, or on the linux partition that Ubuntu lives on?

---

### Post by psusi on 2011-04-08
The MBR contains the very first part.  Another part, called the core image, is put in the unused space between the MBR and the first partition, and the config file and additional modules are in /boot/grub.

---

### Post by Rubi1200 on 2011-04-08
It is also possible and sometimes necessary, in certain scenarios, to install GRUB to a separate /boot partition.
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

But the method described by psusi is the standard way of doing things.

Installing to the root partition is not recommended.

---

### Post by yanom on 2011-04-08
I know that many distros (Slackware comes to mind) install to / partition.
Why is that bad?

---

### Post by Quackers on 2011-04-08
This is from a Launchpad bug report where somebody was questioning the warning you receive when trying to install grub2 to a root partition. The user had ignored the warning and installed grub2 to the root partition (which is quite commonly done, it seems).
The response quoted below is from Colin Watson (one of grub2's co-maintainers)
```
Well, it's correct - I think the warning is justified. Does GRUB work
for you for the meantime? If so, I don't really consider the warning a
bug since it points to a genuine unreliability in your setup that can
only be fixed by not doing this (for example, many kinds of filesystem
changes will make your system unbootable unlelss you run grub-install
again afterwards).
```

---

### Post by yanom on 2011-04-08
ok... so if the root partition gets messed up, GRUB fails also?

---

### Post by Quackers on 2011-04-08
I'm thinking that the root partition doesn't need to get messed up, possibly just filesystem changes could make the system unbootable.
I haven't used this method (except with grub legacy in other distros) so I can't give any definitive information.
It just seems that the advice of one of grub2's co-maintainers is to not do it. That's good enough for me :-)

---

### Post by psusi on 2011-04-08
Installing grub to a partition is unreliable because the boot sector has to encode the sectors where /boot/grub/core.img is located.  If that file gets moved ( think fsck or defrag or what have you ), then the boot sector can't find it, and you're screwed.

When you install to the MBR, the core is copied to the embed area after the MBR so it can't get bothered by normal filesystem operations.  Even if the core can't find /boot/grub, it can at least give you a rescue shell where you can possibly recover.

---

### Post by andrew.46 on 2011-04-09
> **yanom said:**
> I know that many distros (Slackware comes to mind) install to / partition.

Slackware gives the *option *of installing the bootloader to the MBR or the root of a partition. The default bootloader is lilo btw, although grub is available in /extra.

---

### Post by Quackers on 2011-04-09
> **andrew.46 said:**
> Slackware gives the *option *of installing the bootloader to the MBR or the root of a partition. The default bootloader is lilo btw, although grub is available in /extra.

Is that grub legacy?

---

### Post by andrew.46 on 2011-04-09
> **Quackers said:**
> Is that grub legacy?

It is grub 0.97:

[http://slackware.osuosl.org/slackware-current/extra/grub/](http://slackware.osuosl.org/slackware-current/extra/grub/)

---

### Post by Quackers on 2011-04-09
Yes, that's grub legacy. In my travels it seems that many other distros still use grub legacy. I have grub legacy installed to the root partition of several distros, so that I can keep grub2 from my Natty installation in control of booting.

---

### Post by andrew.46 on 2011-04-10
Mind you now I dig a little deeper I can see grub 2 for Slackware here:

[http://slackbuilds.org/repository/13.1/system/grub2/](http://slackbuilds.org/repository/13.1/system/grub2/)

This is a semi-official repository of Slackware build scripts. Mind you I suspect most Slackware users are more than happy with Lilo :)

---

### Post by Quackers on 2011-04-10
Aha! It seems to be a rare option (grub2 with other distros). Thanks for the info :-)

---

