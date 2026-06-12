---
title: "I broke Synaptic"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by etotehpii on 2008-03-17
I was attempting to do a Dist upgrade from 7.04 to 7.10.

I first tried through Synaptic but it was giving me some errors so I decided to go through the terminal.

```
sudo apt-get dist-upgrade 
```didn't do anything.

I read on a thread about going into software sources and clicking everything under ubuntu and update tabs.  This seemed to brake synaptic.  Now whenever I try to launch it, I get the following error.

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occured while processing linux-wlan-ng (NewFileDesc2), E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I thought I had changed all the settings back in software sources but that didn't seem to work.  

Thanks

---

### Post by etotehpii on 2008-03-17
Ok, I managed to fix Synaptic by going into /etc/apt/sources.list and changing all gutsy to feisty.

However, when I go to upgrade to 7.10 in Synaptic I get the following errors.


Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

---

### Post by zvacet on 2008-03-18
System-->Administration-->Software Sources-->Third-party software>untick medibuntu>reload.In terminal type

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Then bacck to the System-->Administration-->Software Sources-->Third-party software>tick medibuntu and reload.

---

