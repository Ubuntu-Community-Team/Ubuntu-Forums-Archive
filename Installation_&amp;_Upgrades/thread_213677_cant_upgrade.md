---
title: "cant upgrade"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by Paul VW on 2006-07-11
Hi I am currently using breezy badger since decemeber, and now the update manager says I can upgrade to draper drake, when I run the instaltion option, it downloads a few files then says
"Failed to fetch [http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz) 404 Not Found [IP: 203.16.234.20 80]
Failed to fetch [http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz) 404 Not Found [IP: 203.16.234.20 80]
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz) Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz) Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz) Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz) Unable to fetch file, server said ‘Failed to open file.

---

### Post by linear on 2006-07-11
Remove or comment out all non-standard repositories from /etc/sources.list before you start. There's good advice [here]("http://www.ubuntuforums.org/showthread.php?t=187656").

---

### Post by Paul VW on 2006-07-12
Thanks for that, I am a linux newbie, despite suing unbutu for 6 months - I just turn my machince on and use it, dont really know how it works :rolleyes: 

can I have how to do it in easy steps :oops:

---

### Post by linear on 2006-07-12
The link in my previous post will lead you to a variety of step-by-step instructions.

---

### Post by Paul VW on 2006-07-16
well i must be thick as i dont understand any of the soultions on that thread

can somone please point me in the right direction, or would it be easier to do a clean install??

---

### Post by linear on 2006-07-16
Clean install may or may not be easier, depending on what you have to lose.

Before you blow it all away, try cleaning up sources.list and running the upgrade again:

First make a backup. In a terminal window, type:

**sudo cp /etc/apt/sources.list /etc/apt/sources.old**

Then:

**gksudo gedit /etc/apt/sources.list**

Replace the contents with the clean sources.list from this post: [http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

Save, and then try the update as listed in the post.

---

### Post by Paul VW on 2006-07-17
thanks :D thats made things a lot clearer! :):)

---

