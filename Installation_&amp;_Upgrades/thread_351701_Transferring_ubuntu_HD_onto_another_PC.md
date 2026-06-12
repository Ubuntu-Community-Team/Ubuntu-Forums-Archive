---
title: "Transferring ubuntu HD onto another PC"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by X-2 on 2007-02-02
Hi,

I have installed ubuntu on a slave HD on a PC, ubuntu configures the GRUB to recognise primary HD etc. 

What I'd like to do is use the ubuntu HD and put it on another PC with a primary HD with Xp on it. Ofcourse the problem was no GRUB was installed on the 2nd PC and I can't load or use the slave HD and ubuntu on it.

Is there any way using floppy etc use the slave HD with ubuntu already installed on a different PC?

Note: the reason I am trying to do this i can install ubuntu on 1 PC but the 2nd one :( .

Thanks

---

### Post by aysiu on 2007-02-03
I believe you can use the "repair an installation" boot option on the Alternate CD to reinstall Grub to the MBR after you've moved the slave drive in to the new computer.

With Grub installed, you should be able to dual boot properly.

---

