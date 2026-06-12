---
title: "Apt-get update fail"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by Ernie S. on 2010-04-09
I apologize if this is posted elsewhere, but after a few searches I came up blank. My question is how do I redirect apt-get to look under current distro repositories? I upgraded recently to Karmic from Jaunty, yet apt-get is still looking for Jaunty. ie

sudo apt-get update returns this:
```

sudo apt-get update
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty Release.gpg
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/restricted Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty Release
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/main Packages

etc....

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

ernie@ubuntu:~$
```I know this has to be an easy fix, I'm just too new to know what to do about it :) Thanks in advance!

---

### Post by HyperFlexed on 2010-04-09
Check out /etc/apt/sources.list

---

### Post by Ernie S. on 2010-04-10
SOLVED ~ Thanks! I still had the Jaunty official release checked. I knew there was a simple fix :guitar:

---

