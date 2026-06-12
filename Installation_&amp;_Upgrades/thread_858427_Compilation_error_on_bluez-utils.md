---
title: "Compilation error on bluez-utils"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by mariecpu on 2008-07-13
Hello.  I'm having a bit of trouble compiling bluez-utils using the .tar.gz source.  I need to run this configuration to enable all the tools (dfutool, etc.)
```
g@cpu:~/Desktop/bluez/bluez-utils-3.36$ ./configure --prefix=/g --mandir=/g/share/man --sysconfdir=/etc --localstatedir=/var --libexecdir=/lib --enable-all

```

```
g@cpu:~/Desktop/bluez/bluez-utils-3.36$ sudo make && make install

```

Here's the errors I ended with, I'm not sure what's wrong:
```
make[2]: Entering directory `/home/g/Desktop/bluez/bluez-utils-3.36/hcid'
make  all-am
make[3]: Entering directory `/home/g/Desktop/bluez/bluez-utils-3.36/hcid'
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I../sdpd   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I../eglib  -I../gdbus -DPLUGINDIR=\""/g/lib/bluetooth/plugins"\" -Wall -O2 -D_FORTIFY_SOURCE=2 -fPIE -MT security.o -MD -MP -MF .deps/security.Tpo -c -o security.o security.c
security.c: In function ‘link_key_request’:
security.c:279: error: storage size of ‘req’ isn’t known
security.c:291: error: ‘HCIGETAUTHINFO’ undeclared (first use in this function)
security.c:291: error: (Each undeclared identifier is reported only once
security.c:291: error: for each function it appears in.)
security.c:279: warning: unused variable ‘req’
make[3]: *** [security.o] Error 1
make[3]: Leaving directory `/home/g/Desktop/bluez/bluez-utils-3.36/hcid'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/g/Desktop/bluez/bluez-utils-3.36/hcid'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/g/Desktop/bluez/bluez-utils-3.36'
make: *** [all] Error 2

```

I'm quite new to this, so any help would be greatly appreciated.

Thank you!

---

### Post by mariecpu on 2008-07-13
I just ran a make check, and here's what I came up with:

```
make[1]: Entering directory `/home/g/Desktop/bluez/bluez-utils-3.36/hcid'
make  check-am
make[2]: Entering directory `/home/g/Desktop/bluez/bluez-utils-3.36/hcid'
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I../sdpd   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I../eglib  -I../gdbus -DPLUGINDIR=\""/g/lib/bluetooth/plugins"\" -Wall -O2 -D_FORTIFY_SOURCE=2 -fPIE -MT security.o -MD -MP -MF .deps/security.Tpo -c -o security.o security.c
security.c: In function ‘link_key_request’:
security.c:279: error: storage size of ‘req’ isn’t known
security.c:291: error: ‘HCIGETAUTHINFO’ undeclared (first use in this function)
security.c:291: error: (Each undeclared identifier is reported only once
security.c:291: error: for each function it appears in.)
security.c:279: warning: unused variable ‘req’
security.c: At top level:
**security.c:1037: fatal error: opening dependency file .deps/security.Tpo: Permission denied**
compilation terminated.
make[2]: *** [security.o] Error 1
make[2]: Leaving directory `/home/g/Desktop/bluez/bluez-utils-3.36/hcid'
make[1]: *** [check] Error 2
make[1]: Leaving directory `/home/g/Desktop/bluez/bluez-utils-3.36/hcid'
make: *** [check-recursive] Error 1

```

Any thoughts?

---

### Post by mariecpu on 2008-07-16
Here's a pastebin of the whole bit:
[http://pastebin.ca/1073779](http://pastebin.ca/1073779)

I think I'm doing it right.

---

