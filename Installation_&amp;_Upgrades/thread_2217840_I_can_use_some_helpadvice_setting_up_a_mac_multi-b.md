---
title: "I can use some help/advice setting up a mac multi-boot setup"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by lrflew on 2014-04-18
With the release of 14.04, I want to convert my dual-boot setup to a triple-boot setup. I plan on reinstalling/upgrading windows, so I'm going to be starting from scratch on my partitioning, and will just use Disk Utility to create the partitions for each OS manually. My computer (for reference), is a MacbookPro11,3. I'm not so much looking for specific advice on setting up things like drivers and HiDPI correctly, although advice on this would still be welcome. I have looked at enough guides to feel like I understand what I'm doing, and I've setup an Ubuntu virtual machine already on 14.04, but I had a few questions on how best to setup the partitions and boot setup.

Many guides (such as [this one]("http://lifehacker.com/5531037/how-to-triple-boot-your-mac-with-windows-and-linux-no-boot-camp-required")) warn about setting up the boot loader. Macs have a built in (U)EFI loader, and trying to let another OS take it over can cause serious issues. The guide I linked was for an older version of the installer that had the option of not installing a boot loader, but that doesn't seem to be the case anymore. When installing, it gives the option for "Device for boot loader installation". For this type of setup (where the boot loader needs to be segregated), is it ok to select the Ubuntu installation partition for the boot loader installation, and let the computer's EFI find it when I want to boot to linux?

My other question has to do with the swap partition. Since I'll be doing a custom install, I'll have to decide how big to make the swap partition. I understand that the partition is necessary for when the OS runs out of RAM, but I just don't know how much I would need. I don't plan on using Ubuntu heavily (mostly for a mix of testing it out and for developing cross-platform applications). How much should I dedicate for a swap when I have 16GB of RAM? Do I even need one? On a related note, any advice on how much HD space I should allocate for Ubuntu? Since the OS is so small, I'm thinking 40-60GB (combined OS and swap partitions) should be enough for what I'll be doing.

---

