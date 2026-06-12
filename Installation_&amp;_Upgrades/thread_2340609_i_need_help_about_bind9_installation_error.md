---
title: "i need help about bind9 installation error"
date: 2016-10-20
forum: Installation &amp; Upgrades
---

### Post by sherluck007 on 2016-10-20
hi guys. 
iam new to ubuntu iam trying to install bind9 but it shows hthis massage i searched many links but still i did'nt fix this error anybudy please help me..

The following packages have unmet dependencies:
 bind9 : Depends: libbind9-140 (= 1:9.10.3.dfsg.P4-8) but 1:9.10.3.dfsg.P4-8ubuntu1.1 is to be installed
         Depends: libdns162 (= 1:9.10.3.dfsg.P4-8) but 1:9.10.3.dfsg.P4-8ubuntu1.1 is to be installed
         Depends: libisc160 (= 1:9.10.3.dfsg.P4-8) but 1:9.10.3.dfsg.P4-8ubuntu1.1 is to be installed
         Depends: libisccc140 (= 1:9.10.3.dfsg.P4-8) but 1:9.10.3.dfsg.P4-8ubuntu1.1 is to be installed
         Depends: libisccfg140 (= 1:9.10.3.dfsg.P4-8) but 1:9.10.3.dfsg.P4-8ubuntu1.1 is to be installed
         Depends: liblwres141 (= 1:9.10.3.dfsg.P4-8) but 1:9.10.3.dfsg.P4-8ubuntu1.1 is to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by SeijiSensei on 2016-10-20
Did you run "sudo apt-get update" before "sudo apt-get install bind9"?  If not, try that.

---

### Post by sherluck007 on 2016-11-05
thanks man my problem has been sovled.

---

