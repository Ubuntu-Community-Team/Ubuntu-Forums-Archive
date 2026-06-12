---
title: "FLASH: npviewer.bin crashing"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Grimhound on 2008-10-03
Just installed Flash for Intrepid, and now npviewer.bin is crashing whenever I try to access a Flash site. Says I'm using a nongenuine Ubuntu package when I try to report it.

---

### Post by wilsong on 2008-10-03
This bug is known and been reported on launchpad, i just wouldnt worry about it or hit dont report again because its definitely out there :) fix should be out sometime! Thanks for asking !:)

---

### Post by wilsong on 2008-10-03
If you would like to read about it though here you go [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/178038](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/178038)

---

### Post by Wubuntish on 2008-10-04
Problem occurs on AMD64 systems.

```
ldd /lib32/libnss_ldap.so.2
```

Returns "libgnutls.so.26 => Not Found", even though libgnutls26 is installed.

You'll need to install i386 binary:

```

wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
getlibs -l libgnutls.so.26
```

And restart FireFox. Works on my Dell M1530.

---

