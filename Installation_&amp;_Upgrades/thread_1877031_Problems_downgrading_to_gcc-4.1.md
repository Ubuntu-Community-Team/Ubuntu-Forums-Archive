---
title: "Problems downgrading to gcc-4.1"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by Indrek_K on 2011-11-07
Greetings, I recently installing Ubuntu with Wubi. I'm currently trying to compile a project called SRILM, and my default gcc compiler 4.6 does not find the old .h files. I read about it, so I know, that I should try installing gcc 4.1, which could support it. However:

When doing "apt-get install gcc-4.1"  I get the following:



Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gcc-4.1 : Depends: binutils (>= 2.17cvs20070426) but it is not going to be installed
           Depends: libgcc1 (>= 1:4.1.2-27ubuntu1) but it is not going to be installed
           Recommends: libc6-dev (>= 2.5) but it is not going to be installed
 libasound2 : PreDepends: multiarch-support
              PreDepends: dpkg (>= 1.15.7.2)
 libc6 : Depends: libgcc1 but it is not going to be installed
         Depends: tzdata but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.



That is after adding "deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) lucid main univers" to /etc/apt/sources.list.
However without it I get:



Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gcc-4.1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gcc-4.1' has no installation candidate



That is both with newest version of gcc installed, and not installed(apt-get remove gcc).

I tryed looking for similar problems, but failed, I'm hoping you could help me? 

Also, if anyone knows of a script being written that would recursivly go to all folders and files and change all old includes for new ones, that would work fine aswell.

---

