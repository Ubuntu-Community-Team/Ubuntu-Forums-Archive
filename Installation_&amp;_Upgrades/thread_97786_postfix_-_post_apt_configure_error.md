---
title: "postfix - post apt configure error"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by wedge2k on 2005-12-01
First is first: 

Running p4 2.8ht, ubuntu smp kernel, all patched up

When I go to install postfix, i get this:

```
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postfix (2.2.4-1ubuntu2) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
postalias: symbol lookup error: /usr/lib/libpostfix-util.so.1: undefined symbol: db_version_4002
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

so I made usre the libdb-4.2 was installed, it was (even tried a compiled version), reinstalled it for good measure.  Ran ldd on libpostfix-util.so.1.  Got this:

```
sanders@d-lnx005:/usr/lib$ ldd /usr/lib/libpostfix-util.so.1
        linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f3e000)
        libssl.so.0.9.7 => /usr/lib/i686/cmov/libssl.so.0.9.7 (0xb7f0d000)
        libcrypto.so.0.9.7 => /usr/lib/i686/cmov/libcrypto.so.0.9.7 (0xb7e10000)
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7dfb000)
        libdb-4.2.so => /usr/lib/libdb-4.2.so (0xb7d2d000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7d18000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7d05000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7bd6000)
        /lib/ld-linux.so.2 (0x80000000)

```

To me it looks as iff it sees the correct libdb-4.2.so file.  

I then ran *strings /usr/lib/libdb-4.2.so | grep db_version_4002* and it returned the value found.  So obviously everything should be right in the world, but when i run apt-get -f install, i get the error you saw above.  

As anyone else had this problem before?  Its really annoying.   Thanks!

---

