---
title: "How to update libraries for audio codecs"
date: 2014-12-19
forum: Installation &amp; Upgrades
---

### Post by ovingiv on 2014-12-19
Morning from plymouth!

I'm having problems installing EasyTAG editor. I have added the PPA and did a apt-get update and went into the software center to install it. It told me that some dependence were not there. How would I go about to updating these to the current version. I'm running Chrubuntu 12.0.4 LTS. If you need something more just ask...

Thanks

> The following packages have unmet dependencies:

easytag: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.9 is to be installed
         Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
         Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.26.1-1ubuntu1.1 is to be installed
         Depends: libglib2.0-0 (>= 2.37.3) but 2.32.4-0ubuntu1 is to be installed
         Depends: libgtk-3-0 (>= 3.2.1) but 3.4.2-0ubuntu0.8 is to be installed
         Depends: libopus0 (>= 1.0.3) but it is not going to be installed
         Depends: libopusfile0 (>= 0.5) but it is not going to be installed
         Depends: libpango-1.0-0 (>= 1.14.0) but it is not going to be installed
         Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
         Depends: libwavpack1 (>= 4.40.0) but 4.60.1-2 is to be installed




---

### Post by grahammechanical on 2014-12-19
The command apt-get update just updates the list of software sources to include that PPA as a source. It is usual, after adding a PPA, to run these two commands before trying to install the software.

```
sudo apt-get update
sudo apt-get upgrade
```

Regards.

---

### Post by ovingiv on 2014-12-19
Thanks for the quick reply. 

I did that with no avail. It does not find that there is an update for these items...

Is there a manual way to update these one by one?

---

