---
title: "Lucid Beta 2 (10.04) missing KDevelop"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by damien_d on 2010-04-11
On Ubuntu (not kubuntu) seems to be missing KDevelop:

```

damien@damien-backup:~$ sudo apt-get update
Hit http://au.archive.ubuntu.com lucid Release.gpg
Hit http://au.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_AU
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_AU
Hit http://au.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_AU
Hit http://security.ubuntu.com lucid-security Release
Ign http://au.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_AU
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://au.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com lucid-updates Release.gpg
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_AU
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com lucid Release
Hit http://au.archive.ubuntu.com lucid-updates Release
Hit http://au.archive.ubuntu.com lucid/main Packages
Hit http://au.archive.ubuntu.com lucid/restricted Packages
Hit http://au.archive.ubuntu.com lucid/main Sources
Hit http://au.archive.ubuntu.com lucid/restricted Sources
Hit http://au.archive.ubuntu.com lucid/universe Packages
Hit http://au.archive.ubuntu.com lucid/universe Sources
Hit http://au.archive.ubuntu.com lucid/multiverse Packages
Hit http://au.archive.ubuntu.com lucid/multiverse Sources
Hit http://au.archive.ubuntu.com lucid-updates/main Packages
Hit http://au.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://au.archive.ubuntu.com lucid-updates/main Sources
Hit http://au.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://au.archive.ubuntu.com lucid-updates/universe Packages
Hit http://au.archive.ubuntu.com lucid-updates/universe Sources
Hit http://au.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://au.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
damien@damien-backup:~$ sudo apt-get install kdevelop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kdevelop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdevplatform1-libs
E: Package kdevelop has no installation candidate
damien@damien-backup:~$ sudo apt-get install kdevplatform1-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libapr1 libaprutil1 libsublime1 libsvn1
The following NEW packages will be installed:
  kdevplatform1-libs libapr1 libaprutil1 libsublime1 libsvn1
0 upgraded, 5 newly installed, 0 to remove and 177 not upgraded.
Need to get 3,025kB of archives.
After this operation, 11.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com/ubuntu/ lucid/main libapr1 1.3.8-1build1 [123kB]
Get:2 http://au.archive.ubuntu.com/ubuntu/ lucid/main libaprutil1 1.3.9+dfsg-3build1 [90.8kB]
Get:3 http://au.archive.ubuntu.com/ubuntu/ lucid/universe libsublime1 0.9.98-0ubuntu1 [99.5kB]
Get:4 http://au.archive.ubuntu.com/ubuntu/ lucid/main libsvn1 1.6.6dfsg-2ubuntu1 [906kB]
Get:5 http://au.archive.ubuntu.com/ubuntu/ lucid/universe kdevplatform1-libs 0.9.98-0ubuntu1 [1,806kB]
Fetched 3,025kB in 4s (606kB/s)               
Selecting previously deselected package libapr1.
(Reading database ... 136426 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.3.8-1build1_amd64.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.3.9+dfsg-3build1_amd64.deb) ...
Selecting previously deselected package libsublime1.
Unpacking libsublime1 (from .../libsublime1_0.9.98-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.6.6dfsg-2ubuntu1_amd64.deb) ...
Selecting previously deselected package kdevplatform1-libs.
Unpacking kdevplatform1-libs (from .../kdevplatform1-libs_0.9.98-0ubuntu1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Setting up libapr1 (1.3.8-1build1) ...

Setting up libaprutil1 (1.3.9+dfsg-3build1) ...

Setting up libsublime1 (0.9.98-0ubuntu1) ...

Setting up libsvn1 (1.6.6dfsg-2ubuntu1) ...

Setting up kdevplatform1-libs (0.9.98-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
damien@damien-backup:~$ sudo apt-get install kdevelop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kdevelop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdevplatform1-libs
E: Package kdevelop has no installation candidate
damien@damien-backup:~$ 

```

It's not available searching Ubuntu Software Centre either :(

Any ideas?  I'm looking to see if the new version fixes the bugs that were in 9.10...

  -- Damien

---

### Post by damien_d on 2010-04-11
OK, this changelog isn't promising:

[https://launchpad.net/ubuntu/+source/kdevelop/+changelog](https://launchpad.net/ubuntu/+source/kdevelop/+changelog)

:(

---

### Post by luisella on 2010-04-13
It seems the kdevelop-data and kdevelop packages have been postponed as they will not be stable by the lucid release (29 April).

But although kdevelop 4 is not yet supported, it's still possible to install it in the current lucid beta 2. Here is what is needed:
- manually download the kdevelop-data ( [https://launchpad.net/ubuntu/lucid/armel/kdevelop-data/4:3.9.98-0ubuntu1](https://launchpad.net/ubuntu/lucid/armel/kdevelop-data/4:3.9.98-0ubuntu1) ) and kdevelop ( [https://launchpad.net/ubuntu/lucid/armel/kdevelop/4:3.9.98-0ubuntu1](https://launchpad.net/ubuntu/lucid/armel/kdevelop/4:3.9.98-0ubuntu1) ) discontinued packages.
- Install with Synaptic Package Mager around one hundred packages from which they depend (these are still supported in ubuntu lucid)
- manually install kdevelop-data and kdevelop.

---

### Post by damien_d on 2010-04-13
Thanks for that. The links for amd64 are:
  * [https://launchpad.net/ubuntu/lucid/amd64/kdevelop-data/4:3.9.98-0ubuntu1](https://launchpad.net/ubuntu/lucid/amd64/kdevelop-data/4:3.9.98-0ubuntu1) 
  * [https://launchpad.net/ubuntu/lucid/amd64/kdevelop/4:3.9.98-0ubuntu1](https://launchpad.net/ubuntu/lucid/amd64/kdevelop/4:3.9.98-0ubuntu1)

About to see if it solves some of the issues I had with the version in 9.10 ...

---

### Post by overdrank on 2010-04-13
Moved to  Lucid Lynx Testing and Discussion :)

---

### Post by markh on 2010-04-15
Gah, I don't want to rant, but this is what drives me mad about Ubuntu. I've been testing Lucid for deployment for the past few months, our students use Kdevelop extensively from Hardy, and now it's just 'oh yeah, it's not in the repos any more'. I thought this was supposed to be post feature freeze. Yeah, I know I can probably work around it, but I don't see why they can't just ship an older version or something? 

Every time I test a new Lucid drop they've either moved some buttons, or packages, or renamed things in the preseed file for no apparent reason. 

Ok, I've calmed now :P

---

### Post by damien_d on 2010-04-15
> **markh said:**
> 
Every time I test a new Lucid drop they've either moved some buttons, or packages, or renamed things in the preseed file for no apparent reason. 

Ok, I've calmed now :P

On the bright side, it now indexes the Kernel and U-Boot :)

It crashed miserably before.

  -- Damien

---

### Post by christian.convey on 2010-04-22
This is incredibly frustrating.  Canonical has two other options available to them: delay the release, or use an older version of KDevelop.

It seems like either (a) they're being overly fixated on the originally planned release date (as discussed elsewhere regarding the xserver memory leak), or they're waiting far too long in the development process to find good work-arounds to issues like what KDevelop faces.

And the urgency of the issue is listed a "low"???  For the omission of KDE's main C++ IDE???

I've generally been happy with Ubuntu, but the choices they're making regarding releases lately are really turning me off.

---

### Post by cariboo on 2010-04-22
I would suggest you wait until the first point release to see if the packages that are being held back, because of dependencies are installable.

---

