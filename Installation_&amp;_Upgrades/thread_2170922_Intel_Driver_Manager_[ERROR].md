---
title: "Intel Driver Manager [ERROR]"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by alvaromirandacosta on 2013-08-28
I've tryied to instal my drivers with Intel Driver Manager and get that 2 errors:

The following packages have unmet dependencies:

libatk-wrapper-java-jni:i386: Depends: libatk1.0-0 (>= 1.18.0) but 2.8.0-1 is to be installed
                              Depends: libc6 (>= 2.4) but 2.17-0ubuntu5 is to be installed
                              Depends: libglib2.0-0 (>= 2.31.8) but 2.36.0-1ubuntu2 is to be installed
                              Depends: libgtk2.0-0 (>= 2.12.0) but 2.24.17-0ubuntu2 is to be installed
                              Depends: libatk-wrapper-java (>= 0.30.4-0ubuntu4) but 0.30.4-0ubuntu4 is to be installed
_____________________________________________________________________________________________________________________________________________________

Error running transaction: GDBus.Error:org.debian.apt.TransactionFailed: error-dep-resolution-failed: The following packages have unmet dependencies:

libatk-wrapper-java-jni:i386: Depends: libatk1.0-0 (>= 1.18.0) but 2.8.0-1 is to be installed
                              Depends: libc6 (>= 2.4) but 2.17-0ubuntu5 is to be installed
                              Depends: libglib2.0-0 (>= 2.31.8) but 2.36.0-1ubuntu2 is to be installed
                              Depends: libgtk2.0-0 (>= 2.12.0) but 2.24.17-0ubuntu2 is to be installed
                              Depends: libatk-wrapper-java (>= 0.30.4-0ubuntu4) but 0.30.4-0ubuntu4 is to be installed
_____________________________________________________________________________________________________________________________________________________
NOTE: i started using ubuntu yesterday
NOTE: in place of the smiley is a ": o" no space

---

### Post by ibjsb4 on 2013-08-28
Please provide a link to the driver download source and post the make and model of your video card.  

Also what version are you running?  Ubuntu 13.04? Or something else?

---

### Post by alvaromirandacosta on 2013-08-28
**solved**

---

