---
title: "How to on AMD firmware RAID 10"
date: 2015-12-13
forum: Installation &amp; Upgrades
---

### Post by xen3 on 2015-12-13
I am trying to discover how to run e.g. Ubuntu on an AMD "motherboard" RAID solution, so that I can use it both in Windows and in Linux.

Last time I tried:

- Kubuntu installer did not even see the RAID, nor was I able to install on it (*I may just need to do "dmraid -ay" from a shell*).
- OpenSUSE installer did see it and allowed me to install on it, BUT it wouldn't boot, as apparently (perhaps) this same command *???* was not getting executed by the initrd.

From some Gentoo wiki page I surmised that at least the boot partition has to be the first partition, but this was old information and may not hold for Grub2.

The Chipset I am using is SB710 which is in principle supported by Linux kernel because I can see and use them (it, the array) from an OpenSUSE installer session.

I have also achieved SOME success in activating the array in a Kubuntu live session.

But attempting this *may* require me to reinstall Windows and repartition, but I also hate Grub to the bones and I run into issues with a TrueCrypt boot loader, later on. It may be possible in Grub2 to save the functioning TrueCrypt loader to a .bin file and load it from Grub2, but I don't know how and it is one hell of a moron software.

Grub is ugly anyway unless you know how to theme it.

And usually I have better stuff to do than that.................

I prefer not to have a dedicated Linux install but this thread is about how to do it. I would likely just create and use a second array if I did attempt it but this is suboptimal and not what I want. And not what I need.

However, any temporary solution may suffice. I just need to be able to work in Linux for a few days.

I guess my best bet for my needs is to try VMWare, but.

Apart from that.

***What are the requirements to get Ubuntu running on an AMD bios RAID?***

---

### Post by xen3 on 2015-12-13
Pretty much the same question was asked here:

[ubuntuforums.org/showthread.php?t=2296102]("http://ubuntuforums.org/showthread.php?t=2296102")

But received no answer. One thing to note is that on my motherboard driver DVD, there is at least *mention* of a Linux software package called (as for Windows) RaidXpert but it's not actually on the disc.

---

