---
title: "php installation problem (/usr/lib/libxml2.so: undefined reference to `gzopen64')"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by stillwaiting on 2008-01-13
Hi, I'm totally newbie at Ubuntu, and I have the next problem:

Ubuntu version: 
```

root@ubuntu:/# uname --all
Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
root@ubuntu:/# 

```

Configuring php installer:
```

./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql=/usr/local/mysql

```

After that typing:
```

root@ubuntu:/# make

```

It starts doing something and throws

```

/usr/lib/libxml2.so: undefined reference to `gzopen64'
collect2: ld returned 1 exit status
make: *** [sapi/cli/php] 

```

in the end. And I have no any ideas what to do with this. I've tried to change php package (I've tried 5.2.5 and 5.2.4) but the error still appears.

I've spent two days already and I'll be very grateful for any help.

Thank you very much for your interest.

---

### Post by Partyboi2 on 2008-01-13
this might help
[https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045](https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045)

---

### Post by stillwaiting on 2008-01-14
**2Partyboi2:** Thank you for your post.

Yes, I've already read that thread (found it while using google). There are some posts with `fixed` message, but I don't know how to apply it to my situation:
```
** PerJensen  wrote on 2007-10-10**
Fixed !

I removed an old libz from /usr/local/lib and ran ldconfig.

After that 'sudo aptitude full-upgrade' is very busy.

```

Well, first of all, in /usr/local/lib I've found only folder with python, no any libz* files. I remove all libz* files from /usr/lib and run ldconfig and aptitude full-upgrade (under su root), it says that no modifications were made,

```
**Etienne Lepercq  wrote on 2007-11-04:  (permalink)**


Ok, with a irc chan and a good user, I found and this is not a bug :

ldd /usr/lib/libxml2.so.2
        linux-gate.so.1 => (0xffffe000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ec5000)
        **libz.so.1 => /opt/matlab/bin/glnx86/libz.so.1 (0xb7eb4000)**
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e8f000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d45000)
        /lib/ld-linux.so.2 (0x80000000)

As you can see, libz is linked to the matlab one (I recently installed it) and this is the 
cause to my pb... This is the end of 2 days of heavy searches for this problem ! The 
solution is to unset LD_LIBRARY_PATH for the matlab path and add it just when launching 
/ linking to matlab libraries....

```

When I type
 ldd /usr/lib/libxml2.so
it prints:
```
linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7eae000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7e99000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e74000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d2a000)
        /lib/ld-linux.so.2 (0x80000000)

```
And I have no idea what to do with this.:confused:

---

