---
title: "Problem with update manager"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by prasadchalasani on 2009-11-16
when I run the update manager this error showup

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```

```
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Beta amd64 (20090929.2)/dists/karmic/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Beta amd64 (20090929.2)/dists/karmic/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

what I have to do now
:?

---

### Post by coffeecat on 2009-11-16
It looks as though you have the CD marked as a repository.

Open Synaptic, go to Setting > Repositories > Ubuntu Software tab. Uncheck the box by "CD with Ubuntu 9.10 'Karmic Koala' ". Do a reload, close Synaptic and see if Update Manager works properly now.

---

### Post by prasadchalasani on 2009-11-16
ya you are right. thanks a lot

---

