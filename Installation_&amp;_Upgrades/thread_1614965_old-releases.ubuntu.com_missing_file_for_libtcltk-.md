---
title: "old-releases.ubuntu.com missing file for libtcltk-ruby1.8"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by wyBTUiRt on 2010-11-06
Not sure if this is an appropriate place to post this but I need to start somewhere.

Anyway, I want to know what I can do or who to inform to get the issue addressed.

Thanks, Tom

I'm getting a file not found error when trying to install libtcltk-ruby1.8 via apt-get update; apt-get upgrade. Both intrepid-updates' and intrepid-security's universe packages claim to require pool/universe/r/ruby1.9/libtcltk-ruby1.9_1.9.0.2-7ubuntu1.3_i386.deb but the file doesn't exist on old-releases.ubuntu.com.

Install using intrepid-updates universe:
```

root@dcerouter:/etc/apt# apt-get update; apt-get upgrade
Ign file: ./ Release.gpg
Ign file: ./ Translation-en_US
Ign file: ./ Release
Ign file: ./ Packages
Ign http://debian.slimdevices.com stable Release.gpg
Hit http://old-releases.ubuntu.com intrepid Release.gpg
Ign http://old-releases.ubuntu.com intrepid/main Translation-en_US
Ign http://old-releases.ubuntu.com intrepid/restricted Translation-en_US
Hit http://packages.medibuntu.org intrepid Release.gpg
Ign http://packages.medibuntu.org intrepid/free Translation-en_US
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US
Ign http://deb.linuxmce.org intrepid Release.gpg
Ign http://deb.linuxmce.org intrepid/beta2 Translation-en_US
Ign http://deb.linuxmce.org 20dev_ubuntu Release.gpg
Ign http://debian.slimdevices.com stable/main Translation-en_US
Ign http://old-releases.ubuntu.com intrepid/universe Translation-en_US
Ign http://old-releases.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com intrepid-updates Release.gpg
Ign http://old-releases.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com intrepid-security Release.gpg
Hit http://packages.medibuntu.org intrepid Release
Ign http://old-releases.ubuntu.com intrepid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://deb.linuxmce.org 20dev_ubuntu/main Translation-en_US
Ign http://deb.linuxmce.org intrepid Release
Get:1 http://debian.slimdevices.com stable Release [1645B]
Ign http://old-releases.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com intrepid Release
Hit http://old-releases.ubuntu.com intrepid-updates Release
Hit http://packages.medibuntu.org intrepid/free Packages
Ign http://deb.linuxmce.org 20dev_ubuntu Release
Ign http://debian.slimdevices.com stable/main Packages
Hit http://old-releases.ubuntu.com intrepid-security Release
Hit http://packages.medibuntu.org intrepid/non-free Packages
Ign http://deb.linuxmce.org intrepid/beta2 Packages
Hit http://old-releases.ubuntu.com intrepid/main Packages
Hit http://old-releases.ubuntu.com intrepid/restricted Packages
Hit http://old-releases.ubuntu.com intrepid/universe Packages
Hit http://old-releases.ubuntu.com intrepid/multiverse Packages
Hit http://old-releases.ubuntu.com intrepid/main Sources
Hit http://old-releases.ubuntu.com intrepid/restricted Sources
Hit http://debian.slimdevices.com stable/main Packages
Ign http://deb.linuxmce.org 20dev_ubuntu/main Packages
Hit http://old-releases.ubuntu.com intrepid/universe Sources
Hit http://old-releases.ubuntu.com intrepid/multiverse Sources
Hit http://old-releases.ubuntu.com intrepid-updates/main Packages
Hit http://old-releases.ubuntu.com intrepid-updates/restricted Packages
Get:2 http://old-releases.ubuntu.com intrepid-updates/universe Packages [146kB]
Hit http://deb.linuxmce.org intrepid/beta2 Packages
Hit http://deb.linuxmce.org 20dev_ubuntu/main Packages
Hit http://old-releases.ubuntu.com intrepid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com intrepid-security/main Packages
Hit http://old-releases.ubuntu.com intrepid-security/restricted Packages
Hit http://old-releases.ubuntu.com intrepid-security/multiverse Packages
Fetched 146kB in 2s (59.3kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  libtcltk-ruby1.8
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1731kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
WARNING: The following packages cannot be authenticated!
  libtcltk-ruby1.8
Authentication warning overridden.
Err http://old-releases.ubuntu.com intrepid-updates/universe libtcltk-ruby1.8 1.8.7.72-1ubuntu0.2
  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/pool/universe/r/ruby1.8/libtcltk-ruby1.8_1.8.7.72-1ubuntu0.2_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@dcerouter:/etc/apt#

``` Install using intrepid-security universe:
```

root@dcerouter:/etc/apt# apt-get update; apt-get upgrade
Ign file: ./ Release.gpg
Ign file: ./ Translation-en_US
Ign file: ./ Release
Ign file: ./ Packages
Ign http://debian.slimdevices.com stable Release.gpg
Hit http://old-releases.ubuntu.com intrepid Release.gpg
Ign http://old-releases.ubuntu.com intrepid/main Translation-en_US
Ign http://old-releases.ubuntu.com intrepid/restricted Translation-en_US
Hit http://packages.medibuntu.org intrepid Release.gpg
Ign http://packages.medibuntu.org intrepid/free Translation-en_US
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US
Ign http://deb.linuxmce.org intrepid Release.gpg
Ign http://deb.linuxmce.org intrepid/beta2 Translation-en_US
Ign http://deb.linuxmce.org 20dev_ubuntu Release.gpg
Ign http://debian.slimdevices.com stable/main Translation-en_US
Ign http://old-releases.ubuntu.com intrepid/universe Translation-en_US
Ign http://old-releases.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com intrepid-updates Release.gpg
Ign http://old-releases.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com intrepid-security Release.gpg
Ign http://old-releases.ubuntu.com intrepid-security/main Translation-en_US
Get:1 http://debian.slimdevices.com stable Release [1645B]
Hit http://packages.medibuntu.org intrepid Release
Ign http://old-releases.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://deb.linuxmce.org 20dev_ubuntu/main Translation-en_US
Ign http://deb.linuxmce.org intrepid Release
Ign http://old-releases.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com intrepid Release
Hit http://old-releases.ubuntu.com intrepid-updates Release
Hit http://old-releases.ubuntu.com intrepid-security Release
Ign http://debian.slimdevices.com stable/main Packages
Hit http://packages.medibuntu.org intrepid/free Packages
Ign http://deb.linuxmce.org 20dev_ubuntu Release
Hit http://debian.slimdevices.com stable/main Packages
Hit http://old-releases.ubuntu.com intrepid/main Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Ign http://deb.linuxmce.org intrepid/beta2 Packages
Hit http://old-releases.ubuntu.com intrepid/restricted Packages
Hit http://old-releases.ubuntu.com intrepid/universe Packages
Hit http://old-releases.ubuntu.com intrepid/multiverse Packages
Hit http://old-releases.ubuntu.com intrepid/main Sources
Hit http://old-releases.ubuntu.com intrepid/restricted Sources
Hit http://old-releases.ubuntu.com intrepid/universe Sources
Hit http://old-releases.ubuntu.com intrepid/multiverse Sources
Ign http://deb.linuxmce.org 20dev_ubuntu/main Packages
Hit http://old-releases.ubuntu.com intrepid-updates/main Packages
Hit http://old-releases.ubuntu.com intrepid-updates/restricted Packages
Hit http://old-releases.ubuntu.com intrepid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com intrepid-security/main Packages
Hit http://deb.linuxmce.org intrepid/beta2 Packages
Hit http://old-releases.ubuntu.com intrepid-security/restricted Packages
Get:2 http://old-releases.ubuntu.com intrepid-security/universe Packages [90.9kB]
Hit http://deb.linuxmce.org 20dev_ubuntu/main Packages
Hit http://old-releases.ubuntu.com intrepid-security/multiverse Packages
Fetched 90.9kB in 2s (40.3kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  libtcltk-ruby1.8
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1731kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  libtcltk-ruby1.8
Authentication warning overridden.
Err http://old-releases.ubuntu.com intrepid-security/universe libtcltk-ruby1.8 1.8.7.72-1ubuntu0.2
  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/pool/universe/r/ruby1.8/libtcltk-ruby1.8_1.8.7.72-1ubuntu0.2_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@dcerouter:/etc/apt#

```

---

### Post by wyBTUiRt on 2010-11-06
Apparently the issue is not limited to just the one file.

See [http://forum.linuxmce.org/index.php?topic=10917.0](http://forum.linuxmce.org/index.php?topic=10917.0) for additional missing files.

---

