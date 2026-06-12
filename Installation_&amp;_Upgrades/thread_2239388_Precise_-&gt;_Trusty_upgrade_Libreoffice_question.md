---
title: "Precise -&gt; Trusty upgrade Libreoffice question"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2014-08-13
I am running 14.04.1 x64 with Gnome Flashback.  My question concerns some Libreoffice entries in /opt.  When I upgraded from 12.04.5, Libreoffice 4.2.4.2 was installed.  Libreoffice 3.3 was not removed.  Are the Libreoffice items in /opt part of 3.3?  I used Synaptic to remove completely 3.3, but these items seem to be outliers from 3.3.  4.2.4.2 seems to be installed in /usr.  Is there any way to tell?

---

### Post by ajgreeny on 2014-08-13
Have you at some time in the past installed LO using the downloaded installer of .deb files direct from LO?
That will have, or at least it used to do it that way, put all the package's files in /opt rather than the more standard arrangement when installing from repos.

What output do you get from commands ```
whereis libreoffice
which libreoffice
``` and which number version opens when you use command **libreoffice**?

---

### Post by cscj01 on 2014-08-13
No, I have only installed Libreoffice through Synaptic.```
whereis libreoffice
libreoffice: /usr/bin/libreoffice /etc/libreoffice /usr/lib/libreoffice /usr/bin/X11/libreoffice /usr/share/libreoffice /usr/share/man/man1/libreoffice.1.gz
``````
which libreoffice
/usr/bin/libreoffice
```LO 4.2.4.2 opens with the "libreoffice" command.

So I presume it is safe to delete the Libreoffice folder in /opt?

---

### Post by ajgreeny on 2014-08-14
I should think it's safe to remove it, but lets see the output of ```
ls -l /opt/libreoffice
``` first to see what it contains, and also look in your running LO **Tools ->Options ->Libreoffice ->Paths** to see if for some reason your configs for LO are sitting in /opt instead of where they should be in your home.

---

### Post by cscj01 on 2014-08-14
All of my LO paths are in home, so that is okay.

Here's the command:```
ls -l /opt/libreoffice
total 8
drwxr-xr-x 4 root root 4096 Aug 12 23:40 share
drwxr-xr-x 5 root root 4096 Feb  8  2011 ure
```
I fould a linked folder in /usr/lib/libreoffice named ure-link.  Here is it's target:```
ls -al /usr/lib/libreoffice/ure-link
lrwxrwxrwx 1 root root 6 Jun 18 06:31 /usr/lib/libreoffice/ure-link -> ../ure
```

---

### Post by ajgreeny on 2014-08-15
> **cscj01 said:**
> All of my LO paths are in home, so that is okay.

Here's the command:```
ls -l /opt/libreoffice
total 8
drwxr-xr-x 4 root root 4096 Aug 12 23:40 share
drwxr-xr-x 5 root root 4096 Feb  8  2011 ure
```
I fould a linked folder in /usr/lib/libreoffice named ure-link.  Here is it's target:```
ls -al /usr/lib/libreoffice/ure-link
lrwxrwxrwx 1 root root 6 Jun 18 06:31 /usr/lib/libreoffice/ure-link -> ../ure
```
OK, so what is in those two folders in /opt/libreoffice?
I forgot the -R (recursive) option so now try command ```
ls -lR /opt/libreoffice
```

---

### Post by cscj01 on 2014-08-15
Here is the command results: ```
ls -lR /opt/libreoffice
/opt/libreoffice:
total 8
drwxr-xr-x 4 root root 4096 Aug 12 23:40 share
drwxr-xr-x 5 root root 4096 Feb  8  2011 ure

/opt/libreoffice/share:
total 8
drwxr-xr-x 3 root root 4096 Feb  7  2011 prereg
drwxr-xr-x 3 root root 4096 Feb  7  2011 uno_packages

/opt/libreoffice/share/prereg:
total 4
drwxr-xr-x 3 root root 4096 Feb  8  2011 bundled

