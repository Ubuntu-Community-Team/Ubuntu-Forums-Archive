---
title: "GooglEarth on 9.10 AMD64"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by Keith_Beef on 2010-01-02
I found that after upgrading from 9.04 to 9.10 my Google Earth has disappeared. :-(

So I downloaded a new version from Google, and tried to run the installer.

```
sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.1.3533.1731...............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64
```


Tried again as root.

```
sudo sh GoogleEarthLinux.bin 
[sudo] password for xxxxx: 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.1.3533.1731...............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
```

Any idea what's going on here?

K.

---

### Post by Ginsu543 on 2010-01-02
Have you tried installing GoogleEarth through the Medibuntu repository? Just follow the directions from [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to add the repository. Then you will be able to install GoogleEarth in Synaptic which is much easier than trying to install it yourself.

---

