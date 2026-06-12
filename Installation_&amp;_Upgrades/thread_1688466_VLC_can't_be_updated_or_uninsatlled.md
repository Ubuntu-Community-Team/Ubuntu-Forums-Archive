---
title: "VLC can't be updated or uninsatlled"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by prashant.saraf on 2011-02-15
After upgrade to 10.10 and when i do update or tries to install/update/remove i get following message
```
Errors were encountered while processing:
 /var/cache/apt/archives/vlc_1.1.4-1ubuntu1.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```please help me out,  I can do anything now.

Thanks

---

### Post by sikander3786 on 2011-02-15
Try,

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get install -f
sudo dpkg --configure -a

```

If that doesn't solve the isse, try these.

```
sudo rm /var/cache/apt/archives/vlc_1.1.4-1ubuntu1.3_i386.deb
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by prashant.saraf on 2011-02-17
while doing it i got following error

```

Unpacking replacement vlc ...
dpkg: error processing /var/cache/apt/archives/vlc_1.1.4-1ubuntu1.4_i386.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Operation not permitted

```

Any help on this please... I am not able to update my ubuntu10.10 any more.

Thanks

---