/opt/libreoffice/share/prereg/bundled:
total 20
-rw-r--r-- 1 root root 12288 Feb  8  2011 extensions.db
-rw-r--r-- 1 root root     1 Feb  8  2011 lastsynchronized
drwxr-xr-x 9 root root  4096 Feb  7  2011 registry

/opt/libreoffice/share/prereg/bundled/registry:
total 28
drwxr-xr-x  2 root root 4096 Feb  7  2011 com.sun.star.comp.deployment.bundle.PackageRegistryBackend
drwxr-xr-x  2 root root 4096 Feb  8  2011 com.sun.star.comp.deployment.component.PackageRegistryBackend
drwxr-xr-x 14 root root 4096 Feb  8  2011 com.sun.star.comp.deployment.configuration.PackageRegistryBackend
drwxr-xr-x  2 root root 4096 Feb  7  2011 com.sun.star.comp.deployment.executable.PackageRegistryBackend
drwxr-xr-x  4 root root 4096 Feb  8  2011 com.sun.star.comp.deployment.help.PackageRegistryBackend
drwxr-xr-x  2 root root 4096 Feb  7  2011 com.sun.star.comp.deployment.script.PackageRegistryBackend
drwxr-xr-x  2 root root 4096 Feb  7  2011 com.sun.star.comp.deployment.sfwk.PackageRegistryBackend

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend:
total 12
-rw-r--r-- 1 root root 11230 Feb  8  2011 backenddb.xml

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend:
total 196
-rw-r--r-- 1 root root  2578 Feb  8  2011 backenddb.xml
-rw-r--r-- 1 root root 42496 Feb  8  2011 common_.rdb
-rw-r--r-- 1 root root 42496 Feb  8  2011 common.rdb
-rw-r--r-- 1 root root   142 Feb  8  2011 Linux_X86_64rc
-rw-r--r-- 1 root root 48128 Feb  8  2011 Linux_X86_64_.rdb
-rw-r--r-- 1 root root 48128 Feb  8  2011 Linux_X86_64.rdb
-rw-r--r-- 1 root root   246 Feb  8  2011 unorc

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend:
total 72
-rw-r--r-- 1 root root     0 Feb  7  2011 3OfAC3
drwxr-xr-x 2 root root  4096 Feb  7  2011 3OfAC3_
-rw-r--r-- 1 root root     0 Feb  8  2011 3U6kNP
drwxr-xr-x 2 root root  4096 Feb  8  2011 3U6kNP_
-rw-r--r-- 1 root root 11248 Feb  8  2011 backenddb.xml
-rw-r--r-- 1 root root     0 Feb  7  2011 bwe3e7
drwxr-xr-x 2 root root  4096 Feb  7  2011 bwe3e7_
-rw-r--r-- 1 root root     0 Feb  7  2011 cK4vx8
drwxr-xr-x 2 root root  4096 Feb  7  2011 cK4vx8_
-rw-r--r-- 1 root root  3332 Feb  8  2011 configmgr.ini
-rw-r--r-- 1 root root     0 Feb  7  2011 DrI9nz
drwxr-xr-x 2 root root  4096 Feb  7  2011 DrI9nz_
-rw-r--r-- 1 root root     0 Feb  8  2011 H6UxRZ
drwxr-xr-x 2 root root  4096 Feb  8  2011 H6UxRZ_
-rw-r--r-- 1 root root     0 Feb  7  2011 JsW2hn
drwxr-xr-x 2 root root  4096 Feb  7  2011 JsW2hn_
-rw-r--r-- 1 root root     0 Feb  7  2011 nDQbEI
drwxr-xr-x 2 root root  4096 Feb  7  2011 nDQbEI_
-rw-r--r-- 1 root root     0 Feb  7  2011 nf05It
drwxr-xr-x 2 root root  4096 Feb  7  2011 nf05It_
-rw-r--r-- 1 root root 12288 Feb  7  2011 registered_packages.db
-rw-r--r-- 1 root root     0 Feb  7  2011 Rji3i3
drwxr-xr-x 2 root root  4096 Feb  7  2011 Rji3i3_
-rw-r--r-- 1 root root     0 Feb  7  2011 tENnmv
drwxr-xr-x 2 root root  4096 Feb  7  2011 tENnmv_
-rw-r--r-- 1 root root     0 Feb  8  2011 zVsYqi
drwxr-xr-x 2 root root  4096 Feb  8  2011 zVsYqi_

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/3OfAC3_:
total 4
-rw-r--r-- 1 root root 2015 Feb  7  2011 dictionaries.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/3U6kNP_:
total 4
-rw-r--r-- 1 root root 2015 Feb  8  2011 dictionaries.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/bwe3e7_:
total 8
-rw-r--r-- 1 root root 4125 Feb  7  2011 dictionaries.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/cK4vx8_:
total 12
-rw-r--r-- 1 root root 11036 Feb  7  2011 Addons.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/DrI9nz_:
total 4
-rw-r--r-- 1 root root 478 Feb  7  2011 Paths.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/H6UxRZ_:
total 8
-rw-r--r-- 1 root root 4125 Feb  8  2011 dictionaries.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/JsW2hn_:
total 4
-rw-r--r-- 1 root root 874 Feb  7  2011 dictionaries.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/nDQbEI_:
total 4
-rw-r--r-- 1 root root 638 Feb  7  2011 Paths.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/nf05It_:
total 8
-rw-r--r-- 1 root root 6914 Feb  7  2011 OptionsDialog.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/Rji3i3_:
total 472
-rw-r--r-- 1 root root 479800 Feb  7  2011 SunPresentationMinimizer.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/tENnmv_:
total 4
-rw-r--r-- 1 root root 3323 Feb  7  2011 Filter.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/zVsYqi_:
total 4
-rw-r--r-- 1 root root 874 Feb  8  2011 dictionaries.xcu

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend:
total 4
-rw-r--r-- 1 root root 238 Feb  8  2011 backenddb.xml

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend:
total 12
-rw-r--r-- 1 root root    0 Feb  8  2011 2Bn4iK
drwxr-xr-x 3 root root 4096 Feb  8  2011 2Bn4iK_
-rw-r--r-- 1 root root  734 Feb  8  2011 backenddb.xml
-rw-r--r-- 1 root root    0 Feb  7  2011 TLwtvs
drwxr-xr-x 3 root root 4096 Feb  7  2011 TLwtvs_

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/2Bn4iK_:
total 4
drwxr-xr-x 3 root root 4096 Feb  8  2011 en

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/2Bn4iK_/en:
total 20
-rw-r--r-- 1 root root  508 Feb  8  2011 help.db_
-rw-r--r-- 1 root root    0 Feb  8  2011 help.ht_
drwxr-xr-x 2 root root 4096 Feb  8  2011 help.idxl
-rw-r--r-- 1 root root 4863 Feb  8  2011 help.jar
-rw-r--r-- 1 root root  236 Feb  8  2011 help.key_

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/2Bn4iK_/en/help.idxl:
total 12
-rw-r--r-- 1 root root 4089 Feb  8  2011 _0.cfs
-rw-r--r-- 1 root root   45 Feb  8  2011 segments_3
-rw-r--r-- 1 root root   20 Feb  8  2011 segments.gen

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/TLwtvs_:
total 4
drwxr-xr-x 3 root root 4096 Feb  7  2011 en

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/TLwtvs_/en:
total 20
-rw-r--r-- 1 root root  508 Feb  7  2011 help.db_
-rw-r--r-- 1 root root    0 Feb  7  2011 help.ht_
drwxr-xr-x 2 root root 4096 Feb  7  2011 help.idxl
-rw-r--r-- 1 root root 4863 Feb  7  2011 help.jar
-rw-r--r-- 1 root root  236 Feb  7  2011 help.key_

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/TLwtvs_/en/help.idxl:
total 12
-rw-r--r-- 1 root root 4089 Feb  7  2011 _0.cfs
-rw-r--r-- 1 root root   45 Feb  7  2011 segments_3
-rw-r--r-- 1 root root   20 Feb  7  2011 segments.gen

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend:
total 4
-rw-r--r-- 1 root root 319 Feb  8  2011 backenddb.xml

