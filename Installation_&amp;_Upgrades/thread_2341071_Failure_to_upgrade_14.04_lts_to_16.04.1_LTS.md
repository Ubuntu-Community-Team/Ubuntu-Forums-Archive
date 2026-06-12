---
title: "Failure to upgrade 14.04 lts to 16.04.1 LTS"
date: 2016-10-24
forum: Installation &amp; Upgrades
---

### Post by Confused_Cheese on 2016-10-24
Hiya,

I recently tried to upgrade to the latest LTS on my intel nuc mini server and it failed at the end of the installation when trying to install a new kernel (i think) as I'd run out of space on my boot partition.

I let it continue, then when it was done I ran "apt-get auto-remove" which cleaned up the boot partition. I noticed the latest kernel was installed, so I just rebooted and it all seems to be working okay.

The thing that worries me is, could something else of been left broken? Is there any way to see if there were any other issues with the upgrade or anything is broken?

Thanks

---

### Post by ian-weisser on 2016-10-24
If a normal 'sudo apt update && sudo apt upgrade' works, then all is probably well.
If you wish to browse, check the logs in  /var/log/dist-upgrade

A 'separate boot partition' means something specific - it means you use encryption and/or LVM.
Only kernel packages would be directly affected by an out-of-space condition on the /boot partition. Only kernel packages are installed there.
Secondary problems --caused by the out-of-space condition but requiring separate fix-- are identified by apt warning messages.  If there are no warnings, then there are currently no further problems.

---

### Post by Confused_Cheese on 2016-10-24
Thanks for the reply

All seems well, aptitude is behaving as it should and reboots are working. Spent an hour or 2 fixing a few broken python apps and migrating some init.d scripts :D

---

