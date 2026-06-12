---
title: "can't install a pkg for &quot;intel&quot; on a &quot;i386&quot; PC"
date: 2005-07-06
forum: Installation &amp; Upgrades
---

### Post by gugus on 2005-07-06
Hi,
I'm tring to install the latest OpenOffice.org2 devel version (SRC680_m113) on my PC (Intel Pentium),
Then I download the file:
```
wget http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m113/Build-1/OOo_SRC680_m113_en-US_native_LinuxIntel_install_deb.tar.gz

```
But when I'm trying to install it:
```
sudo dpkg -i *.deb
```
I have this error message:
```
package architecture (intel) does not match system (i386)
```
I don't understand this error because "intel" and "i386" are the same architecture no ?

---

### Post by gugus on 2005-07-08
I found the solution, I must use this command:
```

sudo dpkg -i --force-architecture *.deb

```

---

