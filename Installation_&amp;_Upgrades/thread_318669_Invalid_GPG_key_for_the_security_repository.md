---
title: "Invalid GPG key for the security repository"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by AzraelUK on 2006-12-14
I'm trying to run **apt-get update**, but each time it tells me that the GPG key is invalid:

[FONT="Courier New"]
W: GPG error: http://archive.ubuntu.com edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
[/FONT]

Does anybody know where the latest GPG key for it is?

---

### Post by Sqwishy on 2006-12-14
you could try ```
apt-get dist-upgrade --allow-unauthenticated
``` Otherwise it's pobobly a problem with the servers taking to much trafic.

---

