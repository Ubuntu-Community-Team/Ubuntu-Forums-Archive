---
title: "Compile MTPFS problems"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by Hero of Time on 2007-12-07
I downloaded the tar file from the mtpfs page ([http://www.adebenham.com/mtpfs/](http://www.adebenham.com/mtpfs/)) and want to compile it. I had to install automake to get the first part done, but when I try to compile, I get the error that I'm missing packages. When I try to apt-get them, they aren't found.

Error I get is:

No package 'fuse' found
No package 'mad' found
No package 'id3tag' found
No package 'libmtp' found

where the last one is strange, since I installed libmtp from the repo. It seems that it doesn't see that package correctly.

What do I need to get it working? Any help is much appreciated. I want to mount my mp3 player (Creative Zen Vision:M) so I can put my music on it like I can with the Creative Media Explorer that works in Windows.

---

### Post by Conor Gallagher on 2007-12-15
You need to install the development (libmtp-devel fuse-devel etc) packages as well.

---

### Post by Hero of Time on 2007-12-15
I will try that once I reboot to Linux. It does make sense, but when I searched for 'fuse' I couldn't find any packages with that name. And as far as I know, there isn't any libmtp-devel package.

---

### Post by Hero of Time on 2007-12-17
Ok, it got compiled. Now I need to install it. Somehow, ./install-sh won't work, it says no input file specified.

Anything I missed?

Edit:
I removed everything I had, then recompiled again from source, sudo make, sudo make install and it works. Well, as far as I can tell. I have to connect my mp3 player before I really know if it works, but I do get the mtpfs command if I type 'mtp<tab>'.

---

### Post by Hero of Time on 2007-12-17
For others who are interrested, I have the Creative Zen Vision:M 60 GB and this program works just fine. It's a bit slow and CPU intensive, but it gets the job done.

---

