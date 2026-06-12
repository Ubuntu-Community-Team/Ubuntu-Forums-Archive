---
title: "Unmet dependencies - snapd"
date: 2017-05-02
forum: Installation &amp; Upgrades
---

### Post by arie2017 on 2017-05-02
Hello everyone

I have a problem with packages:

If I do:```
sudo apt-get upgrade
```…then I see an error message:
```
The following packages have unmet dependencies:snap-confine : Depends: snapd (= 2.24.1) but 2.21~14.04.2 is installed
snapd : Depends: snap-confine (= 2.21~14.04.2) but 2.24.1 is installed
Depends: ubuntu-core-launcher (= 2.21~14.04.2) but 2.24.1 is installed
ubuntu-core-launcher : Depends: snapd (= 2.24.1) but 2.21~14.04.2 is installed
```
If I do:```
sudo apt-get -f install
```…again an error:
```
Preparing to unpack .../snapd_2.24.1_amd64.deb ...Failed to stop snapd.refresh.timer: Unit snapd.refresh.timer not loaded.
Failed to stop snapd.refresh.service: Unit snapd.refresh.service not loaded.
Failed to stop snapd.autoimport.service: Unit snapd.autoimport.service not loaded.
Failed to stop snapd.socket: Unit snapd.socket not loaded.
dpkg: warning: subprocess old pre-removal script returned error exit status 5
dpkg: trying script from the new package instead ...
Failed to stop snapd.autoimport.service: Unit snapd.autoimport.service not loaded.
dpkg: error processing archive /var/cache/apt/archives/snapd_2.24.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 5
Errors were encountered while processing:
 /var/cache/apt/archives/snapd_2.24.1_amd64.deb
```
Thank you kindly!

---

### Post by Xian on 2017-05-02
Best guess is you have a package installed named snap.

Try this:

```
sudo apt-get remove snap
sudo apt-get install snapd
```

If not that simple:

```
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

---

