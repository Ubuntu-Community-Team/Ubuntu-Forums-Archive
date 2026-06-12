---
title: "Looking for advice on updating"
date: 2015-12-22
forum: Installation &amp; Upgrades
---

### Post by Eagle Nest on 2015-12-22
HI Ubuntu friends. For the time being, I am using 12.04 in a dual boot environment. I will do the** upgrade** when I need to. 

The** question I have is about updating**. Which updates do I say yes to? The Update Manager provides a list of items, separated into "Important Security Updates" and "Recommended Updates" every once in a while, and I usually just say yes to them all. 

I usually do the important ones first, anything to do with the kernel, and if they look really important then I attach the laptop to a hard line/ethernet cable connected to the router rather than using the household wifi. The latter sometimes craps out what with the less than perfect ISP I have. 

But some guidance, if there is any such advice, about the updates would be helpful. I have plenty of room, for the time being. But it is a dual boot, and that other OS is a pig. 

Let's see now, here is a list of some of the current updates ...

Ubuntu updates

Important Security Updates

Version of host bundled with BIND 9.X
Clients provided with BIND
Safe and easy web browser from Mozilla
Eng lang pack for Firefox
Open Printing Printer Support
GRand Unified Bootloader x3 (version, binaries, common files for ver 2)
BIND9 Shared Library used by BIND
DNS Shared Library used by BIND
ISC Shared LIbrary used by BIND
Common Channel Library used by
Config File Handling Library used by
Lightweight Resolver Lib used by
GNOME XML library
XML Utilities
Complete Generic Linux kernel
Header file re kernel
Linux kernel headers
etc
etc 

and then the recommended updates...

---

### Post by veddox on 2015-12-22
In general, updates don't take up that much space - indeed, if you find yourself with too little space to carry out an update, I would say it's high time to add another drive/buy a new computer. Thus, disk space should not really be a consideration in whether or not to install your updates.

General advised policy is to always stay up to date with everything, as you have been doing so far. Apart from the security updates, whose importance I need not go into, updates fix bugs and add new features. Some updates are necessary to keep up with dependencies - say your desktop program 'foo' depends on some library 'bar', and 'bar' makes a version jump that introduces incompatibilities, then 'foo' needs to be updated as well. Thus, if you install the new version of 'bar' but not the new version of 'foo' (or vice versa), you're going to run into trouble.

The only exception when you shouldn't install an update is if you know that a certain update is broken. However, that should never happen (major fail by the software vendors).

In short, just install everything the updater says.

---

### Post by Eagle Nest on 2015-12-23
OK, that's helpful.

---

### Post by ian-weisser on 2015-12-23
Veddox is right: Say yes to all updates.

If connectivity is an issue, then say NO to all updates, and use the shell instead.
```
sudo apt-get --download-only upgrade      ## Download all upgrades to cache without installing - safe/resumable in case of network failure
sudo apt-get upgrade                      ## Upgrade from cache
```

---

