---
title: "getlibs not finding packages in repositories?"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by akos.maroy on 2011-03-14
I'm trying to get some libraries through getlibs:

```

$ sudo ./getlibs -p libpng-dev
The following i386 packages will be installed: libpng-dev
Continue [Y/n]? 
libpng-dev was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

```

wonder what 'all repositories' mean in this case? I'm using Ubuntu 10.10 (64 bit, naturally)

I wonder what I'm doing wrong...

---

### Post by Hakunka-Matata on 2011-03-14
System > Administration > Synaptic Package Manager:[LIST]
[INDENT][/INDENT][*]Settings:
[INDENT][/INDENT][*]Repositories
[/LIST]

You must add other repositories as needed too, I don't have a lot of them listed in the Thumbnail.

You need to know which repository provides the package you're trying to download, and then make sure it is in your list of subscribed to repositories.

Thumbnail 3 (synaptic package manager, first view when opening it) allows you to first SEARCH for the package you want, and then if available, install it.

---

### Post by akos.maroy on 2011-03-14
> **Hakunka-Matata said:**
> System > Administration > Synaptic Package Manager:[LIST]
[INDENT][/INDENT][*]Settings:
[INDENT][/INDENT][*]Repositories
[/LIST]

You must add other repositories as needed too, I don't have a lot of them listed in the Thumbnail.

You need to know which repository provides the package you're trying to download, and then make sure it is in your list of subscribed to repositories.

Thumbnail 3 (synaptic package manager, first view when opening it) allows you to first SEARCH for the package you want, and then if available, install it.

I have about the same repositories (except medibuntu perhaps), and I can install libpng-dev fine for 64 bit, but I'm trying to use getlib to install 32 bit packages for me...

I wonder why getlib is not finding the 32 bit libpng-dev package for me :(

---

### Post by Hakunka-Matata on 2011-03-14
eemmhh, me thinks you cannot build 32 applications on a 64 bit system.  Check that out for yourself, but that's how I understand it.

---

### Post by akos.maroy on 2011-03-15
> **Hakunka-Matata said:**
> eemmhh, me thinks you cannot build 32 applications on a 64 bit system.  Check that out for yourself, but that's how I understand it.

well, you understand it wrong then :) you compile 32 bit apps on a 64 bit system by using the -m32 flag :)

the very reason getlibs was created to download & install 32 bit library packages on 64 bit systems

---

### Post by Hakunka-Matata on 2011-03-15
well ok then, i do understand now.  thanks

---

### Post by Hakunka-Matata on 2011-03-15
Caveat, I'm on a Ubuntu10.10 Desktop 32bit OS at the moment.  But I investigated your libpng-dev install deal and decided to try installing it myself to see what happened.

I first installed [getlibs] from [http://explore-ubuntu.blogspot.com/2010/04/getlibs.html]("http://explore-ubuntu.blogspot.com/2010/04/getlibs.html")

after that ```
das@1010-Westport:~$ sudo ./getlibs -p libpng-dev
[sudo] password for das: 
sudo: ./getlibs: command not found
das@1010-Westport:~$ sudo getlibs -p libpng-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libpng12-dev' instead of 'libpng-dev'
The following extra packages will be installed:
  libpng12-dev zlib1g-dev
The following NEW packages will be installed:
  libpng12-dev zlib1g-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 451kB of archives.
After this operation, 1,069kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ maverick/main zlib1g-dev i386 1:1.2.3.4.dfsg-3ubuntu1 [188kB]
Get:2 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ maverick/main libpng12-dev i386 1.2.44-1 [262kB]
Fetched 451kB in 0s (1,243kB/s)     
Selecting previously deselected package zlib1g-dev.
(Reading database ... 207246 files and directories currently installed.)
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3.4.dfsg-3ubuntu1_i386.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.44-1_i386.deb) ...
Processing triggers for man-db ...
Setting up zlib1g-dev (1:1.2.3.4.dfsg-3ubuntu1) ...
Setting up libpng12-dev (1.2.44-1) ...
das@1010-Westport:~$ ^C
das@1010-Westport:~$ 

```

it looks kinda like a 'metapackage', ??? It apparently has worked on this system.

---