/opt/libreoffice/share/prereg/bundled/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend:
total 0

/opt/libreoffice/share/uno_packages:
total 4
drwxr-xr-x 3 root root 4096 Feb  8  2011 cache

/opt/libreoffice/share/uno_packages/cache:
total 4
drwxr-xr-x 2 root root 4096 Feb  7  2011 uno_packages

/opt/libreoffice/share/uno_packages/cache/uno_packages:
total 0

/opt/libreoffice/ure:
total 12
drwxr-xr-x 2 root root 4096 Feb  8  2011 bin
drwxr-xr-x 2 root root 4096 Feb  8  2011 lib
drwxr-xr-x 4 root root 4096 Feb  8  2011 share

/opt/libreoffice/ure/bin:
total 388
-r-xr-xr-x 1 root root  15504 Jan 19  2011 javaldx
lrwxrwxrwx 1 root root     10 Feb  8  2011 regcomp -> startup.sh
-r-xr-xr-x 1 root root 131248 Jan 19  2011 regcomp.bin
-r-xr-xr-x 1 root root  15520 Jan 19  2011 regmerge
-r-xr-xr-x 1 root root  12312 Jan 19  2011 regview
-r-xr-xr-x 1 root root   1829 Jan 19  2011 startup.sh
lrwxrwxrwx 1 root root     10 Feb  8  2011 uno -> startup.sh
-r-xr-xr-x 1 root root 204584 Jan 19  2011 uno.bin
-r--r--r-- 1 root root    124 Jan 19  2011 versionrc

