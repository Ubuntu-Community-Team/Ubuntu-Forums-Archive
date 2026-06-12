---
title: "[SOLVED] APT-GET &amp;amp; adept trouble"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by trumpeteersman on 2006-11-14
I cannot upgrade, install, or remove any package at all, it gives me the same error in adept and apt-get:

```

Fetched 3180kB in 9s (319kB/s)
(Reading database ... dpkg: error processing /var/cache/apt/archives/libavahi-common-dev_0.6.10-0ubuntu3.2_i386.deb (--unpack):
 unable to open files list file for package `java-common': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/libavahi-common-dev_0.6.10-0ubuntu3.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I searched around and found that people have problems with other packages and not "java-common".  Their fixes were to put the correct contents into the specified .list file in /var/lib/dpkg/info, which was either blank or corrupted.
 
My /var/lib/dpkg/info/java-common.list is blank and I believe that this is the issue.  Can anyone post what is supposed t go in that file or how I can update the list through apt-get or something?  Other ideas are welcome.

---

### Post by trumpeteersman on 2006-11-20
Bump!  I still cannot install anything at all, and now my nvidia driver is messed up and I can't trouble shoot that untill I can uninstall stuff. Anyone?

---

### Post by trumpeteersman on 2006-11-29
Please help me. I have many flac files that I cannot play because I cannot install the custom patch for the xinelib.  Someone please tell me why I am being ignored.

---

### Post by trumpeteersman on 2007-01-15
Anyone? I am still having this problem:
```

dpkg: serious warning: files list file for package 'java-common' missing, assuming package has no files currently installed.
-------------
-------------
unable to open files list file for package 'jfsutils': No such device or address

```

At least someone say that they don't know so I know that this post is being read!
](*,) ](*,) ](*,)

---

### Post by trumpeteersman on 2007-05-18
This problem was [SOLVED]:
Post:
[http://ubuntuforums.org/showthread.php?t=446107]("http://ubuntuforums.org/showthread.php?t=446107")

---

