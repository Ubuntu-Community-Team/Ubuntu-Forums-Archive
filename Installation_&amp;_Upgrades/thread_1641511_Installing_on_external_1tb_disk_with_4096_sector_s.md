---
title: "Installing on external 1tb disk with 4096 sector size"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by abosetti on 2010-12-09
Hello everyone

In the past I have been able to succesfully install ubuntu on several external usb drives with up to 500gb in size.

Now I am trying to install a copy of ubuntu 10.10 on an external usb iomega 1tb eGo drive but I am having major issues.

The installer reports the total disk size as only 124 gb, instead of the 998gb that gParted reports for the same disk. Proceeding with "use the full disk" installs ok, but it doesn't boot. Grub2 reports that it cannot find the kernel.

After some desperate attempts to repartition and after some googling I think that the issue may be with the sector size, which fdisk -l reports as 4096kb (all my other drivers report 512kb) and I have the impression that linux is not ready for it (or I lack the knowledge, which seems more likely).

I have also tried to install fedora 14. This distribution reports the correct disk size, installs properly, but again, it cannot boot (Fedora uses grub, not grub2), with a very similar message to the grub2 installer.

Because of the way I work, I need my external usb drive to be able to boot linux. And I find it difficult to believe that linux doesn't handle 4096kb sector disks, so here I am asking for help :-). Please note I am not a linux expert.

Can anybody give me some hints on what to do?

Thank you a million in advance

Alessandro

---

### Post by albertmatyi on 2011-03-20
Hey, I am facing the same problem, and after a lot of strugling I've come to the conclusion that unfortunately you can not make your HDD bootable.

It is because it is a native 4k drive and the bios is not able to use it, because the bios only supports 512b drives - or 4k drives that can emulate 512b sectors.

This is also the reason why there is no support added for 4k drives in grub either (AFAIK)

I have this problem with a Transcend StoreJet 18m.

Sources:
[http://lwn.net/Articles/377895/](http://lwn.net/Articles/377895/)
[http://lwn.net/Articles/377900/](http://lwn.net/Articles/377900/)
[http://us.generation-nt.com/answer/bug-602071-usr-sbin-grub-probe-error-cannot-find-grub-drive-dev-sda1-check-your-device-map-help-200890251.html#r](http://us.generation-nt.com/answer/bug-602071-usr-sbin-grub-probe-error-cannot-find-grub-drive-dev-sda1-check-your-device-map-help-200890251.html#r)

Oh, but if you managed somehow to make it work, please tell me what you did:)

---

### Post by Savio2010 on 2011-03-20
I am planning to upgrade my internal hdd to 1 TB when 11.04 is released.

I don't have any idea what is creating a problem?:o
Is it the size of the HDD? or The HDD being internal or external.

I am in a doubt, should I upgrade or no?

Do post updated news here as an when possible.

---

### Post by srs5694 on 2011-03-20
First, a minor (but 1024-fold!) correction: The sector sizes in question are 512 bytes and 4096 bytes, not 512 "kb" and 4096 "kb".

As to the question, I suspect that albertmatyi is correct, although it's also possible there's some dependency on 512-byte sectors in GRUB Legacy and GRUB 2. This is one of the reasons that Western Digital, and now Seagate and I believe at least one other manufacturer, are using "Advanced Format" technology, in which disks with 4096-byte sectors pretend to have 512-byte sectors. Without this fiction, many BIOSes would be unable to boot from these drives.

One possible workaround would be to set up a separate /boot partition on an internal disk or even a USB flash drive with 512-byte sectors. This partition can be pretty small; on my systems, /boot holds between 40 MiB and 60 MiB worth of files. I recommend making /boot at least 100 MiB, and preferably 200 MiB, so that you'll have enough room to install a few kernels. (That, and the GRUB files, are the main contents of /boot.) In theory, once the kernel has loaded from /boot, it will take over and any BIOS or boot loader limitations should become irrelevant.

---

