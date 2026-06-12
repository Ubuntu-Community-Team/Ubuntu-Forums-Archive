---
title: "Virtual desktop on server for remote"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by Khao on 2009-12-24
Hi,

I'm trying to install a virtual ubuntu desktop version on a server ubuntu to do some testing via remote desktop.. I've searched but couldn't find a way to do this. I already have 1 virtual server on the machine installed with kvm and vmbuilder but I don't think I can create an ubuntu-desktop version with vmbuilder.. Can anybody help me do this? 

Thank you
Khao

---

### Post by lancealbertson on 2011-02-21
I am trying to do the exact same thing.

First, you can create desktop VM by downloading the desktop ISO of your choice and passing that in as an parameter to vmbuilder instead of using the mirror.

However, once I get it installed I don't know how to access the desktop GUI. I can get in via ssh.

Part of the problem that Remote Desktop is disabled by default, so you have to enable it via the command line. Somehow. But even after that I'm not sure how to bring up the GUI. 

I'd like to run the GUI from inside Windows. I know this is not much help, but maybe we can figure it out.

---

