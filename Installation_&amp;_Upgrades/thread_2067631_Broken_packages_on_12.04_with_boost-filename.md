---
title: "Broken packages on 12.04 with boost-filename"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by alex2356 on 2012-10-07
Hi all, 

I need to compile a larger software package, and both ```

    -libbost-filename
    -lboost-filename
```gave a "cannot find" message. So I suppose boost-filename is not installed on my system. 

In order to install it I tried the command
```

sudo apt-get install libboost-filesystem*
```which returned the following enchalada:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libboost-filesystem1.42-dev' for regex 'libboost-filesystem*'
Note, selecting 'libboost-filesystem1.46-dev' for regex 'libboost-filesystem*'
Note, selecting 'libboost-filesystem-dev' for regex 'libboost-filesystem*'
Note, selecting 'libboost-filesystem1.48-dev' for regex 'libboost-filesystem*'
Note, selecting 'libboost-filesystem1.46.1' for regex 'libboost-filesystem*'
Note, selecting 'libboost-filesystem1.48.0' for regex 'libboost-filesystem*'
libboost-filesystem-dev is already the newest version.
libboost-filesystem1.46-dev is already the newest version.
libboost-filesystem1.46.1 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libboost-filesystem1.48-dev : Depends: libboost1.48-dev (= 1.48.0-3) but it is not going to be installed
                               Depends: libboost-system1.48-dev (= 1.48.0-3) but it is not going to be installed
                               Conflicts: libboost-filesystem1.46-dev but 1.46.1-7ubuntu3 is to be installed
E: Unable to correct problems, you have held broken packages.
```I would appreciate any advice how to cleanly correct those problems with the most minimal work and to be sure that boost-filename gets installed correctly so it can be used again. 


Thanks
  Alex

---

