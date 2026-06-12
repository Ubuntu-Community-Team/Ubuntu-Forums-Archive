---
title: "Unable to fix broken Adobe Flash installation"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by indiapavan on 2010-04-07
I just installed Ubuntu 9.04 again on my PC after a long time. Everything was working fine. No problems at all. After running all the necessary updates, I wanted to install Adobe Flash. This I did by going to [Adobe's site]("http://get.adobe.com/flashplayer/"). I selected the APT version for 9.04+. It was installing fine UNTIL there was a power cut. Since then I have been trying out various methods of repair suggested in these forums. But again and again I get the same message:

> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


Please somebody help me if possible. Thanks in advance.

---

### Post by shaohu.xie on 2010-04-07
You try follow command please

1. $ cd /var/lib/apt/lists/partial
2. $ sudo rm -rf *
3. Restore sources.list file to default status. 
4. $ sudo apt-get update -o Acquire::http::No-Cache=true
5. $ sudo apt-get update

---

