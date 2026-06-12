---
title: "Synaptic Error"
date: 2005-10-08
forum: Installation &amp; Upgrades
---

### Post by gman2004 on 2005-10-08
I try to open synsptic and I got this error:

W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/multiverse Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Suggestions!

---

### Post by aysiu on 2005-10-08
Your /etc/apt/sources.list may not be up-to-date.
Try following these instructions:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by gman2004 on 2005-10-08
I follow the instructions but cl;ose to the end I got this message:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release](http://archive.ubuntu.com/ubuntu/dists/breezy/Release)  Unable to find expected entry  multivers/source/Sources in Meta-index file (malformed Release file?)

---

### Post by gman2004 on 2005-10-08
I did it again and no error  show!

---

### Post by Pablo_Escobar on 2005-10-08
Then don't worry , be happy :)

Maybe some small problem with Your ISP ?? :)

No error = happy man :D

---

