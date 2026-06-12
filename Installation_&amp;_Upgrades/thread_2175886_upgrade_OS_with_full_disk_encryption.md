---
title: "upgrade OS with full disk encryption?"
date: 2013-09-21
forum: Installation &amp; Upgrades
---

### Post by bakinsoda on 2013-09-21
Hi,

When I installed Ubuntu Natty back then, I enabled full disk encryption per [this]("http://joernfranz.net/2011/01/20/installing-ubuntu-10-10-with-full-disk-encryption/") blog post (now no longer available).  Basically, I created an LVM and encrypted it, the only part not encrypted is the boot partition.

As Natty is no longer supported, I want to upgrade my OS to a more recent version of ubuntu, probaly Ubuntu 12.04.  However, I'm afraid that once I upgrade my computer won't boot up and that I won't be able to fix it.

Does anyone know if it's safe to upgrade the OS with full disk encryption?  What file should I save and have accessible in order to do post-hoc fixing should issues arise?  (eg, /etc/crypttab?)

I've been trying to not upgrade because of fear that things will break, but as Natty is no longer supported, the packages that I need are forcing me to upgrade.  Please advise, thanks!

---

### Post by TheFu on 2013-09-21
Do a full backup when the system is decrypted.
Install 12.04 (great choice, BTW), then restore of the files you don't want to lose.  Do not restore the programs, since most of those have changed.  The reason for a full system backup is to ensure you don't forget to backup something important.  I've recently written about backups here ... with dpkg --get-selections and --set-selections as part of it.  That should reduce the need to backup the programs, but still be certain to get /home and all the settings.  There might be other places you MUST get too ... your system isn't the same as mine.

If you use encryption and don't have backups ... well, that is absolutely crazy.

---

### Post by bakinsoda on 2013-09-22
Thanks.  Yes, I do keep a backup of the important files since the drive is encrypted ;).

I went ahead and upgraded to 11.10 successfully, and then 12.04.  Will keep it here until 14.04 comes out.

Thanks!

---

