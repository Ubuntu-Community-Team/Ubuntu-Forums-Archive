---
title: "error in Version string"
date: 2011-12-06
forum: Installation &amp; Upgrades
---

### Post by zzigahertz on 2011-12-06
I'm trying to install a linmodem driver.  Installation fails with the message:  "error in Version string"

The message in full:  "dpkg: error processing /home/fernando/Downloads/hsfmodem_7.43.00.01full_k2.6.12_9_386_ubuntu_i386.deb/hsfmodem_7.43.00.01full_k2.6.12_9_386_ubuntu_i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 2 package 'hsfmodem':
 error in Version string '7.43.00.01full_k2.6.12_9_386_ubuntu': invalid character in version number"

What is the error, and how can I fix it?

Thanks,
zzigahertz

---

### Post by lechien73 on 2011-12-06
I remember reading that newer versions of dpkg don't like underscores in version numbers and throw the file out because of that.

A potential fix would be to use ```
dkpg-deb -x
``` to extract the files, and ```
dpkg-deb -e
``` to extract the control file.

You could then change the version number in the control file, repackage it and try installing it again.

Alternatively, you could try building hfsmodem from source. This link may be helpful: [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

---

