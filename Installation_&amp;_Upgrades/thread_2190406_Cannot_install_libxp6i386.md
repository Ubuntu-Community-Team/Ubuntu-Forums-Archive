---
title: "Cannot install libxp6:i386"
date: 2013-11-27
forum: Installation &amp; Upgrades
---

### Post by jfrantzius on 2013-11-27
Hi,

when I try to install libxp6:i386 on my x86_64 Saucy installation, all I get is the error
 [INDENT][COLOR=#000000][FONT=Ubuntu Mono]
 trying to overwrite shared '/usr/share/doc/libxp6/changelog.Debian.gz', which is different from other instances of package libxp6:i386"
[/FONT][/COLOR][/INDENT]
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]This is the full output:
```

~$ sudo apt-get install libxp6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsvnqt7 linux-image-3.8.0-31-generic linux-image-extra-3.8.0-31-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libxp6:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 18,0 kB of archives.
After this operation, 78,8 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libxp6
Authentication warning overridden.
Get:1 http://de.archive.ubuntu.com/ubuntu/ saucy/main libxp6 i386 1:1.0.2-1 [18,0 kB]
Fetched 18,0 kB in 0s (60,1 kB/s) 
(Reading database ... 231983 files and directories currently installed.)
Unpacking libxp6:i386 (from .../libxp6_1%3a1.0.2-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libxp6_1%3a1.0.2-1_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libxp6/changelog.Debian.gz', which is different from other instances of package libxp6:i386
Errors were encountered while processing:
 /var/cache/apt/archives/libxp6_1%3a1.0.2-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Is this maybe due to a bug in packaging?

Thanks for any help,
Jörg

---

### Post by jfrantzius on 2013-12-02
Filed [https://bugs.launchpad.net/ubuntu/+source/libxp/+bug/1256876](https://bugs.launchpad.net/ubuntu/+source/libxp/+bug/1256876) for this one.

---

