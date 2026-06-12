---
title: "UEFI Boot Windows 8 &amp; Ubuntu"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by skwalas on 2013-01-12
Hi, recent linux virgin, wanted to jump into this thread as I'm interested in outcomes too.  I suspect there's something about the way the new Win8 bootmanager is implemented that's not helping. Here's my experience:

No issues whatsoever booting live cd with secureboot and fastboot enabled (even made a VM with it using Hyper-V). Figured this meant i would be one of the lucky ones without s-boot or f-boot issues.

First install attempt:  resized existing win8 partitions, used live cd to install ("do something else"), created a second efi partition (sda6) and made it bootloader target, /, and /home. Install completed fine with some some weird scripting during the restart.  Result:  Grub2 booted ubuntu fine, windows boot manager booted win8 fine, but neither could boot the other ("missing files" for windows boot manager trying to boot ubuntu, and missing uefi issues for grub2).  I had to use F12 to get the UEFI boot menu to go back and forth.  This tells me the second EFI partition at least did not blow anything up.  And no, i did not use boot-repair here.

Second install attempt:  Deleted all of the previous linux partitions, repeated install but *did not make second efi partition*.  selected the existing efi partition (sda2) for bootloader target.  Installed fine, no weird script during restart this time.  Results were same as before:  i have to use the UEFI boot menu to switch back and forth.  Also tried boot-repair with no success.  Instead of missing uefi, i now have secureboot problems when using grub2 to boot win8.  Shutting off secure boot and fastboot doesn't help.  I also changed order of boot, still same boot behavior.

I decided to play with the windows boot manager.  That thing is completely inconsistent.  but here was the weird thing:  when i had ubuntu as first boot priority but selected windows manager through UEFI, then i selected windows 8 in the windows boot manager, it would send me to grub2 instead of booting windows.  selecting ubuntu still gave missing file error.  changing order so windows boot manager was first boot priority restored expected behavior (what i was experiencing before).  Almost like the boot manager thinks "windows 8" means whatever is the first bootable OS in the priority list.

anyway, I'm thinking of deleting the install and trying over again.  Any suggestions by anyone on what to try next?

---

### Post by skwalas on 2013-01-12
Quick update before bed.  For kicks, instead of re-installing, I just disabled both fastboot and secureboot through UEFI settings, manually booted back into ubuntu, and THEN ran disk-repair. This time it seemed to work!  Grub2 now boots ubuntu and windows 8, alhtough it still goes through a windows-7-style boot menu going into windows 8 boot.  I do see four different windows .efi boot choices and a dead primary loader link in grub2... (these seem to be generic boot menu and Lenovo-branded diagnostic boot items)

On the other hand, the windows 8 bootmanager does not see ubuntu at all now.  if grub2 genuinely is in the .efi partition, shouldn't the windows bcdedit tool be able to see it?

the pastubuntu # is 1522686.  i don't recall the full url, sorry!

---

### Post by oldfred on 2013-01-12
Moved to your own thread as your issues are different.

Paste bin is not correct, I go a list of web sites?

You can re-run just to BootInfo report.

Never create a second efi partition. There can only be one and all systems load their efi boot files into that one partition. Boot-Repair may find both and we have seen where Vendor recovery partitions have boot files, so you may be able to chain load to an efi file not in the efi partition. But UEFI will only find boot files in the efi partition.

---

### Post by skwalas on 2013-01-12
> **oldfred said:**
> Moved to your own thread as your issues are different.

Paste bin is not correct, I go a list of web sites?  

You can re-run just to BootInfo report.

Never create a second efi partition. There can only be one and all systems load their efi boot files into that one partition. Boot-Repair may find both and we have seen where Vendor recovery partitions have boot files, so you may be able to chain load to an efi file not in the efi partition. But UEFI will only find boot files in the efi partition.

Not sure how it's different, as I also want to be able to use windows  bootmanager like the OP, but perhaps you're seeing something else in my  setup?  in any case, I always appreciate any help!

new bootinfo report URL:  [http://paste.ubuntu.com/1525102/](http://paste.ubuntu.com/1525102/)

And yes, I figured out I shouldn't have two EFI partitions.  that was a main reason why I deleted all the partitions from the first install attempt rather than just reformatting.  I also repaired the primary EFI through the OEM recovery before starting the second install.

In any case, curious what you see that's useful in the bootinfo.  I'd really like to keep secure-boot as an option (fast-boot i can do without), and would ultimately like to use the windows boot manager, since for the time being i'll be working with windows 8 about 90% of the time as I transition to linux use.  But it's a real mystery why windows bcd tool doesn't see ubuntu if it's in the EFI.

Cheers!

---

### Post by oldfred on 2013-01-12
System looks ok.

Boot-Repair added correct chain load entries.
Does this boot Windows:

> Windows UEFI bootmgfw.efi
The entries that grub2's os-prober finds are incorrect.
Or anything that refers to partition like this:
> Windows 8 (loader) (on /dev/sda4)

Windows is not designed to multi-boot. BCD will not show grub.
But grub will show Windows. And UEFI will show both. If mostly booting 
Windows you can just set it in UEFI. And go back to UEFI when you 
want Ubuntu. Otherwise just boot from grub menu.

---

### Post by skwalas on 2013-01-13
> **oldfred said:**
> System looks ok.

Boot-Repair added correct chain load entries.
Does this boot Windows:


The entries that grub2's os-prober finds are incorrect.
Or anything that refers to partition like this:


Windows is not designed to multi-boot. BCD will not show grub.
But grub will show Windows. And UEFI will show both. If mostly booting 
Windows you can just set it in UEFI. And go back to UEFI when you 
want Ubuntu. Otherwise just boot from grub menu.

All three of the bootmgfw.efi entries boots windows after redirecting to the win7-style boot manager.  And yes, the "Windows 8 (loader)" entry does not do anything.

I guess i will be restricted to using the UEFI boot menu to select ubuntu in those rare occasions  for the time being.  I may move more to using grub2 sooner than planned, if I can get comfortable with linux fast enough though.  

Are there any plans for ubuntu to eventually be compatible with secure boot?  As stated before, fast-boot does nothing for me as all of my drives are SSD, but secure boot seems like it might actually serve a purpose.

Thanks for the help!

---

### Post by oldfred on 2013-01-13
Ubuntu 12.10 with grub2 2.00 uses the Windows secure boot key and is supposed to work. But some UEFI only boot Windows.

See this thread post #5
[http://ubuntuforums.org/showthread.php?t=2104518](http://ubuntuforums.org/showthread.php?t=2104518)

But some UEFI only boot based on file name which is a UEFI bug by the vendor.
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

