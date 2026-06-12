---
title: "HELP! Partial Upgrade deleted my kernel"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by l0r3zz on 2008-10-16
I've been happily running 8.04 on my HP NC6910p laptop for months.  A few days ago, it started complaining about having to run a partial upgrade, which I did sometimes, sometimes not.  After a while I got tired of seeing the message about some packages that it couldn't authenticate (libdb3) so I went into update manager and reinstalled it.  Then the Partial Update message said that it needed to delete a bunch of obsolete packages and reinstall a couple, I proceeded, it finished, then called for a reboot. I rebooted and the system didn't come back up!  Upon running an installation disk and looking at the /boot partition on the hard drive I discovered all of my kernels have been deleted!! The grub directory is still there but all of the vmlinuz , abi, config and initrd.img files are gone!  I had this system tuned the way that I wanted it and would like to try and save it and not do a re-install (I have a bunch of VMs and projects on it.  What can I do?  I do have another HP6400 that has a more or less working 8.04 installation, I was thinking that I could somehow copy the files from that /boot partition and somehow get them over to the broken installation, If I could get it booted, maybe I could repair it further.


Any Ideas?

---

### Post by cariboo on 2008-10-16
If I get a partial upgrade message, I open a terminal and use:

```
sudo aptitude safe-upgrade.
```

Are you sure you don't have any old kernels still installed. If so you may be able to get grub to use one of the older kernels.

Jim

---

