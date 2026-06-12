---
title: "&quot;package system broken&quot; error on ubuntu 12.04 LTS"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by vivekkholia on 2014-04-27
Hi, 
 I've come across a problem while updating. The update manager displayed an error saying that the package system is broken. The following is the output of the error message.
```

The following packages have unmet dependencies:

libwmf0.2-7-gtk: Depends: libc6 (>= 2.3.6-6~) but 2.15-0ubuntu10.5 is installed
                 Depends: libgdj-pixbuf2.0-0 (>= < 2.22.0(, libglIb2.0-0 >= 2.12.0) but it is not installed
                 Depends: libwmf0.2-7 (= 0.2.8.4-10ubuntu1) but 0.2.8.4-10ubuntu1 is installed
onboard: Depends: python (>= 2.7.1-0ubuntu2) but 2.7.3-0ubuntu2.2 is installed
         Depends: libc6 (>= 2.4) but 2.15-0ubuntu10.5 is installed
         Depends: libglib2.0-0 (>= 2.24.0) but 2.32.4-0ubuntu1 is installed
         Depends: libgtk-3-0 (>= 3.0.0(, libx10-6, libxi6 (>= 2:1.2.99.4) but 3.4.2-0ubuntu0.8 is installed
         Depends: gir1.2-pango-1.0 (>= 1.29.3) but 1.30.0-0ubuntu3.1 is installed


```

I tried this command:

```

sudo apt-get install -f

```

The output is the following
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libwmf0.2-7-gtk onboard
The following packages will be upgraded:
  libwmf0.2-7-gtk onboard
2 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
5 not fully installed or removed.
Need to get 0 B/412 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error: parsing file '/var/lib/dpkg/status' near line 32883 package 'libwmf0.2-7-gtk':
 `Depends' field, reference to `libgdj-pixbuf2.0-0':
 bad version relationship ><
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I followed the error message and saw the line 32883 in the file */var/lib/dpkg/status*.
The following the the section of the file* /var/lib/dpkg/status* containing information about the package [I]libwmf0.2-7-gtk
[/I]
```

Package: libwmf0.2-7-gtk
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 63
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: libwmf
Version: 0.2.8.4-10ubuntu1
Depends: libc6 (>= 2.3.6-6~), libgdj-pixbuf2.0-0 (>< 2.22.0(, libglIb2.0-0 >= 2.12.0), libWmf0.2-7 (= 0.2.8.4-10ubuntu1)
Description: Windows metafile conversion library
 Windows metafile (WMF) is a picture format used by many Windows
 programs, e.g. Microsoft Word.  libwmf is a library for interpreting
 metafile images and either displaying them using X or converting them
 to standard formats such as PNG, JPEG, PS, EPS and SVG(Z)...
 .
 This package contains the GTK pixbuf plugin.
Original-Maintainer: Loïc Minier <lool@debian.org>

```

The problem I suspect is the line saying:
 [I]Depends: libc6 (>= 2.3.6-6~), libgdj-pixbuf2.0-0 (>< 2.22.0(,  libglIb2.0-0 >= 2.12.0), libWmf0.2-7 (= 0.2.8.4-10ubuntu1)

[/I]So I tried to correct it by rewriting it:
*[I]Depends: libc6 (>= 2.3.6-6~), libgdk-pixbuf2.0-0 (>= 2.22.0),  libglib2.0-0 (>= 2.12.0), libWmf0.2-7 (= 0.2.8.4-10ubuntu1)*
[/I]
but now the update manager can't even parse the file* /var/lib/dpkg/status. *I'm not able to install or remove any software in my system. And if any one is wondering about the third party repos*, *I'm not using any.
Please help me resolve this issue.

---

### Post by Bashing-om on 2014-04-27
vivekkholia; Hi !

As a suggestion.

Take a peek at the backup file '/var/lib/dpkg/status-old' and see what the difference is. Then one might copy the backup file back into place of the 'status' file. and see what results when the system is updated.
Always a good practice to make a backup of any file that one is working on/with -> Murphy's Law always applies.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by vivekkholia on 2014-04-28
> Take a peek at the backup file '/var/lib/dpkg/status-old' and see what  the difference is. Then one might copy the backup file back into place  of the 'status' file. and see what results when the system is updated.

It worked! I tried the backup file in place of the original file and I was able to update the system. I can install and remove softwares. Everything is back to normal again.

Thank you very much Bashing-om!

---

### Post by Bashing-om on 2014-04-28
vivekkholia; Hey;

Glad it worked out, and all that the fault was a bad index that had a replacement ( ain't it a wonderful system !).

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

