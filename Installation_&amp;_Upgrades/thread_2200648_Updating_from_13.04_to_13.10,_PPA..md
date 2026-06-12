---
title: "Updating from 13.04 to 13.10, PPA."
date: 2014-01-20
forum: Installation &amp; Upgrades
---

### Post by Therseo on 2014-01-20
Trying to update from 13.04, This is the error that comes back. 
```

W: Failed to fetch http://..archive.canonical.com/dists/raring/Release.gpg  Something wicked happened resolving '..archive.canonical.com:http' (-11 - System error)

W: Failed to fetch http://..archive.canonical.com/dists/raring/partner/binary-i386/Packages  Something wicked happened resolving '..archive.canonical.com:http' (-11 - System error)

W: Failed to fetch http://..archive.canonical.com/dists/raring/partner/i18n/Translation-en_GB  Something wicked happened resolving '..archive.canonical.com:http' (-11 - System error)

W: Failed to fetch http://..archive.canonical.com/dists/raring/partner/i18n/Translation-en  Something wicked happened resolving '..archive.canonical.com:http' (-11 - System error)

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/intel-graphics-updates/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by grahammechanical on 2014-01-20
When we upgrade from one version of Ubuntu to another we should disable any PPAs and reactivate them after the upgrade has completed. The upgrade scripts that the developers create cannot take into account all the changes that users make to the system. Does Ubuntu still load and does it still work? Can you run Update Manager and does it work or do you get an error and are unable to update?

Regards.

---

### Post by Therseo on 2014-01-20
The error comes during the start of the update, it does not allow the update. thus, no problems with normal functionality. 

Thanks for the quick response, sorry about my delay

---

