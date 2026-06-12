---
title: "Pulseaudio Won't Install"
date: 2008-11-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GuitarRocker2562 on 2008-11-08
Hi, I am running juanty, i386, and I was wondering, does anybody else not have pulseaudio installed, when I try to install it, I get an error about broken packages. Anybody else?

---

### Post by plun on 2008-11-08
Yup and its "stone dead broken" at least for 32 bit...

I tested GIT and it works great. ver .14

[http://ubuntuforums.org/showpost.php?p=6124305&postcount=15](http://ubuntuforums.org/showpost.php?p=6124305&postcount=15)

Or remove PA but thats a "primitive solution"...:D


I hope that Luke goes directly to the GIT version. Fedora 10 uses that code.

---

### Post by GuitarRocker2562 on 2008-11-08
when do you think it will be fixed?

---

### Post by autocrosser on 2008-11-08
Yes--same here--just waiting for the updates--thinking about going the git way, I'm not in a world of hurt (Alsa stuff is still working here)--so I'm not in a real rush.....

Have not seen any indication yet--the problem is with libasound-plugins

---

### Post by plun on 2008-11-08
I downloaded source for ver .13 and it was impossible to build.
GIT version was Ok with the patch.

alsa-plugins was updated again today and the challenge is that these packages are really nested within each other and also the meta package ubuntu-desktop

GIT builds Ok but maybe there is a "Debian challenge"....  "dirty packages" directly built from source...O:)  maybe impossible....

Luke must for sure be aware of that the builds broke...

---

### Post by plun on 2008-11-08
Followup... I have a package build and I can upload it if someone wants to test.

I take no responsibility for this package....except its done with a standard Debian checkinstall

module-raop-discover.a must be done with a "dummy" file



> ======================== Installation successful ==========================

Copying documentation directory...
./
./ChangeLog
./LICENSE
./README
./GPL
./ABOUT-NLS
grep: /var/tmp/tmp.gKDOkCmqGD/newfile: No such file or directory

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...
OK

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/plun/pulseaudio/pulseaudio_0.9.14-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r pulseaudio



---

