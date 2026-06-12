---
title: "How to install sg3_utils"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2010-07-20
Hi all ,

how to install sg3_utils in ubuntu (10.04) , I tried the following

I downloaded sg3_utils from the site :-http://linux.softpedia.com/progDownl...load-7371.html


sudo dpkg -i sg3-utils_1.29-0.1_i386.deb
Selecting previously deselected package sg3-utils.
(Reading database ... 153436 files and directories currently installed.)
Unpacking sg3-utils (from sg3-utils_1.29-0.1_i386.deb) ...
dpkg: dependency problems prevent configuration of sg3-utils:
sg3-utils depends on libsgutils2-2 (>= 1.29); however:
Version of libsgutils2-2 on system is 1.28-2.
dpkg: error processing sg3-utils (--install):
dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
sg3-utils

How to resolve this dependency error ?

---

