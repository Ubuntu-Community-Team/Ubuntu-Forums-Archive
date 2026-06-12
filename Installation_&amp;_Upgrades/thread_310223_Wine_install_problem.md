---
title: "Wine install problem"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by LinuxLappy on 2006-11-30
# apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
        Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
        Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
        Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
        Depends: libusb-0.1-4 (>= 2:0.1.12) but 2:0.1.10a-22ubuntu1 is to be installed
        Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed
        Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages


any idea on how to fix this? Thanks.

---

### Post by claydoh on 2006-11-30
It looks like you may have some mixed repos in your sources.list. Make sure you have the correct ones for wine (assuming you are trying for the latest from winehq). make sure you have run 'sudo apt-get update' first and try again if you have not done so.

Then copy the text from your /etc/apt/sources.list into a post here, we can find out where it is might be fixed.

---

### Post by LLRNR on 2006-11-30
For an easier Wine install and configuration: [this](http://doc.gwos.org/index.php/Wine) and [this](http://doc.gwos.org/index.php/HowToWine).

LLRNR

---

### Post by LinuxLappy on 2006-11-30
Thanks LLRNR! The links you posted worked perfect. Thanks again.

---

