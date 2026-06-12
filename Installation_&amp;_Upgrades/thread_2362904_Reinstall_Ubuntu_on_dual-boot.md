---
title: "Reinstall Ubuntu on dual-boot"
date: 2017-06-03
forum: Installation &amp; Upgrades
---

### Post by navarrano on 2017-06-03
Hello,

I'm trying to reinstall Ubuntu on my laptop with dual-boot and during installation process, when selecting "Reinstall Ubuntu" I'm getting the following message:
> The partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked for use as an "EFI boot partition" and should be at least 35 MB in size. Note that this is not the same as a partition mounted on /boot.
If you do not go back to the partitioning menu and correct this error, boot loader installation may fail later, although it may still be possible to install the boot loader to a partition

I don't understand why do I get this message, because I have an EFI partition:
[IMG]http://storage5.static.itmages.com/i/17/0603/h_1496484354_6884226_017f953978.png[/IMG]

During my previous installation, when I created dual-boot for the first time, I didn't have any problems with the boot loader. Not sure if I even had to use boot-repair after. 
I've created mu bootable USB using portable Rufus and GPT partition scheme for UEFI.

What should I do with the message? Will choosing a /dev/sda2 in partition screen work or can I expect some problems afterwards? 

Thank you for your help!

---

