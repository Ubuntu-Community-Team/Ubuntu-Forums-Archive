---
title: "Can't install packages"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by sethosayher on 2005-08-01
I've been attempted to install a few packages (one for amsn and xmms), .deb files. Whenever I try to lauch it in synaptic, it informs me that I must run it as root...I tried opening the package in the console in sudo mode, but then it informs me:

root@sethosayher:/home/sethosayher # sudo install /home/sethosayher/Desktop/xmms_1.2.10+cvs20050209-2_i386.deb
install: too few arguments
Try `install --help' for more information.

Any ideas? Is this a permissions issue? Am I missing anything? I'm somewhat new to Ubuntu (and debian), and I could use some help...thank you ^_^

---

### Post by Xian on 2005-08-01
Place that file 'xmms_1.2.10+cvs20050209-2_i386.deb'
in your /home/username/ directory.

Then open a terminal and issue this command:
```
$ sudo dpkg -i xmms_1.2.10+cvs20050209-2_i386.deb
```

---

