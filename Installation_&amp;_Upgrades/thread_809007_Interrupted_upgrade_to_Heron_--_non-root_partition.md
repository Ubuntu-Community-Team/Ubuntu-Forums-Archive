---
title: "Interrupted upgrade to Heron -- non-root partitions aren't mounting"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by BroadArrow on 2008-05-27
I started an upgrade from 7.10 to 8.04 via Update Manager which was interrupted by a power cut. 

When rebooting only the root partition is mounted and no others and /dev/disk/by-uuid returns errors. (However, /dev/disk/by-uuid still works when run from a 7.10 live CD -- I've read in another thread that this may be because the Ubuntu can't recognise the hard drive correctly.)

Because I have a /home partition this means I am unable to properly log in as a user.

I believe the upgrade was interrupted after downloading all new packages and waiting for user input during the install. (Because I started the upgrade before going to bed but the power cut was well after the expected time to download.) Grub only has boot options for 7.10 so I'm pretty sure the upgrade wasn't completed.

Any ideas on how to:
[LIST=1]
[*]boot so that the drive works and I can mount my partitions
[*]resume the installation
[/LIST]

Oh, and the drive is an IDE drive.

Let me know if I need to post any output for further information.

---

### Post by BroadArrow on 2008-05-28
Following suggested solutions recommended to others who had interrupted upgrades, I tried booting in safe mode and then manually running dpkg to update and then upgrade.

As expected it's requiring me to run 
```
sudo dpkg --configure -a
```

which I do but it dies after hitting this error:

```
dpkg: error processing gtkhtm13.14
dependency problem - leaving unconfigured
dpkg: too many errors, stopping
```

Any ideas how to correct this?

Please?

---

