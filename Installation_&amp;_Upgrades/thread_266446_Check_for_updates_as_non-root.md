---
title: "Check for updates as non-root"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by k_rock923 on 2006-09-27
Hi.  I'm writing a big brother external script that will alert me to package updates.  However, aside from giving the bb user an entry in sudoers, I can' figure out a way to allow bb to check for updates.  in gentoo, normal users can do emerge -pvuND world and check for updates without being root.  I don't need bb to be able to install packages, just check if updates are available.  Any ideas?

---

### Post by maxpower on 2006-09-27
Well, I am not sure of your exact end goal, but one solution may be to have a cron job check for updates and then a non-root user can do a ```
aptitude -s upgrade
``` to see what would be updated without actually doing anything.  There is also the option of using SUID to allow a non-root user to check for updates.

mAx

---

### Post by x64Jimbo on 2006-09-27
There's also that nice little icon that shows up in the tray when updates are available.

---

### Post by k_rock923 on 2006-09-27
Thanks, aptitude is just what i was looking for as cron already does apt-get update nightly

Thanks for the idea of the system tray, but X is not installed on this machine.

---

