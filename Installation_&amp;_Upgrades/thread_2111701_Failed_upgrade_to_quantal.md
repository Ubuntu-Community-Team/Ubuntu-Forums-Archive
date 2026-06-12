---
title: "Failed upgrade to quantal"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by lingenfr on 2013-02-02
I attempted to upgrade from 12.04 to 12.10 today. No joy. The upgrade seemed to complete and I followed the instructions to restart. Unfortunately, the upgrade seems to be stuck due to a problem with libmagickcore4. I have done several hours of googling and have tried a variety of solutions from the command line and with synaptic, but no joy. For example, if I run "sudo apt-get install -f" I get:

dpkg: warning: parsing file '/var/lib/dpkg/status' near line 1158 package 'libmagickcore4':
 'Depends' field, reference to 'libc6': error in version: version number does not start with digit
dpkg: error: parsing file '/var/lib/dpkg/status' near line 10334 package 'python2.5-minimal':
 error in Version string '524288:': nothing after colon in version number
E: Sub-process /usr/bin/dpkg returned an error code (2)

I can't figure out how to clear the error to let the upgrade complete. Any assistance is appreciated.

---

### Post by lingenfr on 2013-02-02
I tried booting to recovery and:

Enabling networking: Fails
Fixing dependencies: Fails
Files System Check:  Fails

All of those options hang. FSCK checks both drives with less that 5% non-contiguous and then hangs. I do have a separate /home partition. My wife would cut me if I lost her stuff. If possible, I would like to correct the error and complete the dist upgrade. I don't really have time to do a clean install and reinstall all her programs today.

---

### Post by lingenfr on 2013-02-03
Still need help.

---

