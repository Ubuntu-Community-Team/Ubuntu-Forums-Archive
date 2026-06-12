---
title: "Tried to install gtkpod and now everything is broken"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by giruzz on 2007-01-07
Hi,

I tried to install gtkpod_0.99.8-1_i386.deb which requires libgpod0.4.0_0.4.0-1_i386.deb. So I installed the libgpod and...when I did that...I broke my system..

anyone can help me?

sudo apt-get install -f doesn't work and I cannot un-install the old libgpod0.3.2

The following packages have unmet dependencies:
  gtkpod: Depends: libgpod0.4.0 but it is not installable
          Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is installed
  libfontconfig1: Depends: fontconfig-config (= 2.4.1-2) but 2.3.2-7ubuntu2 is installed
  libpango1.0-0: Depends: libpango1.0-common (>= 1.15.2-0ubuntu1) but 1.14.5-0ubuntu1 is installed
                 Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


any suggestions?

thanks

g.

---

