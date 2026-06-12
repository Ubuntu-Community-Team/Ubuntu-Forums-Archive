---
title: "Ubuntu 11.04 x64 and Matlab R2011a"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2011-07-07
Hi,

I have a problem during the installation of Matlab r2001a in Ubuntu 11.04 x64. If I run the install.sh file, I get the following messages and the graphical installation does not start. Where could be the problem?
```

sudo sh install
Preparing installation files ...
Installing ...
Finished

```Thank you

NB I have installed well the java RE
```

java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)

```

---

### Post by peugas on 2011-07-19
I found this, [https://help.ubuntu.com/community/MATLAB:](https://help.ubuntu.com/community/MATLAB:)

> Important Note Regarding Ubuntu 11.04

MATLAB R2011a was released on April 8, 2011. Please note that this is prior to the release of Ubuntu 11.04. Consequently Ubuntu 11.04 is not a supported operating system for MATLAB R2011a.

MATLAB R2011a users are strongly encouraged to install R2011a on Ubuntu 10.04 LTS or Ubuntu 10.10 for best results. Installation of MATLAB R2011a on unsupported Ubuntu releases are outside the scope of this documentation.

---

