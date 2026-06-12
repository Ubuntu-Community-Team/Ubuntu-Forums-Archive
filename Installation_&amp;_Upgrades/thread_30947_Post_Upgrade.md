---
title: "Post Upgrade"
date: 2005-05-01
forum: Installation &amp; Upgrades
---

### Post by larry on 2005-05-01
Dear all,
I am a newbie and I have just upgraded from warty to hoary.
A silly question about the post upgrade; in the notes online I read:


if you are Not running NFS (Network File System) as a client or a server then remove the portmap package:

sudo apt-get --purge remove portmap

How can I find out if that is my case, i.e. how do I get to know what is my filesystem?

Regards
Larry

---

### Post by Leif on 2005-05-01
NFS, as its name suggests, is a remote file system. Your computer does not have an NFS drive by default. The only way you would have it would be if you had personally set it up.

---

