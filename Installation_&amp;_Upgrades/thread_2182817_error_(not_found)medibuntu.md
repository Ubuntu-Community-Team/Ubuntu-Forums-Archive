---
title: "error (not found)medibuntu"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by BrianB62 on 2013-10-22
While doing updates last few days I keep getting  this - error (not found) regarding medibuntu.
Im using 12.04 Lts and even though I get error everything else is fine.
Any help appreciated.

---

### Post by howefield on 2013-10-22
The medibuntu repositories no longer exist so you have to remove them.

Open the Software Centre and from the Edit menu, select Software Sources, you should be able to remove or uncheck anything medibuntu related from the Other Software tab.

---

### Post by oldfred on 2013-10-22
[http://ubuntuforums.org/showthread.php?t=2179777](http://ubuntuforums.org/showthread.php?t=2179777)
Older Ubuntu versions may not have new install-css.sh
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
(make sure to install/upgrade the libdvdread4 package first)
sudo apt-get install libdvdread4
new libdvdread 4 is already in 13.10
The new libdvdread4 has an updated install-css.sh that will install libdvdcss2 from a videolan repo
[https://launchpad.net/ubuntu/+source/libdvdread](https://launchpad.net/ubuntu/+source/libdvdread)
Medibuntu discontinued April 2013
[https://launchpad.net/medibuntu/+announcement/11219](https://launchpad.net/medibuntu/+announcement/11219)
[http://gauvain.pocentek.net/node/61](http://gauvain.pocentek.net/node/61)

---

### Post by BrianB62 on 2013-10-23
Thanks for quick reply. Will try 2morra. Thanks:)

---

