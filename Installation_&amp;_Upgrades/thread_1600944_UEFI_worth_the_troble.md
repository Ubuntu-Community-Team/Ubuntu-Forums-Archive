---
title: "UEFI worth the troble?"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by mos4567 on 2010-10-19
Hi! :)

I am getting ready to move a desktop from 10.04 to 10.10.  The motherboard is an intel DP55KG. Currently, the system has a problem I have yet to find a solution to, if halted it will turn off fine but if rebooted it will hang forever after requesting a system restart. 

The board supports "EFI boot" as an option you can toggle. I have it off because I could not even get the install CD to boot when I installed 10.04 but with it off everything works except for that rather annoying reboot problem, it only really become bothersome after installing an update that requires a reboot because it is easy to just forget and click reboot. 

Now then I am going to be installing 10.10, it seems time to give the problem a fresh crack. I have wondered if the problem might go away if I was using the UEFI, but before I spent some time attempting to figure out how to boot the install CD when UEFI is on  and then install correctly, I wanted to see if people felt I was barking up the wrong tree in my attempts to alleviate this problem. 

I have done some googling on installing with UEFI and I have found a lot of information regarding the EFI Apple Macs use,  but it also seems that UEFI, an Intel technology, is little different animal.  Should I follow steps along the lines of the ones for the Mac EFI or is someone aware of a UEFI specific resource / has personal experience with UEFI?  

Thanks for your help!

---

### Post by srs5694 on 2010-10-19
Apple Macs use a slight variant on EFI 1.x, but most x86 systems with EFI use UEFI 2.x, which is a more recent version of the same thing. (Apparently Apple's EFI has a few Apple-specific tweaks, too.)

I don't know whether switching to UEFI would help your rebooting problem or not. If you do switch, you'll be a bit of a trail-blazer, so I'd only recommend it if you're willing to spend some time experimenting. The biggest problems are likely to relate to partitioning and boot loader configuration.

EFI (including UEFI) introduces a new partitioning system, known as the GUID Partition Table (GPT). UEFI doesn't *require* GPT, so in theory you should be able to continue to use the older Master Boot Record (MBR) system you're probably using now; however, UEFI *does* require (or at least strongly recommend; I don't recall which) a special partition known as an EFI System Partition (ESP), which is about 100-200 MiB in size with a FAT32 filesystem on it. Thus, if you want to preserve your existing partitions, you may need to trim one of them a bit to make room for an ESP. Give it a type code of 0xEF if you keep using MBR. If you decide to go whole-hog and switch to GPT, you can do it non-destructively with my [GPT fdisk](http://www.rodsbooks.com/gdisk/) utility. You can boot BIOS-based systems from GPT, so if you try EFI and then decide you don't like it you should be able to switch back to BIOS; however, some Intel BIOSes have [known problems that require workarounds](http://www.rodsbooks.com/gdisk/bios.html) to boot from GPT disks. Note that if you dual-boot with Windows, it requires GPT to boot from EFI. Switching from one to the other under Windows is likely to be tricky, but see [this forum post](http://www.insanelymac.com/forum/index.php?showtopic=186440%20.) for information on making such a transition.

In terms of booting, GRUB 2 supports EFI, but this support seems to be a bit new. Most Mac users seem to be using something called rEFIt, but I'm not sure if that's Mac-specific or if it works with UEFI-based PCs. The older ELILO is also an option. I'm afraid I don't know much about the specifics of these boot loaders, since I don't (yet) have an EFI-based system. (I've got a used Intel-based Mac Mini on the way, though.)

---

