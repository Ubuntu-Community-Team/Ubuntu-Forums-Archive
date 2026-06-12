---
title: "Can't install (hangs on ' select a disk')"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by Mennoz on 2006-07-31
[IMG]http://i7.tinypic.com/21l1j80.png[/IMG]
I can't get past this point of the install. It just hangs, but the installer and Ubuntu self don't crash.

I have a 250GB Sata2 HD, I don't know if this has something to do with it. 
I've also installed Windows XP allready on this hard drive.

Some one knows why it hangs?

---

### Post by Mennoz on 2006-08-01
I found the problem, it's the sata2-controller on my mobo, an Asrock 939 dual-sata, that is not supported by the Kernel, since i don't know how to compile the new kernel (which does support my sata2-controller) into Ubuntu, i just installed my HD on the sata1 controller, now it works fine:lol:

---

