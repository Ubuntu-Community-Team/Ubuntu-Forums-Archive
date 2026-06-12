---
title: "Warning boot issues on latest kernel upgrade when having / encrypted"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by crypope on 2008-10-15
Hi,

Just to let everyone know that I run into some issues today when I upgraded my kernel to lates 2.6.24-21 version as of today release. I am running a Ubuntu 8.0.4 with root (/) encrypted with pvcrypt.

Everything went fine except the fact that I've got prompted with a window that warned me about the menu.lst that is going to be changed.

I have selected the option to see the differences and I saw that instead of my normal UUID from blkid currently used for root (/) the UUID got changed with another UUID that I could not figured out from where it came from.

As I precaution I saved my original from on root=UUID=".." on menu.lst and added it as a recovery entry on menu.lst.

I was really lucky that I have saved my UUID and added a recovery entry on menu.lst as the reboot with the new UUID did not worked. I was able to boot in recovery mode with my saved UUID.

I am wondering why the UUID got changed and from where it came the new one? Why would not use the one that was currently used to boot the system?

Chris

---

### Post by QCompson on 2008-10-21
> **crypope said:**
> Hi,

Just to let everyone know that I run into some issues today when I upgraded my kernel to lates 2.6.24-21 version as of today release. I am running a Ubuntu 8.0.4 with root (/) encrypted with pvcrypt.

Maybe a silly question but what is pvcrypt, and is it different than the normal ubuntu encrypted lvm install?

---

