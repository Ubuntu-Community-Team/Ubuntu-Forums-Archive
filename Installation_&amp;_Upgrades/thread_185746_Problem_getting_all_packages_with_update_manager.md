---
title: "Problem getting all packages with update manager"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by MoxJet on 2006-06-01
I get the following message when using the update manager accessed through terminal gksudo "update-manager -d" and starting the update to dapper drake:

Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found

Any idea why?

---

### Post by deweese on 2006-06-01
This is a bug that has been reported with update manager.
You can complete the upgrade by going to your repositories and disabling
them.  Here is what Michael Vogt said in launchpad.com who is assigned to this bug,
"It seems to me like the some of your repositories, namely
[http://theli.free.fr/packages/breezy/](http://theli.free.fr/packages/breezy/) and [http://koti.mbnet.fi/](http://koti.mbnet.fi/) are no
longer working. This is most likely why it stops."

Could you please try to disabled them (e.g. via
System/Adminsitration/SoftwareProperties) and try again?

To see this entire bug report go to:  [https://launchpad.net/bugs/46163](https://launchpad.net/bugs/46163) seems to me like the some of your repositories, namely
[http://theli.free.fr/packages/breezy/](http://theli.free.fr/packages/breezy/) and [http://koti.mbnet.fi/](http://koti.mbnet.fi/) are no
longer working. This is most likely why it stops.

Could you please try to disabled them (e.g. via
System/Adminsitration/SoftwareProperties) and try again?

I followed Mike Vogt's instructions and the download went through.
You can just delete those Breezy Repositories.  Then, It goes through.
You will be Dapper then.

---

