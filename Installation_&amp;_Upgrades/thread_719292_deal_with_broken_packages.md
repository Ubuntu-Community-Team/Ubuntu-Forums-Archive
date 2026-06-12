---
title: "deal with broken packages"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by apecar67 on 2008-03-09
Hi there, I trying to remove a broken package that (also)  I converted from RPM to DEB package before. I do that because I want to use my USB token on my linux.

when I trying to remove the package I got this error. I also tried with --force-all but without success. anyone have any idea how to remove this package?
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
thanks all
ape

root@hayabuxa:/home/apecar/Desktop/eToken_PKI_Client_4_55_Linux# dpkg --remove --force-remove-reinstreq pkiclient-full
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 159813 files and directories currently installed.)
Removing pkiclient-full ...
/var/lib/dpkg/info/pkiclient-full.prerm: 4: Syntax error: Bad fd number
dpkg: error processing pkiclient-full (--remove):
 subprocess pre-removal script returned error exit status 2
Warning: pcsc-lite installation not found (maybe installed from source?)
Checking installation of pcsc from source... None.
/etc/init.d/eTCacheMarker: line 46: /usr/bin/eTCacheMarker: No such file or directory
/var/lib/dpkg/info/pkiclient-full.postinst: 87: Syntax error: Bad fd number
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 pkiclient-full

---

