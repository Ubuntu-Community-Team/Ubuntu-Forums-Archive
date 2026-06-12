---
title: "Upgrade to 9.10 from 9.04 failed"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by henrismail on 2010-01-24
I tried to upgrade from 9.04 64 bit to 9.10 64, but the update manager crashed. If i try again it says to preform an partial update, it then says
 	```

Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Use of uninitialized value in subroutine entry at /usr/share/perl5/Debconf/Encoding.pm line 65, <> line 1436.
Extracting templates from packages: 89%

dpkg: `ldconfig' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin

```


repeatedly
it then says;

Could not install the upgrades
```

The upgrade is now aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a). 
```

After that it claims that there upgrade is done but there are errors. 

There are three broken packages libc6 libc6-dev libc6-i386

---

