---
title: "Upgrade from Alt.CD Failing"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Tatty on 2008-04-25
I am trying to upgrade to hardy from gutsy using a hardy alternate CD.

When i insert the CD it gives me an option to upgrade, which begins happily.  It spends a while "fetching files" then aborts before installing anything with the following error message:

```
Failed to add the CD

There was a error adding the CD, the upgrade will abort. Please report this as a bug if this is a valid Ubuntu CD.

The error message was:
'E:Unable to locate any package files, perhaps this is not a Debian Disc'
```

Afterwards I had a look and saw that it had altered my sources.list file to have the hardy repos.  So I deleted that and restored the bakup gutsy sources.list file.  I then tried to do the typical net upgrade using update manager, although this failed after a long long pause saying it failed to get the release notes - I assume this will be due to server demand?

Any help getting the install working from the alt.cd would be excellent.

Things I have tried:
-md5 of iso checks out
-The first burn of the alt.cd failed an integritry check, have now burned a new CD which checks out fine, but still fails with the same message. 

Thanks.

---

### Post by Tatty on 2008-04-26
24h bump :)

---

### Post by erorr404 on 2009-04-17
I get this problem as well.

I tried upgrading from 8.04 to 8.10 using the alternate CD (ubuntu-8.10-alternate-i386.iso). I have checked the MD5 checksum and it is correct.

I followed the instructions [Here]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD") and mounted the ISO as a drive.

After running 'gksu "sh /cdrom/cdromupgrade"' the installation starts but the 'Failed to add the CD...' error occurs and stops the installation.

Any help would be appreciated.

---

### Post by spinwood on 2009-04-27
Same here with both the mounted ISO and burned media when attempting an upgrade.

On a positive note... A clean install worked seamlessly on a different box.

---

### Post by spinwood on 2009-05-03
Alas... I guess we are alone in the world.

---

### Post by spinwood on 2009-05-08
The live upgrade worked without a hitch.  I'm happy with Jaunty, but I wish I could have gotten the alternate CD method to work.

---

### Post by ton145 on 2009-06-26
I downloaded 9.40 Alternate ISO several times from different mirrors. But they're always failed to upgrade with message 'checksum failed' for some packages. I have tried it bith burned CD and mounted ISO.

---

### Post by spinwood on 2009-06-29
Try the torrent.  I'm seeding the ISO even though I couldn't get it to work.

---

