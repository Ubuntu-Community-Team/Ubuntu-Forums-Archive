---
title: "mod_ntlm in Ubuntu 9.10 Server x86"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by DJNova on 2009-12-29
Hello,
 
I'm new in this community and I don't find any solution in the web.
 
I want to install the mod_ntlm for apache. I downloaded mod_ntlm from [http://modntlm.sourceforge.net/](http://modntlm.sourceforge.net/) and followed the instructions. But I always receive following error, and I don't know how to fix it.
 
```

make
apxs2 -c -o mod_ntlm.so -Wc,-shared mod_ntlm.c
/usr/share/apr-1.0/build/libtool --silent --mode=compile --tag=disable-static i486-linux-gnu-gcc -prefer-pic -DLINUX=2 -D_FORTIFY_SOURCE=2 -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -D_REENTRANT -I/usr/include/apr-1.0 -I/usr/include/openssl -I/usr/include/xmltok -pthread     -I/usr/include/apache2  -I/usr/include/apr-1.0   -I/usr/include/apr-1.0  -shared  -c -o mod_ntlm.lo mod_ntlm.c && touch mod_ntlm.slo
mod_ntlm.c:43: warning: conflicting types for built-in function âlogâ
mod_ntlm.c: In function âlogâ:
mod_ntlm.c:53: warning: format not a string literal and no format arguments
In file included from mod_ntlm.c:86:
ntlmssp.inc.c: In function ântlm_msg3_getusernameâ:
ntlmssp.inc.c:306: warning: cast from pointer to integer of different size
In file included from mod_ntlm.c:107:
smbval/smblib.inc.c: At top level:
smbval/smblib.inc.c:25: error: static declaration of âSMBlib_errnoâ follows non-static declaration
smbval/smblib-priv.h:668: note: previous declaration of âSMBlib_errnoâ was here
smbval/smblib.inc.c:26: error: static declaration of âSMBlib_SMB_Errorâ follows non-static declaration
smbval/smblib-priv.h:669: note: previous declaration of âSMBlib_SMB_Errorâ was here
smbval/smblib.inc.c:35: error: static declaration of âSMBlib_Stateâ follows non-static declaration
smbval/smblib-priv.h:665: note: previous declaration of âSMBlib_Stateâ was here
apxs:Error: Command failed with rc=65536
.
make: *** [mod_ntlm.so] Error 1

```
Apache has been installed during the installation of Ubuntu and the make file has been edited that it fits to installed components. for example: apxs => apxs2
 
Does anyone can help me?!
 
Thanks, Mike!

---

### Post by jsgaarde on 2010-11-12
Solution can be found here:

[http://wiki.bestpractical.com/view/NtlmAuthentication](http://wiki.bestpractical.com/view/NtlmAuthentication)

---

