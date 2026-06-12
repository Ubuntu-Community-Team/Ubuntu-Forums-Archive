---
title: "Installing Mono 2.0 on Mono 1.x"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by OsamaK on 2008-10-07
I downloaded Mono 2.0 tarball and compiled it on my Ubuntu 8.04 computer which already has Mono 1.9 installed. I did not remove the old version because of many software were depended on it.

I had some problem while running some software, plus, Ubuntu distro is not officially  supported by Mono community, therefore, I want to remove Mono 2.0 and back to the 'official' Ubuntu community version of Mono 1.9.

Somebody told me that it is more than removing a package and install another *"you'd have to clear out all the mono stuff and reinstall from package manager ..  by 'mono stuff' i mean everything to do with mono, not stuff that depends on mono"*.

Now, how to remove Mono 2.0 and back to Mono 1.9?

---

### Post by fd0man on 2008-10-13
For programs that use the autoconf system, you can "make uninstall".  Then you can "sudo apt-get --reinstall install" the affected packages.

However, not all of them will support that method, if you installed all of the tarballs for Mono 2.0.  If you did that, you'll have to manually go through the file lists that were installed ("make install" again will show you that information) and then follow that up with "sudo apt-get --reinstall install" for those Ubuntu packages.

A word of advice:  ALWAYS install custom software in /opt, /usr/local, or somewhere in your home directory.  Anywhere else is pretty much asking for trouble, because it can conflict with files installed by the package management system.

---

