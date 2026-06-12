---
title: "Dual UEFI boot on two drives with two ESRs  - any known issues?"
date: 2024-03-19
forum: Installation &amp; Upgrades
---

### Post by bsh on 2024-03-19
Hey guys,
I've been running BIOS/MBR mode for the longest of times, but now I switched to UEFI mode for Windows, so I'm going to reinstall xubuntu 22.04 on it's own disk, as it was before, and do dual booting via the UEFI boot disk select.
Are there any known issues with this? I've read that the Ubuntu installer is buggy and installs on the first UEFI partition it finds (this won't be the case as I'm going to turn off all other drives during the install, ony the Ubuntu drive is going to be present.) Any issues after e.g. upgrades and grub updates, or coming from Windows issues or something?

Also, when I do custom partitioning durign install, am I supposed to make the ESR partition myself or will the installer take care of it?

---

### Post by ubfan1 on 2024-03-19
The Ubiquity installer used on Ubuntu 22.04 has the launchpad bug 1396379,  grub put on wrong disk, but xubuntu uses another installer (Calamares?) I think.  Anyway, your turn off the other disks will solve that issue.  Ubiquity will make an EFI if one doesn't exist I think , subiquity (used in 23.10+) will definitely make  a 1GB efi even if one already exists (too big in my opinion). You decision is how you want to boot.  All bootloaders may be put onto the first disk's UEFI partition, so the second disk is not bootable.  You may put grub on the second disk's UEFI, and make it bootable (maybe on another system).  The standard installs will also add the shim/grub to the disk default location (,,,/EFI/Boot/bootx64.efi) so it may boot on another system.

---

### Post by oldfred on 2024-03-19
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

But this is probably easier for most:
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) & 

Most UEFI remove or change a UEFI entry when a drive is disconnected. But most also find Windows entrys but not Linux entries automatically.
Make sure you have both a Windows repair/recovery flash drive & Ubuntu live installer for current versions at all times.
And have good backups.

I prefer to gpt partition in advance so gpt with an ESP - efi system partition of the size I want. I use larger (500-600MB)for large drive, but 100MB for small flash drives with full installs. Then only use Something Else so I know which partition is then selected to be reformatted as /. I use ext4, but others can be used.

There now are 3 different installers. Older thru 22.04 desktop used Ubiquity with the very old bug on external or second drives.
Newer versions use Subiquity installer which does not have bug.
And Lubuntu and starting with 24.04 Kubuntu use Calamares.
My test install of Kubuntu 24.04 had a bug in a Calameres python script. But when edited, it installs & lets me choose my sdb ESP where my main 22.04 working install is on my first drive, nvme01.

---

### Post by MAFoElffen on 2024-03-19
> **bsh said:**
> 
I've been running BIOS/MBR mode for the longest of times, but now I switched to UEFI mode for Windows, so I'm going to reinstall xubuntu 22.04 on it's own disk, as it was before, and do dual booting via the UEFI boot disk select.

Are there any known issues with this? 

I've read that the Ubuntu installer is buggy and installs on the first UEFI partition it finds (this won't be the case as I'm going to turn off all other drives during the install, ony the Ubuntu drive is going to be present.) Any issues after e.g. upgrades and grub updates, or coming from Windows issues or something?

Also, when I do custom partitioning durign install, am I supposed to make the ESR partition myself or will the installer take care of it?
That is not really an installer Bug, but rather an accepted practice.

I do this (unplug or turn off non-participating drives)... That works, unless your system also follows the below noted accepted practice.

But be aware:
Some UEFI BIOS'es only recognize the first UEFI partition "IT SEE's".

I have an MSI motherboard, which it's UEFI BIOS only recognizes the first UEFI partition it see's. Since it has both SATA and NVMe, if the EFI is on both, then it will see the bus, that is in the boot order first. For instance, mine sees the NVMe bus, before anything on the SATA bus. So if there is already an EFI partition on that, but, it will never see anything on the SATA bus.

Just a note. As oldfred mentioned, mine also changes the UEFI location entries in the BIOS, if you start disabling or unplugging drives.

---

### Post by yancek on 2024-03-19
It should work and will on most systems which don't install to the first EFI partition.  Since you plan to disconnect the windows drive that should eliminate the problem.  When you want to boot Xubuntu you will obviously have to select that drive in the BIOS to boot it and select the windows drive in the BIOS when you want to boot it.  You could set the Xubuntu drive to first boot and boot windows from Grub on that drive.

---

### Post by bsh on 2024-03-20
> **oldfred said:**
> 
But this is probably easier for most:
Remove esp flag from Windows before install to second or external drive - Tim Richardson


...and the most easiestest is if you have [this]("https://img.aucfree.com/e367169476.1.jpg"). :)

---

### Post by bsh on 2024-03-20
Ok guys thanks. I'm not sure now... Been running MB like this forever without any problems, but now I'm not sure. Mostly worried about future updates that may want to update grub or something on the efi partition (like a recent windows 10 update did) messing things ups when both drives are on (normally they are) and there would be two efi partitions...
One thing is sure, I don't like uefi and don't see any of its advantages. And it's apparently still not mature enough after that many years. Why has this been forced on us, dunno.

---

### Post by guiverc on 2024-03-20
I'll provide some details/opinions, but it maybe little extra

- all Xubuntu releases up to 23.10 have used the `ubiquity` installer; it's been replaced by `ubuntu-desktop-installer` for Xubuntu *noble*.

- `calamares` has been used by Lubuntu since 18.10, and has also been used for some releases of Ubuntu Studio, but no other flavors (as OldFred suggested, Kubuntu and Ubuntu Unity will use `calamares` for *noble* & later, but they're not released products yet)

- bugs have been mentioned with regards the bootloader, I'll suggest you follow the documentation on ISO writes to your install media; as many ISO writing apps allow you to select options which *reformat* the ISO which can trigger install bugs with the bootloader write (*meaning bootloader gets written to wrong device, esp. installation media*).  I suggest using a simple *clone* or unaltered write of ISO to media as that's what's QA tested.

- `ubiquity` will create an ESP if required automatically for some options, however if you use *Something else* where you control the partitioning you'll need to do it yourself.

---

