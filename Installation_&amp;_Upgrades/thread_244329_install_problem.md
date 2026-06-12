---
title: "install problem"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by dannykaye on 2006-08-26
I just installed ubuntu 6.06 LTS - the Dapper Drake - released in June 2006 from a cover disk on linux format magazine. all was well until I installed gcc and accidentally installed a later version of gcc 4.0 base than the other files I installed. I now get the following when I run apt-get install -f

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
  cpp-4.0: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
  gcc-4.0: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
  lib64gcc1: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
  libgcc1: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
  libstdc++6: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

how can I correct this, none of the available install/remove packages will work because of this.

Danny

---

### Post by meng on 2006-08-26
Try
sudo apt-get remove gcc-4.0-base

---

### Post by dannykaye on 2006-08-26
sudo apt-get remove gcc-4.0-base

has no effect on the problem, I get essentially the same message

---

### Post by meng on 2006-08-26
Can you describe how you managed to get that version installed in the first place?

---

