---
title: "I can't update packages: &quot;Package operation failed&quot;"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by r109chaos on 2011-05-02
In ubuntu 11.04, I can't update packages. I get the following error:

Package operation failed
The installation or removal of a software package failed.

Details:
```

installArchives() failed: (Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%dpkg: unrecoverable fatal error, aborting:
 files list file for package `tzdata' contains empty filename
```

**Note:** I've tried deselecting certain packages, deselecting all but one package, and several others; with no luck. Any idea how I can resolve this? :(

---

### Post by dino99 on 2011-05-02
open synaptic to remove/purge then reinstall tzdata

---

### Post by r109chaos on 2011-05-04
When I reinstall tzdata I get the following error:

```
Preconfiguring packages ...
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `tzdata' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

```

---

### Post by r109chaos on 2011-05-06
I found this thread here: [http://ubuntuforums.org/archive/index.php/t-1232143.html](http://ubuntuforums.org/archive/index.php/t-1232143.html)

gartss suggests to: cd /var/lib/dpkg
backup status: cp status status.bak
edit: sudo nano status

What I did was Ctrl + W and searched "Package: tzdata" and deleted the lines for tzdata (as oppose to tzdata-java).

After that I did: apt-get install -f
Then ran Update Manager and it resolved the issue.

I guess i could attempt to reinstall tzdata.

These are the lines I deleted, not sure what's wrong with it.

```
Package: tzdata
Status: install ok installed
Multi-Arch: foreign
Priority: required
Section: libs
Installed-Size: 6280
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 2011g-0ubuntu0.11.04
Replaces: libc0.1, libc0.3, libc6, libc6.1
Provides: tzdata-wheezy
Depends: debconf (>= 0.5) | debconf-2.0
Description: time zone and daylight-saving time data
 This package contains data required for the implementation of
 standard local time for many representative locations around the
 globe. It is updated periodically to reflect changes made by
 political bodies to time zone boundaries, UTC offsets, and
 daylight-saving rules.
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>

```

---

### Post by Juvencio on 2011-06-03
First of all find out what’s causing the error.

Go to Ubuntu software center.

Find an app to install or uninstall.

The error should say 
"Package operation failed" 

Click on details scroll down to find the following quote 
"Errors were encountered while processing:"

Mine was Samba4 

Find your app in Ubuntu software center and uninstall.
This should solve your problem.
[U]
apps not compatible with 11.04[/U]

- ESET NOD32 antivirus 
- Samba4 

Hope this helps others

add your app for others to see

---

