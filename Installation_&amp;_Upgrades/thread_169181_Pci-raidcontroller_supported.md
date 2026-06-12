---
title: "Pci-raidcontroller supported?"
date: 2006-05-02
forum: Installation &amp; Upgrades
---

### Post by fredrik_human on 2006-05-02
Hi, i was wondering if Ubuntu is currently supporting any pci-raidcontrolers for sata disks. 

My plan is to hook up two sets of raid1 in witch two 120Gb disks will provide the main backup for my network and two 250Gb disks will serve as central storage.

I've thougt of the Promise TX4310 controller but i don't know if it is supported in Ubuntu. Is there any list of supported devices?

---

### Post by yota on 2006-05-02
As you can see at:

[http://www.promise.com/support/download/download2_eng.asp?category=all&os=100&productID=165](http://www.promise.com/support/download/download2_eng.asp?category=all&os=100&productID=165)

there are binary precompiled drivers for redhat and suse, plus one that can be recompiled on every distro (most likely ubuntu too) for the tx4310.

But before going to the shop, please consider that with linux you don't necessarily need a raid controller 'cause the kernel can handle raid and volume management by itself (in software).

[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)

With Ubuntu you can configure raid directly with it's installer.
Software raid has several benefits (different raid types on the same disk, portability of a raid set across different machines).

Moreover pay attention that there are many fake-raid controllers (google for "fake raid") on the market, and the 4310 seems to be one of them.

A list of sata controller devices, and their level of functionality in linux, can be found at:

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

And other useful informations at:

[http://linas.org/linux/raid.html](http://linas.org/linux/raid.html)

Hope this helps!

---

### Post by fredrik_human on 2006-05-02
Thank you for the information, it helped a lot. I just thought that setting the disks up with hardware raid would be safer if the systems crashes and i had no idea there were "fake-raid" controllers?! 

//Fredrik

---

### Post by Kosh42 on 2006-05-09
From what I've read there are several ways to do this. I have a cheap fake RAID card that I nievely bought. Looks like I'll have to manually compile a kernel to get it working...

---

