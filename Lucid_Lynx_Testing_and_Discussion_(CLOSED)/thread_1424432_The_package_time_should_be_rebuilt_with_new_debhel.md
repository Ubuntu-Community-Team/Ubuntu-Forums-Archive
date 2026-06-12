---
title: "The package time should be rebuilt with new debhelper to get trigger support"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Didius Falco on 2010-03-07
The *time* package was updated earlier today. During the install part of the update, I received the following message:

```
Setting up time (1.7-23build1) ...
Ignoring install-info called from maintainer script
The package time should be rebuilt with new debhelper to get trigger support
```

I made sure I had the latest version of *debhelper*, and installed* tex2html* and *texinfo* after getting a message that these two dependencies were missing. 

I read the man page for *debhelper*, and did some searching around the forum and the web, and tried rebuilding it several different ways, but they all lead back to that initial error.

Any suggestions as to what I'm doing wrong, and how to do it properly would be appreciated...

---

### Post by Didius Falco on 2010-03-11
Since there have been several rounds of updates since I originally posted this, I tried reinstalling the time package.

Alack and alas, I'm still getting the same error/warning/notification as before. Any help would be appreciated...

---

### Post by VMC on 2010-03-11
I don't know. I remember seeing the time update, but mine works fine. I don't have debhelper installed either.

```
$ aptitude show debhelper
Package: debhelper
State: **not installed**
```

```
$ dpkg -L time
/.
/usr
/usr/share
/usr/share/info
/usr/share/info/time.info.gz
/usr/share/doc
/usr/share/doc/time
/usr/share/doc/time/time.html
/usr/share/doc/time/copyright
/usr/share/doc/time/README
/usr/share/doc/time/AUTHORS
/usr/share/doc/time/NEWS.gz
/usr/share/doc/time/changelog.Debian.gz
/usr/share/doc-base
/usr/share/doc-base/time
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/time.1.gz
/usr/bin
/usr/bin/time

$ dpkg -s time
Package: time
Status: install ok installed
Priority: standard
Section: utils
Installed-Size: 148
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: **1.7-23build1**
Depends: libc6 (>= 2.3.4)

```

---

### Post by Space_Balls on 2010-03-11
> **Didius Falco said:**
> Since there have been several rounds of updates since I originally posted this, I tried reinstalling the time package.

Alack and alas, I'm still getting the same error/warning/notification as before. Any help would be appreciated...

Did you actually rebuild the apt-source package and integrate trigger support? At least that's what I get from this warning. Odly no bug has been reported yet.

---

### Post by Didius Falco on 2010-03-11
> **Space_Balls said:**
> Did you actually rebuild the apt-source package and integrate trigger support? At least that's what I get from this warning. Odly no bug has been reported yet.

I tried - I may be doing something wrong/not doing something I need to. I've been searching for answers, but I haven't had that "Eureka" moment yet. What little documentation I've found for debhelper is aimed at programmers, which I am not. I've learned a bit about triggers, but haven't had any luck finding triggers relating to the time package.

I'll keep looking, and if I find the answer to this I'll post it.

I considered posting a bug, and may yet, but there aren't tons of people in this thread saying they have the same problem. I don't have any cron jobs assigned at the moment, and the devs  are busy enough as it is. If I haven't found a resolution by the time the 10.04 release is finalized, I'll post a bug.

---

### Post by Didius Falco on 2010-03-11
I'm (finally) getting somewhere. This is a bug that dates back to the Drake era. What it is referring to seems to be updating manpages. I figured this out by purging and installing the time package. The installation gave the following output:

```
$ sudo apt-get install time
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  time
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/29.7kB of archives.
After this operation, 152kB of additional disk space will be used.
Selecting previously deselected package time.
(Reading database ... 285392 files and directories currently installed.)
Unpacking time (from .../time_1.7-23build1_i386.deb) ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up time (1.7-23build1) ...
Ignoring install-info called from maintainer script
The package time should be rebuilt with new debhelper to get trigger support
```

I then started searching for man-db bugs and found this: [https://bugs.launchpad.net/ubuntu/+source/man-db/+bug/50110](https://bugs.launchpad.net/ubuntu/+source/man-db/+bug/50110)

I'm now considering this closed, for my purposes. I still hope they eventually resolve the tension between packages that need the triggers and those that don't, but it's definitely a very low priority item - the only "bug" is the message that is passed that makes people like me think something is broken when it really isn't.

Thanks to those who responded - it was your posts that led me towards the answer.

---