/opt/libreoffice/ure/lib:
total 8464
-r--r--r-- 1 root root   66792 Jan 19  2011 acceptor.uno.so
-r--r--r-- 1 root root  807496 Jan 19  2011 bootstrap.uno.so
-r--r--r-- 1 root root   54920 Jan 19  2011 bridgefac.uno.so
-r--r--r-- 1 root root   60776 Jan 19  2011 connector.uno.so
-r--r--r-- 1 root root  144520 Jan 19  2011 introspection.uno.so
-r--r--r-- 1 root root   50504 Jan 19  2011 invocadapt.uno.so
-r--r--r-- 1 root root   79344 Jan 19  2011 invocation.uno.so
-r--r--r-- 1 root root   37936 Jan 19  2011 javaloader.uno.so
-r--r--r-- 1 root root  132760 Jan 19  2011 javavm.uno.so
-r--r--r-- 1 root root    1798 Jan 19  2011 JREProperties.class
-r--r--r-- 1 root root     367 Jan 19  2011 jvmfwk3rc
-r--r--r-- 1 root root   17592 Jan 19  2011 libaffine_uno_uno.so
-r--r--r-- 1 root root   63488 Jan 19  2011 libgcc3_uno.so
-r--r--r-- 1 root root   55440 Jan 19  2011 libgcc_s.so.1
-r--r--r-- 1 root root  144904 Jan 19  2011 libjava_uno.so
-r--r--r-- 1 root root    9120 Jan 19  2011 libjpipe.so
-r--r--r-- 1 root root    8624 Jan 19  2011 libjuh.so
-r--r--r-- 1 root root  136672 Jan 19  2011 libjuhx.so
-r--r--r-- 1 root root   25672 Jan 19  2011 libjvmaccessgcc3.so.3
-r--r--r-- 1 root root  119176 Jan 19  2011 libjvmfwk.so.3
-r--r--r-- 1 root root   15768 Jan 19  2011 liblog_uno_uno.so
-r--r--r-- 1 root root  114848 Jan 19  2011 libreg.so.3
-r--r--r-- 1 root root   19640 Jan 19  2011 librmcxt.so.3
-r--r--r-- 1 root root  979456 Jan 19  2011 libstdc++.so.6
-r--r--r-- 1 root root  111688 Jan 19  2011 libstore.so.3
-r--r--r-- 1 root root  800160 Jan 19  2011 libuno_cppuhelpergcc3.so.3
-r--r--r-- 1 root root  201456 Jan 19  2011 libuno_cppu.so.3
-r--r--r-- 1 root root   24824 Jan 19  2011 libuno_purpenvhelpergcc3.so.3
-r--r--r-- 1 root root   28600 Jan 19  2011 libuno_salhelpergcc3.so.3
-r--r--r-- 1 root root 2020624 Jan 19  2011 libuno_sal.so.3
-r--r--r-- 1 root root   11536 Jan 19  2011 libunsafe_uno_uno.so
-r--r--r-- 1 root root  157688 Jan 19  2011 liburp_uno.so
-r--r--r-- 1 root root 1308168 Jan 19  2011 libxml2.so.2
-r--r--r-- 1 root root   29512 Jan 19  2011 namingservice.uno.so
-r--r--r-- 1 root root   34000 Jan 19  2011 proxyfac.uno.so
-r--r--r-- 1 root root  143664 Jan 19  2011 reflection.uno.so
-r--r--r-- 1 root root   42024 Jan 19  2011 remotebridge.uno.so
-r--r--r-- 1 root root  132976 Jan 19  2011 stocservices.uno.so
-r--r--r-- 1 root root  182112 Jan 19  2011 streams.uno.so
-r--r--r-- 1 root root   81016 Jan 19  2011 sunjavaplugin.so
-r--r--r-- 1 root root   34408 Jan 19  2011 textinstream.uno.so
-r--r--r-- 1 root root   29976 Jan 19  2011 textoutstream.uno.so
-r--r--r-- 1 root root     403 Jan 19  2011 unorc
-r--r--r-- 1 root root   29584 Jan 19  2011 uuresolver.uno.so

