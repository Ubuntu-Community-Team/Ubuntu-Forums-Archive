---
title: "Software index broken"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by neodorian on 2007-10-04
I'm running the latest Gutsy beta (please move to that forum if it's the proper place) and when I did my daily updates I got the error message that the software index is broken.

I tried running 

```
sudo apt-get install -f 
```

and I got 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gimp
Suggested packages:
  gimp-help-en gimp-help libgimp-perl gimp-data-extras
Recommended packages:
  gimp-gnomevfs gimp-libcurl
The following packages will be upgraded:
  gimp
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/3902kB of archives.
After unpacking 373kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 127870 files and directories currently installed.)
Preparing to replace gimp 2.4.0~rc3-1ubuntu4 (using .../gimp_2.4.0~rc3-1ubuntu5_i386.deb) ...
Unpacking replacement gimp ...
dpkg: error processing /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/share/doc/libgimp2.0/README', which is also in package libgimp2.0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I ran synaptic and filtered by broken packages.  The one giving me problems is gimp-python.

I tried reinstalling it and it still gives me an error that

```
E: /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb: trying to overwrite `/usr/share/doc/libgimp2.0/README', which is also in package libgimp2.0

```

If I try to just remove the package it tells me that the chosen action affects other programs and that it will remove ubuntu-desktop if I remove this package.  I hit cancel since I don't want to remove that but I'm still stuck with a broken software index.

Any ideas?

---

### Post by rsambuca on 2007-10-04
Did you even look in the development section?  This thread should help.

[http://ubuntuforums.org/showthread.php?t=567185](http://ubuntuforums.org/showthread.php?t=567185)

---

### Post by neodorian on 2007-10-04
Missed that one.  Thanks.

---

