---
title: "Cannot uninstall bacula-director-pgsql"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by born1962 on 2011-02-22
:confused: I am trying to uninstall bacula-director-pgsql with very little success. Postgresql is unistalled and no other Bacula packages are installed. An error is raised - Can't open /usr/share/bacula-common/common-functions then the process is rolled back.

I looked at the bacula-director-pgsql.postinst file and found the offending line, but I do not understand the code construction so I am unwilling as yet to alter the offending line.

Can anyone help ? I need to get rid of this so I can at least try the sql lite version.

---

### Post by born1962 on 2011-02-22
Got the ...

anyway I had to force an install of bacula-director-common and bacula-common, then uninstall.

Now for the next frustrating moment !

---

