---
title: "MFC-7420 Scanner installation problem"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by yoog on 2011-08-13
I have installed Ubuntu 11.04, 64 bit and now I am trying to install/configure MFC-7420 scanner part (printer works fine). I tried to follow the steps listed at [http://ubuntuforums.org/archive/index.php/t-590793.html](http://ubuntuforums.org/archive/index.php/t-590793.html), but I don't have /etc/udev/rules.d/45-libsane.rules file to edit and can not continue with the remaining steps of the guide.

I also tried to follow the steps provided by the Brother Solution Center [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html). I have downloaded brscan2 64 bit and installed without error but when I tried to install the brscan-skey-0.2.1-3.amd64.deb using >sudo dpkg -i --force-all brscan-skey-0.2.1-3.amd64.deb I get the following error:
****************************************************************************************************
sudo dpkg -i --force-all brscan-skey-0.2.1-3.amd64.deb
[sudo] password for aUser: 
dpkg: warning: overriding problem because --force enabled:
 package architecture (amd64) does not match system (i386)
(Reading database ... 149212 files and directories currently installed.)
Preparing to replace brscan-skey:amd64 0.2.1-3 (using brscan-skey-0.2.1-3.amd64.deb) ...
Unpacking replacement brscan-skey:amd64 ...
dpkg: dependency problems prevent configuration of brscan-skey:amd64:
 brscan-skey:amd64 depends on libc6 (>= 2.3.4-1).
dpkg: error processing brscan-skey:amd64 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 brscan-skey:amd64
*************************************************************************************************

Which dependencies am I missing? or What am I doing wrong?

---

### Post by yoog on 2011-08-14
Any 1?

---

