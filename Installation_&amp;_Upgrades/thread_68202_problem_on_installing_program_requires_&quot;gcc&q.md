---
title: "problem on installing program requires &quot;gcc&quot;"
date: 2005-09-22
forum: Installation &amp; Upgrades
---

### Post by engkeboy on 2005-09-22
im installing perl but it's aborting itself because of this reason..
----------------------------------------------------------
Use which C compiler? [cc]
./trygcc: line 10: cc: command not found
Uh-oh, the C compiler 'cc' doesn't seem to be working.
./checkcc: line 10: cc: command not found
Uh-oh, the C compiler 'cc' doesn't seem to be working.
You need to find a working C compiler.
Either (purchase and) install the C compiler supplied by your OS vendor,
or for a free C compiler try [http://gcc.gnu.org/](http://gcc.gnu.org/)
I cannot continue any further, aborting.
-------------------------------------------------------------------------

so i shift into gcc and i i've read in the other threads to try **sudo apt-get install build-essential** but it doesn't seem to work because of this reason.. 

----- /home/engkeboy # sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: gcc (>= 3:3.3) but it is not going to be installed
                   Depends: g++ (>= 3:3.3) but it is not going to be installed
  dpkg-dev: Depends: dpkg (>= 1.13.1) but 1.10.27ubuntu2 is to be installed
  perl: Depends: perl-base (= 5.8.7-5) but 5.8.4-6ubuntu1 is to be installed
        Depends: perl-modules (>= 5.8.7-5) but 5.8.4-6ubuntu1 is to be installed
        Depends: libc6 (>= 2.3.5-1) but 2.3.2.ds1-20ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
-----------------------
so i try [B]sudo apt-get -f install[\B] and says..

-------------:/home/engkeboy # sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  dpkg-dev: Depends: dpkg (>= 1.13.1) but 1.10.27ubuntu2 is installed
  perl: Depends: perl-base (= 5.8.7-5) but 5.8.4-6ubuntu1 is installed
        Depends: perl-modules (>= 5.8.7-5) but 5.8.4-6ubuntu1 is installed
        Depends: libc6 (>= 2.3.5-1) but 2.3.2.ds1-20ubuntu14 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
---------


i'm trying to install XMMS and PERL but it requires the gcc.. 

what is the problem with this? im using Ubuntu Hoary Hedgehog 5.04

hope someone could help... :(

---

### Post by mlomker on 2005-09-22
> hope someone could help... :(

My guess is that you have backports or some 3rd-party repositories in your /etc/apt/sources.list.  Remove them, update, and try again.  Post your sources.list if necessary and we'll take a look.

---

### Post by bsussman on 2005-09-22
This looks like you are building perl - why are you not using Synaptic/Kynaptic/apt-get to install it?

Seems like this from the desc of perl-base covers the territory:

 > To make
full use of Perl, you'll want to install the `perl', `perl-modules' and
optionally `perl-doc' packages which supplement this one.

---

