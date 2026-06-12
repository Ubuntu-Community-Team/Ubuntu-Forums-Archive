---
title: "sudo apt-get install X: MaxReports is reached already"
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by Kdar on 2012-08-19
I was trying to install new package:
```
sudo apt-get install linux-linaro-*-tools
```
or (the one that fails)
```
sudo apt-get install linux-linaro-tools-3.3.0-14-linaro-lt-ux500
``` 

```
The following NEW packages will be installed:
  linux-linaro-tools-3.3.0-14-linaro-lt-ux500
0 upgraded, 1 newly installed, 0 to remove and 181 not upgraded.
12 not fully installed or removed.
Need to get 0 B/265 kB of archives.
After this operation, 516 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 129348 files and directories currently installed.)
Unpacking linux-linaro-tools-3.3.0-14-linaro-lt-ux500 (from .../linux-linaro-tools-3.3.0-14-linaro-lt-ux500_3.3.0-14.14~lt~ci~20120328001941+1332905158~4f72991f_armel.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-linaro-tools-3.3.0-14-linaro-lt-ux500_3.3.0-14.14~lt~ci~20120328001941+1332905158~4f72991f_armel.deb (--unpack):
 trying to overwrite '/usr/bin/perf_3.3.0-14', which is also in package linux-linaro-tools-3.3.0-14-linaro-lt-origen 3.3.0-14.14~lt~ci~20120328001941+1332898407~4f7289db
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-linaro-tools-3.3.0-14-linaro-lt-ux500_3.3.0-14.14~lt~ci~20120328001941+1332905158~4f72991f_armel.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can I fix this problem? Or can I force the install somehow?

I already tried to do what I saw from some other older topics on this:
```
sudo apt-get update
sudo apt-get -f install
```
But it didn't help.
This is not exactly on Ubuntu platform, since this version of Ubuntu platform is built by Linaro for Pandaboard.. but maybe I could get some help too, I don't know if this is a common error or not.

---

