---
title: "Update-Manager &quot;Upgrade&quot; button missing"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by miscellanyous on 2012-03-01
I am trying to upgrade from 11.04 (Natty) to 11.10 (Oneiric). I have installed all updates via update-manager, however, there is no box indicating "A new release is available..." nor is there any "Update" button. Here is some info:

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty
```

```
~$ cat /etc/update-manager/release-upgrades
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
prompt=normal
```

Attached is my sources.list file. 

Could this be related to having multiple Ubuntu OS on my hard drive?

---

### Post by dino99 on 2012-03-01
try :  sudo do-release-upgrade -d

---

### Post by miscellanyous on 2012-03-06
works, thanks.

---

