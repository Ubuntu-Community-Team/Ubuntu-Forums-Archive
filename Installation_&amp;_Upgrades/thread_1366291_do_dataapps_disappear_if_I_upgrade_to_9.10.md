---
title: "do data/apps disappear if I upgrade to 9.10?"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by HamletDRC on 2009-12-28
I am on 9.04 and maybe it is time to upgrade to 9.10. 

Will all of my installed apps, configuration, and data still work after the upgrade? Or will I need to install the applications all over again?

---

### Post by lloyd_b on 2009-12-28
> **HamletDRC said:**
> I am on 9.04 and maybe it is time to upgrade to 9.10. 

Will all of my installed apps, configuration, and data still work after the upgrade? Or will I need to install the applications all over again?

Any personal data (stored in your home directory) will not be touched by the upgrade.  It *is* possible for an upgrade to remove obsoleted packages, but this is quite uncommon - packages are generally not obsoleted, unless they are replaced by something else.

The upgrade process will update all applications you have installed to the version for 9.10, so you will not have to reinstall any of them.

About the only thing you may have to manually update are any proprietary video drivers you are running.

All in all - the upgrade process is time consuming (it takes a while on most connections to download all those package updates), but for most people it's pretty painless.

Lloyd B.

---

### Post by phillw on 2009-12-28
> **lloyd_b said:**
> Any personal data (stored in your home directory) will not be touched by the upgrade.  It *is* possible for an upgrade to remove obsoleted packages, but this is quite uncommon - packages are generally not obsoleted, unless they are replaced by something else.

The upgrade process will update all applications you have installed to the version for 9.10, so you will not have to reinstall any of them.

About the only thing you may have to manually update are any proprietary video drivers you are running.

All in all - the upgrade process is time consuming (it takes a while on most connections to download all those package updates), but for most people it's pretty painless.

Lloyd B.

+1.. I'd add, however, that rule about not losing personal data seems to work the best when you have a BACKUP of your personal stuff -- Murphy's Law is always on the look out for those who have not.

The 9.04 -- 9.10 does have a few quite major changes. For instance, moving from ext3 --> ext4  and Grub 0.97 --> Grub 1.97  (Called Grub Legacy & Grub2 respectively)

For changing from ext3 --> ext4 I REALLY would advise a backup. Neither upgrade is difficult, nor particualry time consuming - it's just extra steps to have to do.

I went from 9.04 --> 9.10 painlessly, messed up & recovered my Grub Legacy --> Grub2 and had no problems with ext3 --> ext4 -- I do have a lot of backups lying around the place, tho !!

All in all, especially for 9.10 - It seems best advice is to do a clean install, while you're at it - if you haven't already done so - make a /home partition.

Regards,

Phill.

---

