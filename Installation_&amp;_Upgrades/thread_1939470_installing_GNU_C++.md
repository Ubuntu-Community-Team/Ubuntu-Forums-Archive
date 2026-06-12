---
title: "installing GNU C++"
date: 2012-03-11
forum: Installation &amp; Upgrades
---

### Post by mzimmers on 2012-03-11
Hi -

Is this still the preferred/recommended method for getting C++ on my ubuntu system?

[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

Thanks...

---

### Post by wojox on 2012-03-11
Yes, build-essential will install c/c++.

---

### Post by mzimmers on 2012-03-11
Thank you, wojox. I guess what I was trying to ask is, is this the "best" way to do this? I know that some apps can be installed through the software center, so I was wondering whether the command line was the way to go.

---

### Post by wojox on 2012-03-11
It's a little quicker to use the terminal. The USC and Synaptic are just the GUI frontend's for apt-get. :P

---

### Post by mzimmers on 2012-03-11
OK, good enough. Just to pursue this a little further for my education, if I were to use the USC, how would I do it? My search for C++ didn't reveal the GNU compiler.

EDIT: interesting...I just followed the instructions in the link above for retrieving gcc using svn from gnu.org's repository, and it downloaded all the source, and automatically built it for me. I didn't think it would do that.

Unfortunately, I think it may have also downloaded a bunch of stuff I don't need (as the downloaded files went whizzing by, I saw stuff for Ada and other languages). Is there a way to partly uninstall anything I don't want?

---

### Post by wojox on 2012-03-12
> **mzimmers said:**
> OK, good enough. Just to pursue this a little further for my education, if I were to use the USC, how would I do it? My search for C++ didn't reveal the GNU compiler.
It package alone should be gcc.

> EDIT: interesting...I just followed the instructions in the link above for retrieving gcc using svn from gnu.org's repository, and it downloaded all the source, and automatically built it for me. I didn't think it would do that.
If you followed the link you posted above, you downloaded from Ubuntu's repo's.

> Unfortunately, I think it may have also downloaded a bunch of stuff I don't need (as the downloaded files went whizzing by, I saw stuff for Ada and other languages). Is there a way to partly uninstall anything I don't want?
Sure, just watch what it wants to take with it.

```
wojox@wojox-desktop:~$ apt-cache show build-essential
Package: build-essential
Priority: optional
Section: devel
Installed-Size: 37
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Architecture: amd64
Version: 11.5ubuntu2
Depends: libc6-dev | libc-dev, gcc (>= 4:4.4.3), g++ (>= 4:4.4.3), make, dpkg-dev (>= 1.13.5)
Filename: pool/main/b/build-essential/build-essential_11.5ubuntu2_amd64.deb
Size: 5978
MD5sum: a0b56317a176d3305a94dda33808b276
SHA1: afe756d40911577e8bed2aab4649de7262900bf9
SHA256: 5af06c8e08f84e4d3a73642e1901016844f505c2a8a4cf825ca7ecdf16a89fbf
Description-en: Informational list of build-essential packages
 If you do not plan to build Debian packages, you don't need this
 package.  Starting with dpkg (>= 1.14.18) this package is required
 for building Debian packages.
 .
 This package contains an informational list of packages which are
 considered essential for building Debian packages.  This package also
 depends on the packages on that list, to make it easy to have the
 build-essential packages installed.
 .
 If you have this package installed, you only need to install whatever
 a package specifies as its build-time dependencies to build the
 package.  Conversely, if you are determining what your package needs
 to build-depend on, you can always leave out the packages this
 package depends on.
 .
 This package is NOT the definition of what packages are
 build-essential; the real definition is in the Debian Policy Manual.
 This package contains merely an informational list, which is all
 most people need.   However, if this package and the manual disagree,
 the manual is correct.
Multi-Arch: foreign
Description-md5: 90ef0ef86cafda0bd16f746eb621d9da
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Build-Essential: yes
Origin: Ubuntu
Supported: 5y

```

---

### Post by mzimmers on 2012-03-12
OK, well, since it looks like I need the education, I think I'd like to do this one over. How would I go about completely uninstalling what I've installed so far?

---

### Post by wojox on 2012-03-12
```
sudo apt-get remove build-essential checkinstall cvs subversion git-core mercurial
```
Should do it.

---

### Post by mzimmers on 2012-03-13
Thank you. That apt-get is a nice little program. I decided to uninstall build-essential and checkinstall, and it told me I was going to save only 635 KB. So, I guess I didn't pick up as much unwanted stuff as I'd feared, and decided to leave it at that.

---

