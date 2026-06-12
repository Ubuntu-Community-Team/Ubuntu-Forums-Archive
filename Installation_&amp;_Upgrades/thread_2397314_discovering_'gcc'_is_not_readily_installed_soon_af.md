---
title: "discovering 'gcc' is not readily installed soon after 'build-essential' installation"
date: 2018-07-28
forum: Installation &amp; Upgrades
---

### Post by abdulbadii on 2018-07-28
As there's no direct internet connection, I posed a quite daunting problem while discovering 'gcc' is not readily installed soon after 'build-essential' installation package was copied to HOME dir. and then being installed  
```
$ sudo dpkg -i bui*.deb
(Reading database ... 167850 files and directories currently installed.)
Preparing to unpack build-essential_12.4ubuntu1_amd64.deb ...
Unpacking build-essential (12.4ubuntu1) over (12.4ubuntu1) ...
dpkg: dependency problems prevent configuration of build-essential:
build-essential depends on gcc (>= 4:7.2); however:
Package gcc is not installed.
build-essential depends on g++ (>= 4:7.2); however:
Package g++ is not installed.
build-essential depends on make; however:
Package make is not installed.
build-essential depends on dpkg-dev (>= 1.17.11); however:
Package dpkg-dev is not installed.
dpkg: error processing package build-essential (--install):
dependency problems - leaving unconfigured  

```  
This is on Ubuntu Mate v18.04 with flawlessly installation and launch.
How to solve it and get gcc package installed completely ? Thanks before

---

### Post by steeldriver on 2018-07-28
`build-essential` doesn't actually contain any software - it just pulls in gcc/make etc via **dependencies**

For an offline installation, probably what you need to do is 

```

sudo apt-get install --print-uris build-essential

```

**on the offline machine** and then resolve the dependencies manually by obtaining ALL of the listed packages from the web

---

