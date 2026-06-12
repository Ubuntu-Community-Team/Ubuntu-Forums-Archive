---
title: "Major Issue with updates and applications"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by surtees1985 on 2013-04-25
Hi all

I'm hoping that someone out there would be able to help as I'm now tearing my hair out trying to resolve a major is we are having.

We have a Ubuntu server (Dell Poweredge) running Ubuntu 10.10 maverick with various applications (i.e. Moodle, Prestashop etc) for education use. 

The problem is, is that we are unable to update the main ubuntu install or any of the applications which run on the server through their 1 click updates.

When we run the sudo apt-get update we get the error messages as below

```
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse i386 Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
N: Ignoring file 'preferences.d' in directory '/etc/apt/apt.conf.d/' as it has a
n invalid filename extension
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)
Could not connect to gb.archive.ubuntu.com:80 (91.189.92.202). - connect (110: C
onnection timed out) [IP: 91.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Tra](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Tra)
nslation-en.bz2  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189.92
.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i1](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i1)
8n/Translation-en.bz2  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.
189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i1](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i1)
8n/Translation-en.bz2  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.
189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n)
/Translation-en.bz2  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.18
9.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Relea](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Relea)
se.gpg  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/)
i18n/Translation-en.bz2  Unable to connect to gb.archive.ubuntu.com:http: [IP: 9
1.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multi](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multi)
verse/i18n/Translation-en.bz2  Unable to connect to gb.archive.ubuntu.com:http:
[IP: 91.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restr](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restr)
icted/i18n/Translation-en.bz2  Unable to connect to gb.archive.ubuntu.com:http:
[IP: 91.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/unive](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/unive)
rse/i18n/Translation-en.bz2  Unable to connect to gb.archive.ubuntu.com:http: [I
P: 91.189.92.202 80]


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)
Could not connect to archive.canonical.com:80 (91.189.92.150). - connect (110: C
onnection timed out) [IP: 91.189.92.150 80]


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/)
Translation-en.bz2  Unable to connect to archive.canonical.com:http: [IP: 91.189
.92.150 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Releas](http://security.ubuntu.com/ubuntu/dists/lucid-security/Releas)
e.gpg  Could not connect to security.ubuntu.com:80 (91.189.92.184). - connect (1
10: Connection timed out) [IP: 91.189.92.184 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i)
18n/Translation-en.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.1
89.92.184 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiv](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiv)
erse/i18n/Translation-en.bz2  Unable to connect to security.ubuntu.com:http: [IP
: 91.189.92.184 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restri](http://security.ubuntu.com/ubuntu/dists/lucid-security/restri)
cted/i18n/Translation-en.bz2  Unable to connect to security.ubuntu.com:http: [IP
: 91.189.92.184 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/univer](http://security.ubuntu.com/ubuntu/dists/lucid-security/univer)
se/i18n/Translation-en.bz2  Unable to connect to security.ubuntu.com:http: [IP:
91.189.92.184 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/Release.gp](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/Release.gp)
g  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/)
Translation-en.bz2  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189
.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted)
/i18n/Translation-en.bz2  Unable to connect to gb.archive.ubuntu.com:http: [IP:
91.189.92.202 80]


W: Failed to fetch [http://download.openpanel.com/deb/dists/maverick/Release.gpg](http://download.openpanel.com/deb/dists/maverick/Release.gpg)
 Could not connect to download.openpanel.com:80 (89.31.100.118). - connect (110:
 Connection timed out)


W: Failed to fetch [http://download.openpanel.com/deb/dists/maverick/main/i18n/Tr](http://download.openpanel.com/deb/dists/maverick/main/i18n/Tr)
anslation-en.bz2  Unable to connect to download.openpanel.com:http:


W: Failed to fetch [http://apt.nuxeo.org/dists/precise/Release.gpg](http://apt.nuxeo.org/dists/precise/Release.gpg)  Could not con
nect to apt.nuxeo.org:80 (212.85.154.59). - connect (110: Connection timed out)


W: Failed to fetch [http://apt.nuxeo.org/dists/precise/releases/i18n/Translation-](http://apt.nuxeo.org/dists/precise/releases/i18n/Translation-)
en.bz2  Unable to connect to apt.nuxeo.org:http:


W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/jav/ubuntu/dists/maver](http://ppa.launchpad.net/ferramroberto/jav/ubuntu/dists/maver)
ick/Release.gpg  Could not connect to ppa.launchpad.net:80 (91.189.95.83). - con
nect (110: Connection timed out)


W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/jav/ubuntu/dists/maver](http://ppa.launchpad.net/ferramroberto/jav/ubuntu/dists/maver)
ick/main/i18n/Translation-en.bz2  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Could
not connect to packages.medibuntu.org:80 (88.191.127.22). - connect (110: Connec
tion timed out)


W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/i18n/Translati](http://packages.medibuntu.org/dists/lucid/free/i18n/Translati)
on-en.bz2  Unable to connect to packages.medibuntu.org:http:


W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/i18n/Trans](http://packages.medibuntu.org/dists/lucid/non-free/i18n/Trans)
lation-en.bz2  Unable to connect to packages.medibuntu.org:http:


W: Failed to fetch [http://ppa.launchpad.net/schooltool-owners/dev/ubuntu/dists/m](http://ppa.launchpad.net/schooltool-owners/dev/ubuntu/dists/m)
averick/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch [http://ppa.launchpad.net/schooltool-owners/dev/ubuntu/dists/m](http://ppa.launchpad.net/schooltool-owners/dev/ubuntu/dists/m)
averick/main/i18n/Translation-en.bz2  Unable to connect to ppa.launchpad.net:htt
p:


W: Failed to fetch [http://ppa.launchpad.net/schooltool-owners/ppa/ubuntu/dists/l](http://ppa.launchpad.net/schooltool-owners/ppa/ubuntu/dists/l)
ucid/Release.gpg  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch [http://ppa.launchpad.net/schooltool-owners/ppa/ubuntu/dists/l](http://ppa.launchpad.net/schooltool-owners/ppa/ubuntu/dists/l)
ucid/main/i18n/Translation-en.bz2  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/jav/ubuntu/dists/maver](http://ppa.launchpad.net/ferramroberto/jav/ubuntu/dists/maver)
ick/main/source/Sources.gz  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/jav/ubuntu/dists/maver](http://ppa.launchpad.net/ferramroberto/jav/ubuntu/dists/maver)
ick/main/binary-i386/Packages.gz  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch [http://download.openpanel.com/deb/dists/maverick/main/source/](http://download.openpanel.com/deb/dists/maverick/main/source/)
Sources.gz  Unable to connect to download.openpanel.com:http:


W: Failed to fetch [http://apt.nuxeo.org/dists/precise/releases/source/Sources.gz](http://apt.nuxeo.org/dists/precise/releases/source/Sources.gz)
  Unable to connect to apt.nuxeo.org:http:


W: Failed to fetch [http://download.openpanel.com/deb/dists/maverick/main/binary-](http://download.openpanel.com/deb/dists/maverick/main/binary-)
i386/Packages.gz  Unable to connect to download.openpanel.com:http:


W: Failed to fetch [http://apt.nuxeo.org/dists/precise/releases/binary-i386/Packa](http://apt.nuxeo.org/dists/precise/releases/binary-i386/Packa)
ges.gz  Unable to connect to apt.nuxeo.org:http:


W: Failed to fetch [http://ppa.launchpad.net/schooltool-owners/dev/ubuntu/dists/m](http://ppa.launchpad.net/schooltool-owners/dev/ubuntu/dists/m)
averick/main/source/Sources.gz  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch [http://ppa.launchpad.net/schooltool-owners/dev/ubuntu/dists/m](http://ppa.launchpad.net/schooltool-owners/dev/ubuntu/dists/m)
averick/main/binary-i386/Packages.gz  Unable to connect to ppa.launchpad.net:htt
p:


W: Failed to fetch [http://ppa.launchpad.net/schooltool-owners/ppa/ubuntu/dists/l](http://ppa.launchpad.net/schooltool-owners/ppa/ubuntu/dists/l)
ucid/main/binary-i386/Packages.gz  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Pa](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Pa)
ckages.gz  Unable to connect to packages.medibuntu.org:http:


W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/binary-i38](http://packages.medibuntu.org/dists/lucid/non-free/binary-i38)
6/Packages.gz  Unable to connect to packages.medibuntu.org:http:


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binar](http://archive.canonical.com/ubuntu/dists/lucid/partner/binar)
y-i386/Packages.gz  Unable to connect to archive.canonical.com:http: [IP: 91.189
.92.150 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/source/S](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/source/S)
ources.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189.92.202 8
0]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/so](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/so)
urce/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189.92
.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/sour](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/sour)
ce/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189.92.2
02 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/so](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/so)
urce/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189.92
.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i)
386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189.92
.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/bi](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/bi)
nary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.
189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/bina](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/bina)
ry-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.18
9.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/bi](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/bi)
nary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.
189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/)
source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189.
92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restr](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restr)
icted/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 9
1.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/unive](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/unive)
rse/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.
189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multi](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multi)
verse/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 9
1.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/)
binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 9
1.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restr](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restr)
icted/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:
[IP: 91.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/unive](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/unive)
rse/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http: [I
P: 91.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multi](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multi)
verse/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:
[IP: 91.189.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/sourc](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/sourc)
e/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189.92.20
2 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted)
/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189
.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/binar](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/binar)
y-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP: 91.189
.92.202 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted)
/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http: [IP:
91.189.92.202 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/s](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/s)
ource/Sources.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.
184 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restri](http://security.ubuntu.com/ubuntu/dists/lucid-security/restri)
cted/source/Sources.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.1
89.92.184 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/univer](http://security.ubuntu.com/ubuntu/dists/lucid-security/univer)
se/source/Sources.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.189
.92.184 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiv](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiv)
erse/source/Sources.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.1
89.92.184 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/b](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/b)
inary-i386/Packages.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.1
89.92.184 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restri](http://security.ubuntu.com/ubuntu/dists/lucid-security/restri)
cted/binary-i386/Packages.gz  Unable to connect to security.ubuntu.com:http: [IP
: 91.189.92.184 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/univer](http://security.ubuntu.com/ubuntu/dists/lucid-security/univer)
se/binary-i386/Packages.gz  Unable to connect to security.ubuntu.com:http: [IP:
91.189.92.184 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiv](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiv)
erse/binary-i386/Packages.gz  Unable to connect to security.ubuntu.com:http: [IP
: 91.189.92.184 80]
```


Any help would be much appreciated. I have SSH access to the server.

Thanks

---

### Post by oldos2er on 2013-04-25
10.10 hasn't been supported for a year, which is why it's repositories are offline (moved to old-releases). You should consider installing 12.04 or newer.

---

### Post by surtees1985 on 2013-04-27
I cant sudo apt-get update as I get similar errors. Surely this wouldnt stop the applications from updating either.

---

### Post by ibjsb4 on 2013-04-27
EOL upgrades

[https://help.ubuntu.com/community/EOLUpgrades#Requirements](https://help.ubuntu.com/community/EOLUpgrades#Requirements)

---

### Post by oldos2er on 2013-04-27
> **surtees1985 said:**
> I cant sudo apt-get update as I get similar errors. Surely this wouldnt stop the applications from updating either.

That's exactly what it does. No updates,  no repositories.

---

### Post by snowpine on 2013-04-27
I recommend you install a Long Term Support (LTS) release. 12.04 is the current LTS and will be supported through April 2017.

Your output of apt-get update suggests that you upgraded from 10.04 Lucid. Ironically, if you had stuck with 10.04 instead of updating to 10.10, your server would still be under support. (Support for 10.04 server ends April 2015.)

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

