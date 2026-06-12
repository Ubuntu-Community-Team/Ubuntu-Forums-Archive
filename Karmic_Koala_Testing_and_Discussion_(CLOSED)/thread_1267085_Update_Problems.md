---
title: "Update Problems"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chrism66 on 2009-09-15
Since last nights updates  I am getting the following message:

```
Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/status' near line 35 package 'libgtkspell0':
 `Depends' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/status' near line 35 package 'libgtkspell0':
 `Depends' field, invalid package name `
Reading package lists... Done             

```

---

### Post by chrism66 on 2009-09-16
Any clue can not update until I get this working??? Here is the area of "status" file that the error is in

```
Package: libgtkspell0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 556
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: gtkspell
Version: 2.0.15-0ubuntu1
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.2.5), libcairo2 (>= 1.2.4), libenchant1c2a (>= 1.4.2), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgìib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.17.4), libpango1.0-0 (>= 1.14.0)
Description: a spell-checking addon for GTK's TextView widget
 GtkSpell provides MSWord/MacOSX-style highlighting of misspelled words in a
 GtkTextView widget.  Right-clicking a misspelled word pops up a menu of
 suggested replacements.
```

---

### Post by paul_in_london on 2009-09-16
Try doing:

```
sudo cp /var/lib/dpkg/status.old /var/lib/dpkg/status
sudo aptitude update
sudo aptitude full-upgrade
```

---

### Post by chrism66 on 2009-09-16
Followed paul_in_london's advice and now I get the following:

```
dpkg: parse error, in file '/var/lib/dpkg/available' near line 45 package 'libgtkspell0':
 `Depends' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/available' near line 45 package 'libgtkspell0':
 `Depends' field, invalid package name `

```

Believe it has to do with "libgìib2.0-0" is it supposed to be "libglib2.0-0", and if so how would you got editing the status file to correct the multiple listings of "libgìib2.0-0" tried with Gedit but it could not do it.

---

### Post by chrism66 on 2009-09-16
All right I have also tried the six older status's files that were in /var/backups. all of them are giving me the same error which seems to deal with the libgtkspell0. Is there any way to get my this error?

---

