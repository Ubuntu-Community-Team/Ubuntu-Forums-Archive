---
title: "update to 10.10"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by fidelandche on 2010-12-11
Hi,
Just come back to Ubuntu after a short break and I am running 10.04 by wubi along side vista. I have run the update manager but it does not appear to find the upgrade to 10.10, is there anything I can do to update to 10.10

---

### Post by Rubi1200 on 2010-12-11
Be aware that there are some problems with Wubi installs at the moment. 
See here for more information:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you really want the latest version, I recommend uninstalling the current version and doing a fresh install.

The Windows installer can be found here:
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by garvinrick4 on 2010-12-11
In Terminal copy and paste:
```
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

```
: Look to make sure all is cool with WUBI upgrade from lucid to maverick and no bugs.

---

### Post by Rubi1200 on 2010-12-11
> **garvinrick4 said:**
> Look to make sure all is cool with WUBI upgrade from lucid to maverick and no bugs.
Are you aware of the fact that upgrades are breaking Wubi installs at the moment?
[WUBI MEGATHREAD]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by garvinrick4 on 2010-12-11
> **Rubi1200 said:**
> Are you aware of the fact that upgrades are breaking Wubi installs at the moment?
[WUBI MEGATHREAD]("http://ubuntuforums.org/showthread.php?t=1639198") I tell everyone that is upgrading WUBI to make sure it is cool to upgrade at this time before doing so. Very nice thread, book marked it:

---

