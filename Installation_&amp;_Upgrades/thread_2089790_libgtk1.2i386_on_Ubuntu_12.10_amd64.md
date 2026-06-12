---
title: "libgtk1.2:i386 on Ubuntu 12.10 amd64"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by gabrielitos on 2012-11-30
Hi!

I have a fresh new installation of Ubuntu 12.10 amd64 and I need the libgtk1.2:i386 to have a legacy program working. As suggested in other threads, I added the Hardy repositories and apt-get update.

But, when I try to install the package, it gives me the error:

 libgtk1.2:i386 : Depends on: libgtk1.2-common:i386 (>= 1.2.10-18.1build2) which is a virtual package.

The libgtk1.2 (amd64 version) installs normally. The same error occurs when I try to install the libgtk1.2 deb files manually.

Any suggestion?

---

### Post by gabrielitos on 2012-11-30
Nobody? I looked everywhere for a solution but I am still stuck.

I think it's something related to the libgtk1.2-common librart: it is provided with the ALL architecture and it installs fine, but probably is not seen by the package manager when solving the dependency...

---

### Post by gabrielitos on 2012-12-02
Nobody expert in legacy libraries?

---

### Post by gabrielitos on 2012-12-23
I still have this problem. I think it's something related to multiarch, when it tries to install the libgtk1.2-common which is shared between i386 and amd64. But I have no idea how to solve it! Please help!

---

