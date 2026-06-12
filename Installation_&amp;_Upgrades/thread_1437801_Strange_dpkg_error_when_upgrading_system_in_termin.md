---
title: "Strange dpkg error when upgrading system in terminal..."
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by Izobalax on 2010-03-24
Afternoon all...

Yesterday I started getting a strange error when updating and upgrading my system. I have no idea what's caused this or why it's occurring but it's stopping me keeping my system updated. 

To update my system in the terminal, which I do daily, I usually enter:

```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

I've got a few updates to upgrade today:
```
The following packages will be upgraded:
  devicekit-disks gstreamer0.10-plugins-bad libsmbclient libwbclient0
  samba-common samba-common-bin smbclient
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.9MB of archives.
After this operation, 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]? y
```

However, the upgrade stops here:
```
Get: 1 http://gb.archive.ubuntu.com karmic-updates/main devicekit-disks 007-2ubuntu5 [166kB]
Get: 2 http://security.ubuntu.com karmic-security/main libwbclient0 2:3.4.0-3ubuntu5.6 [103kB]
Get: 3 http://gb.archive.ubuntu.com karmic-updates/universe gstreamer0.10-plugins-bad 0.10.14-4ubuntu1.1 [1,325kB]
Get: 4 http://security.ubuntu.com karmic-security/main libsmbclient 2:3.4.0-3ubuntu5.6 [1,652kB]
Get: 5 http://security.ubuntu.com karmic-security/main smbclient 2:3.4.0-3ubuntu5.6 [11.4MB]
Get: 6 http://security.ubuntu.com karmic-security/main samba-common 2:3.4.0-3ubuntu5.6 [388kB]
Get: 7 http://security.ubuntu.com karmic-security/main samba-common-bin 2:3.4.0-3ubuntu5.6 [4,789kB]
Fetched 19.9MB in 17s (1,139kB/s)                                              
Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/status' near line 1974 package 'xfonts-mathml':
 invalid package name (character ` ' not allowed (only letters, digits and characters `-+._'))
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

How can I fix this, O' Wise People?

/izo\

---

### Post by Dead Pixel on 2010-03-24
There seems to be a problem in the package list. Open the list in gedit and go to line 1974.

```

sudo gedit /var/dpkg/status

```

Can you copy the line and post it?

---

### Post by Izobalax on 2010-03-24
> **Dead Pixel said:**
> There seems to be a problem in the package list. Open the list in gedit and go to line 1974.

```

sudo gedit /var/dpkg/status

```

Can you copy the line and post it?


Thank you for the prompt response!

The line in question is this:
```
: Atsuhito KOHDA <kohda@debian.org>
```

Which is... odd. 

/izo\

---

### Post by Dead Pixel on 2010-03-24
Strange indeed. Can you copy the entire package section which it is in?

---

### Post by Izobalax on 2010-03-24
> **Dead Pixel said:**
> Strange indeed. Can you copy the entire package section which it is in?


Certainly:
```
Package: xfonts-mathml
Status: install ok installed
Priority: extra
Section: x11
Installed-Size: 152
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: all
Version: 2
Depends: defoma, xfonts-utils
Recommends: latex-xft-fonts
Suggests: ttf-mathematica4.1
Conffiles:
 /etc/X11/fonts/Type1/xfonts-mathml.scale 3928791fa92cf3bd6597c3fe224379c6
 /etc/defoma/hints/xfonts-mathml.hints a5984e4966b881253e223e327acddfb4
Description: Type1 Symbol font for MathML
 To display web pages containing MathML equations properly with
 MathML-enabled browsers, you will need TeX's Computer Modern fonts,
 Type1 'Symbol' font, Mathematica 4.1 fonts and some Other fonts
 (MathType's fonts) installed on your computer.
 .
 This package provides Type1 Symbol font which is modified from
 s050000l.pfb of gsfonts with FontForge.
 .
 You will also need to install the packages: latex-xft-fonts (TeX's
 Computer Modern fonts) and ttf-mathematica4.1 (Mathematica 4.1 fonts)
 to view MathML properly.
: Atsuhito KOHDA <kohda@debian.org>
```

/izo\

---

### Post by plucky on 2010-03-24
> The line in question is this:
Code:

: Atsuhito KOHDA <kohda@debian.org>

Which is... odd. 


Mine has ```
Original-Maintainer: Atsuhito KOHDA <kohda@debian.org>
```
It is missing **Original-Maintainer** and doesn't like the : at the beginning of the line.

Good Luck

---

### Post by Izobalax on 2010-03-24
> **plucky said:**
> Mine has ```
Original-Maintainer: Atsuhito KOHDA <kohda@debian.org>
```
It is missing **Original-Maintainer** and doesn't like the : at the beginning of the line.

Good Luck


You're right! I added "Original-Maintainer" at the beginning of the line and the update has gone through fine. Thanks for that. I wonder why that happened. 

/izo\

---

