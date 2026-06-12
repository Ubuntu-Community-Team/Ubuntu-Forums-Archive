---
title: "weird apt-get errors"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by stateq2 on 2005-09-08
I recently reinstalled ubuntu from a warty cd I had, and now when I connect it to the net to install extra software and such, I get these weird errors.

```

stateq2@ubuntu:~ $ sudo apt-get install xine
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com warty/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_warty_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com warty/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com warty-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_warty-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com warty-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_warty-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com warty/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com warty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_warty-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com warty-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_warty-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com warty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_warty-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com warty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package xine

```

and this happens when I try to install anything...as well as apt-get update.  i know the network is working, because that's how I'm making this post.  any ideas?  thanks.

---

### Post by Cashel on 2005-09-09
[QUOTE=stateq2]I recently reinstalled ubuntu from a warty cd I had, and now when I connect it to the net to install extra software and such, I get these weird errors.
...
and this happens when I try to install anything...as well as apt-get update.  i know the network is working, because that's how I'm making this post.  any ideas?  thanks.[/QUOTE]

If you vi /etc/apt/sources.list you'll see where apt's looking for packages.... I would try dumping the us. bit, my line looks like so... 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

replace hoary w/ warty and you should be good to go... if not try deb-src instead of deb....

... you also might wanna try moving the files in /var/lib/apt/lists to your home directory, perhaps they are outdated / corrupted?

Good luck!

---

### Post by rafakl on 2005-09-09
dont worry about these errors, in one post i read that is because of missing files in the mirrormax servers, but you still will be able to retreive packages from them. just ignore these errors.

for the xine error..... the problem is that the package is not called xine, its called xine-ui, so try:

sudo apt-get install xine-ui

 :razz:

---

