---
title: "Creating bootable disc"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by enstardavid on 2007-08-29
Hi,

I have downloaded Ubuntu 7.04 from a USA mirror. Download seems fine. Ran it against winMd5Sum and the checksum tallies OK

BUT when I burn the iso and try to install I get an error:

ISOLINUX 3.11 Debian-2007-03-12 isolinux: Image checksum error, sorry ...

I have tried different computers and burners - same problem. Hmm.

Looking on the installer disc I see that there is a file called md5sum.txt

**Q1.** Should this file contain the same md5 sum as is listed here? [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
(mine does not match).

**Q2.** Also - how can I check the CD ? I am in a Windows environment and this is the first box we are setting up for Linux - the page [https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)
assumes that you already have a ubuntu installation - kind of circular problem here.

Thanks

---

### Post by Pumalite on 2007-08-29
Your md5sum apparently did not match, therefore iso is corrupt, therefore you need new iso. md5sum is compared to md5sum of same iso from site where you dowloaded from.

---

