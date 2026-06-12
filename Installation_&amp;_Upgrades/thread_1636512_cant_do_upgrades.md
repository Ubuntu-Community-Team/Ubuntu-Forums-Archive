---
title: "cant do upgrades?"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by ulao on 2010-12-03
123 packages can be updated.
3 updates are security updates.

New release 'maverick' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Wed Dec  1 21:49:15 2010 from 192.168.0.25
root@spawnlinux:~# do-release-upgrade
Checking for a new ubuntu release
No new release found
root@spawnlinux:~#

---

### Post by Hippytaff on 2010-12-03
Are you trying to upgrade a remote machine, server?

---

### Post by sikander3786 on 2010-12-03
Which version are you running currently? Lucid might need to be configured to 'upgrade to normal releases' instead of LTS only.

---

### Post by ulao on 2010-12-03
Are you trying to upgrade a remote machine, server? -- yes


Which version are you running currently? --
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

---

### Post by wojox on 2010-12-03
Headless, GUI less Server?

---

### Post by Hippytaff on 2010-12-03
10.10 is the latset realese unless you want to test Natty :-s

---

### Post by ulao on 2010-12-03
ah, so unbuntu does not check based on my version, it just assumes? I guess I was under the impression it felt I needed an upgrade.

---

### Post by sikander3786 on 2010-12-03
Updates are available for your Maverick.

```
sudo apt-get update && sudo apt-get upgrade
```

upgrade doesn't mean distro upgrade here ;-)

---

### Post by ulao on 2010-12-03
thx,I guess this was the part confusing me.

> New release 'maverick' available.
Run 'do-release-upgrade' to upgrade to it.

---

