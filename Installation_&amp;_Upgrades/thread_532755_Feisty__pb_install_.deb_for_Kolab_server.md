---
title: "Feisty : pb install .deb for Kolab server"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by plm4@mac.com on 2007-08-23
Hi,

I have an error message when i'm trying to install the kolabd and kolab-resource-handlers package on my new clean install of feisty. See what is happen:

> dobriyedien:~# aptitude install kolabd
Reading package lists... Done
......................................
Setting up kolab-resource-handlers (0.3.9-20060811-3ubuntu1) ...
dpkg: error processing kolab-resource-handlers (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kolabd:
 kolabd depends on kolab-resource-handlers; however:
  Package kolab-resource-handlers is not configured yet.
dpkg: error processing kolabd (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kolab-resource-handlers
 kolabd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up kolab-resource-handlers (0.3.9-20060811-3ubuntu1) ...
dpkg: error processing kolab-resource-handlers (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kolabd:
 kolabd depends on kolab-resource-handlers; however:
  Package kolab-resource-handlers is not configured yet.
dpkg: error processing kolabd (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kolab-resource-handlers
 kolabd

I have a lot of questions:
    - Is someone have a simple solution
    - I thaught the universe packages were stable
    - Is it a good strategy to install kolab 1.9.4 (2006) ?
      on KOLAB web site the 2.1.0 is the official stable version.

---

### Post by lijntje on 2007-08-24
Same problem here (same month same package)
Did you find a solution?
I tried reinstalling the package, but that resulted in the same error (did only reinstall, not redownload)
I tried dpkg-reconfigure, telling me that kolab-resource-handers is damaged or not completely installed.
Anyone any ideas?

---

### Post by mjerger on 2007-09-12
You will find a solution on [https://bugs.launchpad.net/ubuntu/+source/kolab-resource-handlers/+bug/107343](https://bugs.launchpad.net/ubuntu/+source/kolab-resource-handlers/+bug/107343)

---

