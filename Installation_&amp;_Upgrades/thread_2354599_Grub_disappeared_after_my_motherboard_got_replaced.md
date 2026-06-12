---
title: "Grub disappeared after my motherboard got replaced"
date: 2017-03-04
forum: Installation &amp; Upgrades
---

### Post by saurabhorange on 2017-03-04
Hi , was using ubuntu 16 64 bit  before I got my motherboard replaced ( of my dell inspiron 5559 ) , It now defaults to windows , I tried disabling secure boot still no success , I inserted live ubuntu pen drive and entered a terminal to install bootrepair , Even that showed an error , here is the error log [http://paste2.org/dhM0pjAH](http://paste2.org/dhM0pjAH)
Can anyone help me in getting my ubuntu and grub back ?

Thanks
Saurabh

---

### Post by Bucky Ball on 2017-03-04
Depends whether you have a UEFI or legacy install, but just after boot, start hitting shift (or escape!). That should bring up the grub menu list of OSs and kernels.

Don't go fiddling around with anything before you try this as you may cause damage! :)

From the looks of your bootinfo, there seems to be a problem, though. See if you can get to that list, boot Ubuntu and see what it happens and report back. Does Windows boot and function fine?

---

### Post by oldfred on 2017-03-04
It looks like Boot-Repair's reinstall of grub added the ubuntu entry to UEFI boot menu.
Does f12 show ubuntu and does it now work?

Errors seem to be related to sdb, your flash drive. Not sure what it is finding?

Normally disconnecting a drive will cause the UEFI to forget the boot entries it stores in NVRAM.
Most UEFI find entries in ESP - efi system partition, but many seem to only look for Windows or fallback/hard drive entry.

---

### Post by saurabhorange on 2017-03-05
Hi , Thanks for your replies , I can confirm after reinstalling grub via boot repair and restarting , I got my grub back and ubuntu is working fine , I am posting this reply from my ubuntu and I am very happy :)

---

### Post by Bucky Ball on 2017-03-05
Excellent news and well done. ;)

Please help others by marking as solved (Thread Tools at top right of page or see link in my signature for how).

---