/opt/libreoffice/ure/share:
total 8
drwxr-xr-x 2 root root 4096 Feb  8  2011 java
drwxr-xr-x 2 root root 4096 Feb  8  2011 misc

/opt/libreoffice/ure/share/java:
total 428
-r--r--r-- 1 root root   4206 Jan 19  2011 java_uno.jar
-r--r--r-- 1 root root  55553 Jan 19  2011 juh.jar
-r--r--r-- 1 root root 107629 Jan 19  2011 jurt.jar
-r--r--r-- 1 root root 257599 Jan 19  2011 ridl.jar
-r--r--r-- 1 root root   3679 Jan 19  2011 unoloader.jar

/opt/libreoffice/ure/share/misc:
total 1048
-r--r--r-- 1 root root   1272 Jan 19  2011 javavendors.xml
-r--r--r-- 1 root root 237568 Jan 19  2011 services.rdb
-r--r--r-- 1 root root 829952 Jan 19  2011 types.rdb

```

---

### Post by ajgreeny on 2014-08-15
It still looks as if you can remove all those folders in /opt, but for safety's sake, as I have no idea how they got there, it may be best to start, if you just rename the **/opt/libreoffice** folder as OLD to check that LO (and the rest of your OS and applications) still work properly without them.
```
sudo mv /opt/libreoffice /opt/libreofficeOLD
```

---

### Post by cscj01 on 2014-08-16
> **ajgreeny said:**
> It still looks as if you can remove all those folders in /opt, but for safety's sake, as I have no idea how they got there, it may be best to start, if you just rename the **/opt/libreoffice** folder as OLD to check that LO (and the rest of your OS and applications) still work properly without them.
```
sudo mv /opt/libreoffice /opt/libreofficeOLD
```
Okay, that seems appropriate to me.  I'll do as you recommend.  As soon as I check it out and it works (the power of positive thinking), I'll mark this as solved.  Thank you for your help.  It is most appreciated.

---

### Post by cscj01 on 2014-08-16
Everything seems to be fine, so I am marking this as solved.  Thanks ajgreeny.

---

