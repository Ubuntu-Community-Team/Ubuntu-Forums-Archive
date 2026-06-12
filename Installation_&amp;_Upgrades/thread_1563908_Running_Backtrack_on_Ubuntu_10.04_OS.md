---
title: "Running Backtrack on Ubuntu 10.04 OS"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by DavidOfLondon on 2010-08-29
Hi guys,

My only OS is Ubuntu 10.04. There are no partitions ( that is, I use the entire hard drive for Ubuntu, obviously). I need to run Backtrack for security testing.

I've seen lots of various options from running it in virtualbox to running it from a bootable USB but there seem to be problems originating with the grub bootloader. One thing I keep seeing is that the only way to get round all this is to hard drive install Backtrack first and THEN install Ubuntu. Clearly I don't want to have to reinstall my entire world on my pc, play with settings, re-install a billion apps etc.

My question is this - Given that I have 10.04 installed and running alone, how do I get Backtrack installed/running easily and without all the associated disasters? 

Did you achieve this without problems? How did you do it? What do I need to do?

I like the USB option because the thought of screwing the grub up does not appeal; I don't want to reboot my computer and be told "Sorry - I'm grub and I don't want you to load anything" / Other Annoying Message.

Backtrack's site says they didn't provide a USB option so what should I use to burn the ISO (does Unetbootin work for Ubuntu??!?!?!

If you've done what I need to do I'd really appreciate your advice.

Thanks.

---

### Post by gordintoronto on 2010-08-29
"BackTrack &#8211; Penetration Testing Distribution" which means it does not run from within another Linux distro such as Ubuntu, it *is* a Linux distro.

Put Backtrack on a CD or USB stick. You can use Administration/Startup Disk Creator to make a USB stick, or Brasero to burn a "Live CD." image. Or Unetbootin for the USB stick. You can install unetbootin from Administration/Synaptic.

Then tell your BIOS to boot from the device. Grub is not involved in any way.

---

