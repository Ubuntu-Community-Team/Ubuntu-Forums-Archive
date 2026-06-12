---
title: "[SOLVED] partial dpkg install leaves software index broken"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by spaceScout on 2008-11-24
I attempted to do a manual install of some printer drivers since I had a printer error, which I'll get into once this mess gets figured out, but the install did not go through all the way, perhaps because of some other dependencies, and now I can't run the package updater nor can I uninstall the errant package.

Here's where we are.  I have the Do Not Enter sign on my top panel, which gives me a very long tool tip saying, in essence, that a package, mfc8440lpr, needs to be install, but it can't find an archive for it.  Also when I run "sudo apt-get install -f", it says 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc8440lpr needs to be reinstalled, but I can't find an archive for it.

  Well, I have the archive right here in a directory, and I got errors when I originally tried to install it, so now I'm thinking that I'm in that in-between state where I can't install the package that's in error, and so because I can't install it, I can't remove it.  When I try to remove mfc8440lpr, using "sudo dpkg -P mfc8440lpr", I get

dpkg: error processing mfc8440lpr (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 mfc8440lpr

Any hints on how to get out of this mess?

Thanks,
  sS

---

### Post by spaceScout on 2008-11-24
Fixed it.  I guess silence means Read The Fine Manual.

---

