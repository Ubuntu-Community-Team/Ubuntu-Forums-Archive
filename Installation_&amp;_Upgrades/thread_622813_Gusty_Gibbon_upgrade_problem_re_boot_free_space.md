---
title: "Gusty Gibbon upgrade problem re /boot free space"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by GraemePerrins on 2007-11-25
Hi, when I tried to upgrade from Fiesty to Gutsy the installer gives an error saying my /boot partition is short on space, see log file extract

main.log:2007-11-10 23:57:59,388 DEBUG dir '/boot' needs '178257920' of '<DistUpgradeControler.FreeSpace object at 0xa67c28c>' (23623680.000000)
main.log:2007-11-10 23:57:59,388 ERROR not enough free space on /boot (missing 155M)

I know there have been similar problems in the past and have seen suggestions ranging from:
1. resize and extend boot partition, (don;t really want a 155M+ /boot partition)
2. move /boot to the root / partition
3. edit the DistUpgradeControler script to ignore the free space check
4. re-install from scratch (this would be a MS type upgrade process)

Really expected this to be corrected in Gutsy by now. As I want a low-pain option to upgrade what have other people done in this situation ? Is there an approach proven to work.

Regards,
Graeme Perrins

---

### Post by lodp on 2007-11-30
I'm in the same position right now, wasted the whole day trying to get this upgrade done.

I tried increasing the free space on /boot, but as usual qtparted craps out on me and I can't do it. Plus for some reason the laptop won't boot from CD anymore (at least not from any relevant CDs - XP CD boots fine), so there's no chance I'll get the boot partition extended.

What about the other options? 

How do you move the boot partition to the main partition (and still have GRUB load on boot)?

If I edit that script to omit the free space check -- won't i run into trouble at some point (if there really IS to little space for an installation)?

I'm pretty much stuck here -- I can't even do a re-install from scratch, as the CD won't boot..

**EDIT: **I was able to increase the space on the boot partition after all, but only after I had downloaded the Kubuntu DVD, which finally did boot. Did it in Qtparted then, took ages.
But apart from the episode with the boot partition, the upgrade went through surprisingly smooth (even with my proprietary ATI graphics card driver). I say 'surprisingly' because I read about so many people having problems here on the forms..

---

### Post by jfenwick on 2007-12-03
I'm have the same problem.

Is there any other way besides resizing the partition? I already deleted all the old kernels and related files in the directory, it's down to the bare minimum!

---

### Post by lodp on 2007-12-08
i don't think there are, except for the ones that are mentioned in the first post. 

why don't you resize the partition though? i couldn't at first because i would have had to do this with qtparted on a live cd, and that cd wouldn't boot. but if you don't have that problem, i'd just resize it, i'm sure it's the fastest way to deal with this.

---

### Post by sgeoxd on 2007-12-08
155+MB does seem high for a boot partition...to me anyway...

Just a random thought, but is the boot partition ext2 or ext3. I've seen problems using ext3 on a boot partition. Although you did get it up to begin with but may not hurt to format the boot partition via the install, reboot, and try again (as is).

---

### Post by jfenwick on 2008-02-13
It turns out that you can't delete old kernels manually. You have to delete them through apt-get. So remove all your old linx-image packages and you should be all set the next time you upgrade.

---

