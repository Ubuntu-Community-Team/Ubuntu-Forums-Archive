---
title: "Info please about acpi handling with 2.6.22-14.51 onwards"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by Handssolow on 2008-06-05
What's been happening to acpi handling with recent kernels? Here on 5th February 2008 my Gutsy kernel upgrade from 2.6.22-14.47 to 2.6.22-14.51 left my 32 bit system unbootable, landing me with the ever popular Busybox and intramfs lines. To get it to boot I had to select an earlier kernel in menu.lst for several weeks whilst I awaited for HHeron to come along and hopefully cure this problem.

When HHeron did arrive the new kernel wasn't any better, my 32 bit OS didn't boot. However, I read on the Forum about there being an issue with acpi handling and by adding pci=noacpi I could boot. This has also been a required extra with every subsequent kernel update. Whilst I may have solved my boot problem, now I have to manually turn off the power switch at shutdown.

In contrast to my 32 bit Hardy Heron, my 64 bit on a Sata works faultlessly without any additional pci=noacpi to my kernel line. Initially I reported this a Launchpad bug #224268 assuming that this was likely to be a hardware problem but considering that 64 bit works, there must be another explanation.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224268](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224268)

Looking in the Forum, laptops seem to be mostly affected by these acpi related issues. Frequently I see solutions being offered to members who after an upgrade aren't able to boot but need to disable acpi in one way or another. Ive seen no explanation why previous kernels worked but not the more recent ones.

What happened to acpi handling from kernel 2.6.22-14.51 onwards?

---

### Post by Handssolow on 2008-09-25
A new bit of info here for what its worth. I've just discovered that a live i386 Heron CD powers down my PC whilst booting from my 32 bit Generic Heron installed on my hard drive doesn't. My 64 bit Heron on a Sata powers down normally.

I've just bought a Acer netbook with its XP OS - because the TomTom satnav update system doesn't support Linux. (Any TomTom workers reading this? Grrrrr. Why then no TTHome Linux help when your satnav system runs under Linux??).

Initially I'm working on getting Ubuntu working from a USB stick on my new Acer Inspire One before probably moving on to an SSD solution.

If anyone can shed any light why my Desktop's IDE 32 bit Heron doesn't power down whilst my 64 bit Sata and a Live i386 Heron CD does, I would appreciate any comments.

---

### Post by Handssolow on 2008-10-27
Just to add that since I recently corrupted my hd with it's 32 bit Ubuntu OS and instead installed 8.10 Beta Intrepid (2.6.27-7-generic kernel) it needs no addition to the kernel line to modify acpi functionality in menu.lst to get this OS to boot. Probably also as a consequence, my PC now powers off automatically as it used to do prior to 5th February 2008.

I'm uncertain about flagging this as "SOLVED". My system now works but I don't know why. I suspect that acpi function has been changed with the latest kernel which I'm using.

---

