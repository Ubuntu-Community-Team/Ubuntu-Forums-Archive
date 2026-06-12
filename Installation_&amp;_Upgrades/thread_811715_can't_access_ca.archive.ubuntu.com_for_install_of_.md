---
title: "can't access ca.archive.ubuntu.com for install of software??"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by eheyl on 2008-05-29
Hey all. Everything was great until RIGHT NOW. when I can't seem to get access to ca.archive.ubuntu.com for my software installs. Not quite sure what to do about this, It was working fine till today and I haven't changed a thing. Can someone shed some light? are they changing things around or something? It just times out, and I've loaded several web pages and the internet connection is fine.....help! I like to keep things updated and get new software....

I've tried apt-get update and it times out when it gets to that repo.

Here's the error code:

Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main tcl8.4 8.4.16-4ubuntu1
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main tk8.4 8.4.16-2ubuntu1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main blt 2.4z-4ubuntu1
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main python-tk 2.5.2-0ubuntu2
  Unable to connect to ca.archive.ubuntu.com http:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main scribus 1.3.3.11.dfsg-1ubuntu4
  Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.16-4ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.16-4ubuntu1_i386.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tk8.4/tk8.4_8.4.16-2ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tk8.4/tk8.4_8.4.16-2ubuntu1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/blt/blt_2.4z-4ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/blt/blt_2.4z-4ubuntu1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python-stdlib-extensions/python-tk_2.5.2-0ubuntu2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python-stdlib-extensions/python-tk_2.5.2-0ubuntu2_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/s/scribus/scribus_1.3.3.11.dfsg-1ubuntu4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/s/scribus/scribus_1.3.3.11.dfsg-1ubuntu4_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

---

### Post by zvacet on 2008-05-29
Probably server is temporary down.**System>admin>software sources<select main server**

---

