---
title: "vmware-server-kernel-modules : No -386 modules?"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by wirah on 2007-12-11
Hi

I've just upgraded my vmware-server installation from source, using the ubuntu canonical commercial repos.

However I am baffled as to why modules for my -386 kernel are not included?

Running kernel is:

% uname -a                                                                                                                                   (/)
Linux antix 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux

However, vmnet and vmmon modules have only been supplied for -server and -generic kernels. I even cracked open the .deb to check what was inside it, and there are two folders, /lib/modules/...generic and /lib/modules/...server

Meaning, when I try to start vmware, I get:

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

Thanks,
Antony

anybody know why this is the case?

---

