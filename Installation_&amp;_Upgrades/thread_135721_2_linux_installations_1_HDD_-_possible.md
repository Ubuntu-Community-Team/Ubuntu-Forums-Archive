---
title: "2 linux installations 1 HDD - possible?"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by alsac on 2006-02-24
Hi all!

I'd like to attempt two linux installations on the same HDD - gentoo and ubuntu. Any pointers from the gurus on which to install first and regarding partitioning (would LOVE to share /home - but if that's not possible... )

thanks!

---

### Post by ssam on 2006-02-24
you should have no problems. the ubuntu installer will detect other installations and setup grub correctly. i assume gentoos installer will do the same.

i would advise against sharing a /home partiton. if you different versions of an application writing to dot files you could get in a mess.

you could have a partition that both systems mount as /home/alsac/docs/ . you might be able to avoid permission problems by making sure the user id numbers are identical on both systems.

you can safely share the swap partition. (unless you want to suspend to disk on one OS and then boot the other)

---

### Post by LordBug on 2006-02-24
Entirely possible.

I would suggest something like this:

hda1 - / for Linux1  (make this partition bootable)
hda2 - / for Linux2
hda3 - /boot (should be able to use for both Gentoo and Ubuntu)
hda4 - /home (shouldn't have any issue sharing between Gentoo and Ubuntu*)
hda5 - swap for both

*=providing you use the same usernames/groups for both systems

Installation order won't really matter much.  I would suggest Ubuntu first, but only because it installs a LOT faster than Gentoo.  

Install Linux1 into /hda1.  Make a copy of /boot/grub/grub.conf for later.  Install the second Linux to /hda2.  Merge the /boot/grub/grub.conf file from Linux2 into Linux1.  Linux2 might overwrite grub.conf during install, which is why I suggest backing it up in the first place.  Reboot and you should be able to pick your Linux of choice.

---

### Post by LordBug on 2006-02-24
> if you different versions of an application writing to dot files you could get in a mess
That's something I hadn't thought about.  Wise advise.

---

### Post by alsac on 2006-02-24
Great, so I should install Gentoo first, I suppose. There is no installer in gentoo, the user is the installer. tee hee \\:D/  It's a long process (2 days last time I did it) because of compile times...

But, I'll have to create the partitions using gentoo (or otherwise) and make sure to write down the partition info before attempting this. 

What would be the purpose of a /boot partition though. Wouldn't installing GRUB to the MBR be sufficient - or is that a recipe for a muck-up?

I'd like to share app settings, etc between the two installations - **ssam**, you say that wouldn't sit well with either distro? is there a way to do something of the sort like keeping config files on a separate partition altogether?

Thanks for the quick replies fellas! A1 recommendations too! :D

---

### Post by ssam on 2006-02-24
i think you should give it a try. its usually the best way to see if stuff works.

most linux installers i have used have spotted other linux installs and set up grub properly.

the sharing of dot/config files might work for somethings, but i am pretty sure there will be a few probems. version 2 of someapp may be able to read and convert version 1's config file, but version 1 may choke on version 2's. and moving backwards and forwards between to versions reading and writing the same file could cause/expose some bugs. maybe you could do some tests and use symlinks if it works.

---

