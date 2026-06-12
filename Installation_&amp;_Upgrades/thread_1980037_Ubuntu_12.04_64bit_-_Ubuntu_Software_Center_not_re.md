---
title: "Ubuntu 12.04 64bit - Ubuntu Software Center not repairing prozilla failed packages"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by absoluteajk on 2012-05-14
**Hi, I'm a beginner at using linux/ubuntu. I am using Ubuntu 12.04 64-bit with Gnome 3. I've tried installing prozilla using PPA repositories. It didn't install and gave me the following error message: **

Unpacking prozilla (from .../prozilla_2.0.4~precisebuild1-0tahutek1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/prozilla_2.0.4~precisebuild1-0tahutek1_amd64.deb (--unpack):
trying to overwrite '/usr/share/locale/locale.alias', which is also in package locales 2.13+git20120306-3
Errors were encountered while processing:
/var/cache/apt/archives/prozilla_2.0.4~precisebuild1-0tahutek1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

**I tried opening Ubuntu Software Center and repairing the packages, but it failed and gave me this:**

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 208327 files and directories currently installed.)
Unpacking prozilla (from .../prozilla_2.0.4~precisebuild1-0tahutek1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/prozilla_2.0.4~precisebuild1-0tahutek1_amd64.deb (--unpack):
trying to overwrite '/usr/share/locale/locale.alias', which is also in package locales 2.13+git20120306-3
No apport report written because MaxReports is reached already
Errors were encountered while processing:
/var/cache/apt/archives/prozilla_2.0.4~precisebuild1-0tahutek1_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of apt-proz:
apt-proz depends on prozilla; however:
Package prozilla is not installed.
dpkg: error processing apt-proz (--configure):
dependency problems - leaving unconfigured

If anyone can help I'd appreciate it. -Adam

---

### Post by zvacet on 2012-05-14
```
sudo dpkg --configure -a
```

---

### Post by absoluteajk on 2012-05-14
**putting in that code gave back this: **

dpkg: dependency problems prevent configuration of apt-proz:
 apt-proz depends on prozilla; however:
  Package prozilla is not installed.
dpkg: error processing apt-proz (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apt-proz

**nevermind, I fixed it, I had to sudo apt-get purge apt-proz, and then installed ppa-purge to removed all of prozilla**

---

