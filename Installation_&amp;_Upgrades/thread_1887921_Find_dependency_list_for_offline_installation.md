---
title: "Find dependency list for offline installation?"
date: 2011-11-28
forum: Installation &amp; Upgrades
---

### Post by Jonathan L on 2011-11-28
Hello all

Perhaps someone can help me with a package management question.

I am installing a system which needs to be recreatable, offline, and I'm getting stuck in the maze of package management.  What I want is a command which tells me (recusively) what depencies would need to be installed for installing a given package file, perhaps from an install CD tree.

That is, I want something along the lines of this:```
$ **magiccommand nfs-kernel-server /mnt**
/mnt/pool/main/p/portmap/portmap_6.0.0-1ubuntu2.1_i386.deb
/mnt/pool/main/libe/libevent/libevent-1.4-2_1.4.13-stable-1_i386.deb
/mnt/pool/main/libg/libgssglue/libgssglue1_0.1-4_i386.deb
/mnt/pool/main/libn/libnfsidmap/libnfsidmap2_0.23-2_i386.deb
/mnt/pool/main/libr/librpcsecgss/librpcsecgss3_0.19-2_i386.deb
/mnt/pool/main/n/nfs-utils/nfs-common_1.2.0-4ubuntu4.1_i386.deb
/mnt/pool/main/n/nfs-utils/nfs-kernel-server_1.2.0-4ubuntu4.1_i386.deb

```[FONT=Arial][SIZE=1]which is a sequence of package files each installable with dpkg -i, and in the right order[/SIZE][/FONT]
[FONT=Arial]dpkg -I appears to have "or" in the dependencies: how do you know which one it will install?

Thanks all if you've got a good tip.

This is 10.04.3 server, if it matters.

Kind regards,
Jonathan.
[/FONT]

---

### Post by tartalo on 2011-11-28
[http://www.howtoforge.com/checking-package-dependencies-with-apt-rdepends-on-debian-ubuntu](http://www.howtoforge.com/checking-package-dependencies-with-apt-rdepends-on-debian-ubuntu)

If you find yourself in this situation often, Debian might be a better option because you can download all the repositories in DVD.

---

### Post by Jonathan L on 2011-11-28
Hi Tartalo

> **tartalo said:**
> [http://www.howtoforge.com/checking-package-dependencies-with-apt-rdepends-on-debian-ubuntu](http://www.howtoforge.com/checking-package-dependencies-with-apt-rdepends-on-debian-ubuntu)

If you find yourself in this situation often, Debian might be a better option because you can download all the repositories in DVD.

Thanks, that looks like a good start.  What I'm actually seeking is a method to decide which package files need to go on a distribution medium, and generate a script of dpkg -i filename to install them.

I suppose we might describe this as compiling an apt-get -install into a series of wget/cp and dpkg -i

The rdepend looks useful though.

Thanks again.

Kind regards,
Jonathan.

---

