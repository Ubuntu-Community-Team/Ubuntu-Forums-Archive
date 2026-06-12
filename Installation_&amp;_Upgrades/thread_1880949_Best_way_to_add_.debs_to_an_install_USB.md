---
title: "Best way to add .debs to an install USB?"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by djsephiroth on 2011-11-14
Need to install from a USB drive on 100+ systems. Immediately afterward, the systems will need to install a lot of upgrades and additional packages. To avoid straining the network, I'd like to put all these additional debs on the USB drive and tell apt to look in the USB drive before trying to hit a remote repo. What's the best way to go about this?

Note: we have puppet and a local apt cache server; however, using either of those generates network traffic. Anything that creates network traffic is right out, even if the traffic would be local. The debs have to be pulled from the USB drive. inb4 anyone suggests anything that generates network traffic. Thanks. :KS

Here's the final preseed command, in case it matters:
```
d-i preseed/late_command string \
cd /target; \
cp /cdrom/dpkgselections.pruned.txt ./; \
cp /cdrom/sources.list ./etc/apt/; \
chroot ./; \
apt-get update; \
apt-get -y install dselect; \
dpkg --set-selections < dpkgselections.pruned.txt; \
dselect update; \
apt-get dselect-upgrade
```

---

### Post by MG&amp;TL on 2011-11-14
Use remastersys or clonezilla to clone images of your 'setup' system, then use that image rather than the default ubuntu installation disc.

---

### Post by oldfred on 2011-11-14
Why not just copy the debs into the new system and update from there.

Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

Not sure if you can easily do it for multiple packages.

Some other alternatives:
Offline Updates:
[http://keryxproject.org/](http://keryxproject.org/)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

---

### Post by djsephiroth on 2011-11-14
@oldfred: Why didn't I think of that? Thanks!

---

