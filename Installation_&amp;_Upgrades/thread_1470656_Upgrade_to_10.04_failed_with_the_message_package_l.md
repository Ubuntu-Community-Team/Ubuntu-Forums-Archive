---
title: "Upgrade to 10.04 failed with the message: package linux-image-2.6.32-21-generic 2.6.3"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by omeron on 2010-05-03
After I upgraded to 10.04 from the previous version I received the following error:
package linux-image-2.6.32-21-generic 2.6.32-21.32 failed to upgrade.
Then the system tried to rollback and I received the message that the rollback failed and that the system might be unusable. 
It is working fine, but I cannot run package upgrades - they fail to install (the package manager is working fine, it's the install phase that fails). 

Any thoughts on what I should do????

Thanks
Omeron

---

### Post by kansasnoob on 2010-05-03
Try:

```
sudo apt-get clean
```

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

### Post by omeron on 2010-05-03
Thanks, 

I tried and received the following: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.32-21-generic (2.6.32-21.32) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.32-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-21-generic; however:
  Package linux-image-2.6.32-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.21.22); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.32-21-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas?
Thanks,
Omeron

---

### Post by eGelor on 2010-05-04
I have serious problem with my system 
1. my Nvidia drivers are crashed .
2. i can't update or upgrade my system.
Please help


> Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/a/amara/python-amara_1.2a2-1ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/amara/python-amara_1.2a2-1ubuntu1_all.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/p/python-gtkglext1/python-gtkglext1_1.1.0-4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/p/python-gtkglext1/python-gtkglext1_1.1.0-4_i386.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox-ubuntuone-music-store/rhythmbox-ubuntuone-music-store_0.0.9-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox-ubuntuone-music-store/rhythmbox-ubuntuone-music-store_0.0.9-0ubuntu1_all.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode_1.1.5-0ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode_1.1.5-0ubuntu6_i386.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode-doc_1.1.5-0ubuntu6_all.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode-doc_1.1.5-0ubuntu6_all.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xfonts-mathml/xfonts-mathml_4ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xfonts-mathml/xfonts-mathml_4ubuntu1_all.deb) Could not resolve 'archive.ubuntu.com'


> Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by omeron on 2010-05-10
Any ideas someone???

---

### Post by eGelor on 2010-05-17
I finally try to upgrade. the problem was my connection.
The problem now is that my keyboard on linux lost .
i log in via graphic keyboard, but i can not write inside my gdm unit.
Pls Help!
Solution for me  was to first upgrade dpkg (apt-get install dpkg) then run a full upgrade (aptitude full-upgrade). This caused the util-linux error to go away and full-upgrade to hum along like normal.

---

### Post by omeron on 2010-05-29
Nothing works...
I opened a bug on it, but I would love to hear thoughts for a workaround.

Thanks
Omeron

---

