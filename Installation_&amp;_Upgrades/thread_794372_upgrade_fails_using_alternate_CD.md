---
title: "upgrade fails using alternate CD"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by Dan_IV on 2008-05-14
All my normal attempts over the past few weeks to upgrade have failed.  I've upgraded since three releases ago and never had a problem like this.

Here are the details.

when running partial upgrade through the disk I get this error.

```
Could not Calculate the upgrade

A unresolvable Problem occured while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport

```

here is the pertinent information from /var/log/dist-upgrade

```

MarkUpgrade() called on a non-upgrable pkg: 'kubuntu-desktop'
ERROR:root:Dist-upgrade failed: 'A essential package would have to be removed'

```

Noting that, I also have KDE4 installed and running which I check out everyonce in a while when I get updates for it.  currently the only thing selected in my software sources is the CDROM hardy disk.

Any one bump into this or report it in launchpad yet?

---

### Post by Pumalite on 2008-05-14
Remove all third parties from sources.list. You might have to remove video driver. At Virtual Terminal:
sudo dpkg-reconfigure xserver-xorg
Choose vesa as the driver. Then try again.

---

### Post by Dan_IV on 2008-05-14
> **Pumalite said:**
> Remove all third parties from sources.list. You might have to remove video driver. At Virtual Terminal:
sudo dpkg-reconfigure xserver-xorg
Choose vesa as the driver. Then try again.

1.  As already stated the only thing in the third party list is the alternate CD that I'm attempting to install from.
2.  the dist-upgrade error specifically states the problem is with "kubuntu-desktop" as I noted in my first post.
3.  I've had no errors dealing with xserver-xorg at all and don't understand how this recommendation makes any sense at all?


Stated simply the upgrade failed because of kubuntu-desktop (I have KDE4 installed and it's marked as non-upgradable package).

---

### Post by Pumalite on 2008-05-14
This is the reason:
'A essential package would have to be removed'
But you might be right; maybe you need to remove KDE before upgrading.

---

### Post by Dan_IV on 2008-05-14
I'm going on the guess that kubuntu-desktop is the essential package it's reffering to, however I don't think I should have to remove it or any kde4 packages to upgrade as this appears to be a bug. 

My hope was that someone else may had already encountered it and found a work around, trying the alternate CD was my last ditch effort to upgrade as all other methods have failed thus far.

If removing KDE4 is the only way I'm going to be able to upgrade that is a bit dissapointing.

---

### Post by Dan_IV on 2008-05-14
Looks like a very similar bug was already reported all the way back when somebody tried to update to Dapper from Edgy.  Just thought I would share that with others.  Below is the Link.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/88844]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/88844")

---

