---
title: "Installation of 12.04 halts"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by poltr1 on 2012-06-10
I'm trying to install Precise (12.04) on a Compaq Presario M2000 laptop. It had been previously running Maverick (10.10) and XP in a dual-boot configuration, until last Monday.  Last week, I tried to upgrade it to Natty (11.04). It downloaded all the upgraded files and packages, but it froze up when it was installing them. I tried as many fixes as I could find, but nothing seemed to work.

And so I resorted to the brute-force-and-install-it-clean method: booted with my SystemRescueCD disk (a VERY handy disk to have), started a shell session, mounted the hard drive, and wiped the ext3 partition (/dev/sda1) via rm -rf. When I booted again with a live CD, I got the Ubuntu splash screen, and the dots changed color for about 1-2 minutes. Then everything halted -- the CD stopped spinning, the hard drive light stopped flashing, and the dots stopped changing colors.  All for no apparent reason.

I've since downloaded and ran boot-repair on the system, so it can still boot to Windows.  The ext3 partitions are still there; I haven't removed them via gparted.  I'm currently downloading the text-based installer, aka the alternate install CD.

Has anyone else run into this?  And is there anything else I should consider doing, short of running a fallingstone benchmark on the laptop?

---

### Post by poltr1 on 2012-06-11
Update: Downloaded the alternate distro and burned it to CD.  It appeared to be hanging on the DHCP setup.  Since I wasn't connected to a network at the time, this is probably where the standard distro was hanging up.  So I moved to my computer loft, plugged in a live network cable, and began the reinstall process again.

I was a little confused by the disk partitioning menus, as I wanted to re-use the existing (but now empty) partitions /dev/sda1 (ext4) and /dev/sda5 (swap).  (Sidenote: On this system,, I had installed Ubuntu first in /dev/sda1, then Windows in /dev/sda2.)  But I think I have it solved now.

---

### Post by poltr1 on 2012-06-13
Update: The alternative installation CD worked for me.  It was a little confusing at first, being asked to set up a volume group and then a logical volume.  (I didn't have to do that with the standard distro.)  And it wasn't apparent that I needed to hit the Enter key to change the initial or default values.  But Precise is installed now, and running well.  And since the laptop has a Broadcom 4318 wireless controller/card, I had to install firmware-b43-installer.

(Sidenote: The alternate installations can be found here: [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads) )

---

### Post by ramsforums on 2012-06-13
> **poltr1 said:**
> Update: The alternative installation CD worked for me.  It was a little confusing at first, being asked to set up a volume group and then a logical volume.  (I didn't have to do that with the standard distro.)  And it wasn't apparent that I needed to hit the Enter key to change the initial or default values.  But Precise is installed now, and running well.  And since the laptop has a Broadcom 4318 wireless controller/card, I had to install firmware-b43-installer.

(Sidenote: The alternate installations can be found here: [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads) )

You have used text baed alternate? or GUI based alternate?

Thanks for updating your progress..

---

