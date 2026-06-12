---
title: "No new release found"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by lisanels47 on 2012-11-21
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-34-generic i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

New release '12.10' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Wed Nov 21 13:00:04 2012 from hsib-01.hsi.com
root@hsib-14:~# do-release-upgrade
Checking for a new Ubuntu release
No new release found

Ok, it lied!  Well, in the past I was able to purge update-manager-core and re-installing it... Didn't work this time.

:(

---

### Post by ibjsb4 on 2012-11-21
Do you have just the core installed?  If you have the package, check here:

[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab)

Edit:

If running just the core, go to:

/etc/update-manager/release-upgrades

and check that prompt=normal

Also could try

do-release-upgrade -d

Just to see if that will trigger it

---

### Post by polax on 2013-05-21
Worked for me .. Thanks :)

---

