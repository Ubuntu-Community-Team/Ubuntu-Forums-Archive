---
title: "dpkg 1.15.8.4ubuntu1  - invalid character in version number"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by jjkim5 on 2010-10-29
# sudo dpkg -i vasre-se-1.1.1~Debian_5-i386.deb                                                                                                                                                              

dpkg: error processing vasre-se-1.1.1~Debian_5-i386.deb (--install):
 parse error, in file '/var/lib/dpkg/tmp.ci/control' near line 2 package 'vasre-se':
 error in Version string '1.1.1~Debian_5': invalid character in version number
Errors were encountered while processing:
 vasre-se-1.1.1~Debian_5-i386.deb

I did install same package ok in 10.4 but now after I upgrade to 10.10 I am getting this error.

I have already tried

# sudo dpkg --clear-avail
# sudo aptitude update
# sudo aptitude upgrade

but that didn't help

Any suggestion?

---

### Post by afrodeity on 2010-11-03
try reinstalling the packages.

---