### Post by _6i on 2012-12-28
Hi,
  I have basically the same problem.
  According to my research, the problem seems to be with the libgtk1.2-common package.
  I suspect, that the package has been generated either using by "Architecture: all" instead of "Architecture: any" in the <pkg-src-dir>/debian/control file, or missing the "Multi-Arch: foreign" line entirely...or both..
  I made my deduction according to this page: [http://wiki.debian.org/Multiarch/CrossDependencies](http://wiki.debian.org/Multiarch/CrossDependencies)
  I could use a second opinion, as I'm a little underslept right now, and I could have misunderstood something easily.. :)

Also, I could not test my hypothesis, as I has been unable to recompile gtk+1.2 (source pkg from [https://launchpad.net/~adamkoczur/+archive/gtk1.2](https://launchpad.net/~adamkoczur/+archive/gtk1.2) for ubuntu maverick) neither on my i386 lubuntu 12.10 (debuild dies on dh_makeshlibs getting an "-l..." parameter, which I have not found in any of the manpages yet, and I've looked into manpages for various ubuntu versions) nor my amd64 ubuntu 12.04 (same "cannot install" problem with build dependencies like gettext etc. &#8212; I didn't want to recompile everything just yet..)


As a temporary solution, if you download the libgtk1.2 package and its immediate dependecies (which you don't have installed already), then install them using "sudo dpkg -i *.deb", then the software will work as you'll have installed all the right packages, but apt will complain that libgtk1.2:i386 misses the libgtk1.2-common:i386 package (apt does not realize that that package is platform independent..). Dpkg said, that it could not configure the libgtk1.2 package after installation because of that (still) missing dependency problem, however, my old app ran (seemingly) without a problem.

Also, if you know how to tell/force-to-recognize apt that the installed libgtk1.2-common package works as libgtk1.2-common:i386 , please tell me, as I could not figure it out just yet.

---

### Post by _6i on 2012-12-30
Ok, I got a little time on my hands again, and I managed to figure out how to manually tell apt (for being able to install) and dpkg (for successful configuration) that the "libgtk1.2-common" package fulfills the dependency for the package "libgtk1.2:i386" (as being architecture independent).
Well, at least it worked on Ubuntu 12.04 amd64.
It can easily happen that this is not the "proper" way to do things, or that I made some unnecessary steps, too, but this is how i got it to work.

Steps (all done in a user terminal, as a user with administrator privileges):
[LIST=1]
[*] Add the [https://launchpad.net/~adamkoczur/+archive/gtk1.2](https://launchpad.net/~adamkoczur/+archive/gtk1.2) ppa for maverick (if you have not done it already):
[LIST=a]
[*] Add the package source list:
```
sudo sh -c 'echo "deb http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu maverick main" >> /etc/apt/sources.list.d/adamkoczur-gtk1.2-maverick.list'
```
[*] Add the signing key for the ppa (found on the ppa page linked above):
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 19E58C11
```
[/LIST]
[*] Update the apt package database:
```
sudo apt-get update
```
[*] Tell apt that "libgtk1.2-common" is good for i386, too, by adding the line "Multi-Arch: foreign" to the package information of "libgtk1.2-common" for both amd64 and i386 package lists:
(You can probably apply the following 2 sets of lines as patches with "sudo patch -p0 <patchfile" where patchfile contains one set of lines.)
[LIST=a]
[*] For amd64:
```

--- /var/lib/apt/lists/ppa.launchpad.net_adamkoczur_gtk1.2_ubuntu_dists_maverick_main_binary-amd64_Packages	2012-12-31 02:27:00.254793899 +0000
+++ /var/lib/apt/lists/ppa.launchpad.net_adamkoczur_gtk1.2_ubuntu_dists_maverick_main_binary-amd64_Packages.patched	2012-12-31 02:28:38.643848434 +0000
@@ -712,6 +712,7 @@
 Size: 210556
 MD5sum: be36907315704f7289b10fbb9c484371
 SHA1: d67f52ac44d7b5f6884fa7cc3f129e4259e8f701
+Multi-Arch: foreign
 Description: Common files for the GTK+ library
  The GIMP Toolkit is a freely available set of widgets for X.
  GTK is easy to use, and has been implemented in such projects as

```
[*] For i386:
```

--- /var/lib/apt/lists/ppa.launchpad.net_adamkoczur_gtk1.2_ubuntu_dists_maverick_main_binary-i386_Packages	2012-12-31 02:43:34.710334782 +0000
+++ /var/lib/apt/lists/ppa.launchpad.net_adamkoczur_gtk1.2_ubuntu_dists_maverick_main_binary-i386_Packages.patched	2012-12-31 02:44:17.939150985 +0000
@@ -690,6 +690,7 @@
 Size: 210556
 MD5sum: be36907315704f7289b10fbb9c484371
 SHA1: d67f52ac44d7b5f6884fa7cc3f129e4259e8f701
+Multi-Arch: foreign
 Description: Common files for the GTK+ library
  The GIMP Toolkit is a freely available set of widgets for X.
  GTK is easy to use, and has been implemented in such projects as

```
[/LIST]
[*] Install the package "libgtk1.2-common":
```
sudo apt-get install libgtk1.2-common
```
[*] Tell dpkg that "libgtk1.2-common" is good for i386, too, by adding the line "Multi-Arch: foreign" to the package information of "libgtk1.2-common" for both the list- and status-file of available packages:
(You can probably NOT apply the following 2 sets of lines as patches...at least not without some error/warning messages about incorrect line numbers...because iirc the following 2 files are not sorted, and their contents can differ from system to system.)
[LIST=a]
[*] For the list-file:
```

--- /var/lib/dpkg/available	2012-12-31 02:59:30.759873458 +0000
+++ /var/lib/dpkg/available.patched	2012-12-31 03:00:02.648133555 +0000
@@ -1603,6 +1603,7 @@
 Version: 1.2.10-18.1build2ak2maverick2
 Replaces: libgtk1.2 (<< 1.2.10-4)
 Size: 210556
+Multi-Arch: foreign
 Description: Common files for the GTK+ library
  The GIMP Toolkit is a freely available set of widgets for X.
  GTK is easy to use, and has been implemented in such projects as

```
[*] For the status-file:
```

--- /var/lib/dpkg/status	2012-12-31 03:08:58.336431014 +0000
+++ /var/lib/dpkg/status.patched	2012-12-31 03:09:21.954201162 +0000
@@ -1564,6 +1564,7 @@
 
 Package: libgtk1.2-common
 Status: install ok installed
+Multi-Arch: foreign
 Priority: optional
 Section: misc
 Installed-Size: 944

```

IMPORTANT NOTE:
If you try to change the list- and status-file before installing the "libgtk1.2-common" package, the change will be lost, as the package information gets updated upon installation. Therefore installing "libgtk1.2-common" automatically (as a dependency for  "libgtk1.2:i386") will result in an error at the package configuration stage.

[/LIST]

[*] Finally, install "libgtk1.2:i386":
```
sudo apt-get install libgtk1.2:i386
```
[*] (Optional) Mark "libgtk1.2-common" as automatically installed:
```
sudo apt-mark auto libgtk1.2-common
```
[/LIST]

This way, each step should complete without an error.
Hopefully, it will work for you, too.
Happy New Year! ;)

---

### Post by gabrielitos on 2013-01-07
Wow thanks! I can't test immediately your solution, but it sounds very good and it was exactly what I was looking for! I will let you know about the result but for now thanks a lot!

---

### Post by _6i on 2013-01-08
You're welcome. I hope it works out for you, too.

---

