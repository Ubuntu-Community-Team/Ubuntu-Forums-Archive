---
title: "Manually edit choice not seeing hda"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by jwhitener on 2006-07-22
I have two disks and the manually edit partition table option is only showing me /dev/hdk as a choice to edit.

/dev/hda
/dev/hdk

hdk is my windows installation so I tried to set things up manually, and hda is where I want kubuntu to reside.  I booted off the livecd and went to a konsole. 

I did sudo fdisk /dev/hda and made 3 sections:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041   83  Linux
/dev/hda2            2434        2677     1959930   83  Linux
/dev/hda3            2678        9729    56645190   83  Linux

After I made the partitions I rebooted and went back into the livecd kubuntu.  I then opened konsole again and did sudo mkreiserfs and hda1 and hda3, and did sudo mkswap on hda2.  Then I clicked "install".

Same thing.  When I get to the disk part, if I just choose erase entire hardisk and click next, it tells me its going to make two partitions on hda??.  If I choose manually edit, it only brings up hdk and hda is not a choice...

Any ideas on why the graphical installer isn't letting me specify which partitions on hda to use for what?

edit::  Well I gave up and am not letting it do its default install (hda1 hda5 deal) on hda.  I'll see if I can resize and partition into the three areas hda1, hda2 and hda3 after its finished.  Still find it odd that the manually edit option wouldn't list hda as a choice.

---

### Post by catlett on 2006-07-22
I don't like the live installer. It has too many defaults and little configuration done by the user.
I use the Alternate Install CD which is basically the old 5.10 text install. It lets me go through all my drives and partition, rename, label, set bootable, etc If any ??buntu install disc would see all your drives it is the alternate install cd.
[http://mirror.cs.umn.edu/ubuntu-releases/kubuntu/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/kubuntu/6.06/)

---

