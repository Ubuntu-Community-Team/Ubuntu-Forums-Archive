---
title: "Installing Xubuntu with limitations"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by tegalogic on 2007-10-16
Hello, I have a problem here.
I have an old Dell Inspiron 5000 computer that I want to install Xubuntu on.
However, it doesn't have a CD drive (I want to overwrite Windows 98 SE fully), and there is only limited space (1.5 GB). I think the memory is enough (192 MB), though. Also, I can't use a USB stick.

What can I do to successfully install Xubuntu, or is it impossible?

---

### Post by PacketCollision on 2007-10-16
You have two choices, use loadlin (or another program) to bootstrap Linux from DOS, or do a network (PXE) install.  I personally find the second method to be far easier, in fact, it's how I do all of my Ubuntu installs.  You'll need a second computer to do the netboot.  A quick Google turns up [this]("https://help.ubuntu.com/community/Installation/Netboot") in the ubuntu wiki, also [these]("http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install") complicated-looking instructions from some other wiki.  Good luck!

---

