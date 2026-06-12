---
title: "Problem installing, hangs after allocating partition."
date: 2006-02-27
forum: Installation &amp; Upgrades
---

### Post by synergynova on 2006-02-27
As the title decribes:
After allocating the partition, it goes onto the blue screen and then hangs.

Is there a way of debugging this?

---

### Post by synergynova on 2006-02-27
I've been able to get this from the log file:  I'm not sure if this is the same problem or another :?
```
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
  No matching physical volumes found
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
  No volume groups found
  Reading all physical volumes.  This may take a while...
Selecting previously deselected package base-files.
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_3.1.5ubuntu4_i386.deb) ...
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.10_i386.deb) ...
dpkg: base-passwd: dependency problems, but configuring anyway as you request:
 base-passwd depends on libc6 (>= 2.3.4-1); however:
  Package libc6 is not installed.
Setting up base-passwd (3.5.10) ...

dpkg: base-files: dependency problems, but configuring anyway as you request:
 base-files depends on awk; however:
  Package awk is not installed.
Setting up base-files (3.1.5ubuntu4) ...

dpkg: regarding .../dpkg_1.13.10ubuntu4_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on libc6 (>= 2.3.4-1)
dpkg: warning - ignoring pre-dependency problem !
(Reading database ... 84 files and directories currently installed.)
Preparing to replace dpkg 1.13.10ubuntu4 (using .../dpkg_1.13.10ubuntu4_i386.deb) ...
Unpacking replacement dpkg ...
dpkg: dpkg: dependency problems, but configuring anyway as you request:
 dpkg depends on libc6 (>= 2.3.4-1); however:
  Package libc6 is not installed.
 dpkg depends on coreutils | textutils (>= 2.0-3); however:
  Package coreutils is not installed.
  Package textutils is not installed.
Setting up dpkg (1.13.10ubuntu4) ...
Moving /usr/info/dir to /usr/share/info/dir ...
Adding `local diversion of /usr/bin/md5sum.textutils to /usr/bin/md5sum'
Adding `local diversion of /usr/share/man/man1/md5sum.textutils.1.gz to /usr/share/man/man1/md5sum.1.gz'

dpkg: parse error, in file `/var/lib/dpkg/status' near line 2 package `base-files':
 EOF after field name `'
chroot: cannot execute apt-get: No such file or directory
zcat: crc error
tar: Invalid tar header checksum
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2 package `dpkg':
 EOF after field name `'
```

---

### Post by synergynova on 2006-03-02
Still can't get the installation to go through...  I thought it might be something to do with the CD, so did a check on th CD's integrity, it says:
```
The ./install/vmlinuz file failed the MD5 checksum verification.
Your CD-ROM or this file may have been corrupted.
```
I've now used a new CD so I don't believe it to be the CD, I think there's probably an issue with the CD-ROM Drive.  Any ideas how to resolve this?

---

