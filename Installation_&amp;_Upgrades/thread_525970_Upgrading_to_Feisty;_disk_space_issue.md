---
title: "Upgrading to Feisty; disk space issue"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by mssever on 2007-08-14
I'm trying to upgrade my server from Edgy to Feisty. (I can finally afford the downtime in case something goes wrong.) However, I get the following message:
> Not enough free disk space.

The upgrade aborts now. Please free at least 12.2M of disk space on /boot.
I've already cleaned out all old kernels. My /boot partition is 44.1 MB, of which only a small portion is in use. (According to df, 14 MB is in use; according to du, 9.4 MB is in use. I'm not sure which number is correct. At any rate, I have approximately 30 MB available.)

On my Feisty laptop, /boot consumes 17 MB--and it's got newer hardware than my server.

So, I can't figure out how to proceed with the upgrade. Obviously the error message is bogus, since I have space for another kernel. (Or is apt crazy enough to try to write temp files to /boot instead of /tmp? /tmp is the ONLY legitimate location for temp files.)

Any ideas how I can upgrade?

---

### Post by mssever on 2007-08-15
bump

---

### Post by Pumalite on 2007-08-15
Save your /home data and do a clean install of Feisty.

---

### Post by mssever on 2007-08-15
> **Pumalite said:**
> Save your /home data and do a clean install of Feisty.
That really isn't an option, as it would take me a very long time to restore everything. I've customized my setup quite a bit, and I don't really have a record of what I've customized. For example, I have both PHP 4 and PHP 5 running simultaneously.

Even if I backed up /etc, /var, /usr/local, and /opt, I'd probably wind up with problems due to incorrectly overriding certain files.

---

### Post by heimo on 2007-08-15
> **mssever said:**
> Any ideas how I can upgrade?

Resize boot partition or move it to your current root partition (you can move it back afterwards, if you want). Or try forcing install of packages which want to write under /boot, using appropriate --force flags. Or copy stuff from /boot to /boot2, umount /boot, move stuff from /boot2 to /boot, upgrade, move stuff from /boot to /boot2, mount /boot and copy stuff from /boot2 to /boot...

---

### Post by mssever on 2007-08-16
> **heimo said:**
> Resize boot partition or move it to your current root partition (you can move it back afterwards, if you want). Or try forcing install of packages which want to write under /boot, using appropriate --force flags. Or copy stuff from /boot to /boot2, umount /boot, move stuff from /boot2 to /boot, upgrade, move stuff from /boot to /boot2, mount /boot and copy stuff from /boot2 to /boot...

Thanks for the suggestion. Unfortunately, it isn't possible to umount /boot when it's home to your running kernel. What I ended up doing is copying /boot to /boot2, then booting a live CD and copying files back....

I first tried to upgrade from a chroot environment to avoid having to modify GRUB, but I couldn't get X to start in my chroot environment, and if there's a CLI upgrade-manager, I don't know about it. So, I ended up modifying GRUB and fstab and booting normally. The upgrade is now underway.

---

