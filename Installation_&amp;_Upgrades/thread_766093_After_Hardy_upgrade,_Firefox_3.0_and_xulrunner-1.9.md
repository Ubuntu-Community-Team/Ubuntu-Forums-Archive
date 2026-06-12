---
title: "After Hardy upgrade, Firefox 3.0 and xulrunner-1.9 cannot be installed"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Johnny K on 2008-04-25
I just upgraded Gutsy Gibbon to Hardy Heron, but Firefox 3 cannot be installed because it is dependent upon the package xulrunner-1.9, which cannot be installed. When I try to install xulrunner-1.9 with apt-get, I get the following error message:

```
dpkg: regarding .../xulrunner-1.9_1.9~b5+nobinonly-0ubuntu3_amd64.deb containing xulrunner-1.9:
 xulrunner-1.9 conflicts with j2re1.4
  j2re1.4 (version 1.4.2.02-1ubuntu3) is present and installed.
dpkg: error processing /var/cache/apt/archives/xulrunner-1.9_1.9~b5+nobinonly-0ubuntu3_amd64.deb (--unpack):
 conflicting packages - not installing xulrunner-1.9
Errors were encountered while processing:
 /var/cache/apt/archives/xulrunner-1.9_1.9~b5+nobinonly-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Which makes it seem as though the package j2re1.4. So I try to install j2re1.4 from apt-get, and get this message:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package j2re1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package j2re1.4 has no installation candidate


```

which contains the line "Package j2re1.4 is not installed, so not removed".

So in summary, I can't install Firefox because I can't install xulrunner-1.9. I can't uninstall xulrunner-1.9 because it conflicts with the package j2re1.4. I can't uninstall j2re1.4 because it doesn't exist.

---

### Post by boekebaas on 2008-04-25
I have exactly the same problem. I'm not sure and I haven't checked my Ubuntu system yet, but maybe this topic [http://ubuntuforums.org/showthread.php?t=746362](http://ubuntuforums.org/showthread.php?t=746362) is connected to our problem?

---

### Post by boekebaas on 2008-04-25
I solved it by removing the j2re1.4 package using this command:

```
sudo dpkg -r j2re1.4
```

and removing all other conflicting packages (firefox-3.0 etc). Then I installed xulrunner-1.9 using the package manager and after that, I installed the conflicting packages again. everything works fine now.

---

### Post by Johnny K on 2008-04-25
> **boekebaas said:**
> I solved it by removing the j2re1.4 package using this command:

```
sudo dpkg -r j2re1.4
```

and removing all other conflicting packages (firefox-3.0 etc). Then I installed xulrunner-1.9 using the package manager and after that, I installed the conflicting packages again. everything works fine now.

That worked perfectly!!! Thank you so much!

---

### Post by Phil Urich on 2008-05-02
Ditto, fixed perfectly here too, thanks!

---

