---
title: "How do I install the bootloader of Ubuntu 18.04.4 in a external SSD?"
date: 2021-03-06
forum: Installation &amp; Upgrades
---

### Post by goahead97 on 2021-03-06
Hello

I recently installed Ubuntu 18.04 in a 1TB external SSD. I thought I had selected the option to install the bootloader in the same external SSD but it turns outo the installation had changed the bootloader of the computer internal's SSD by adding an entry for Ubuntu. The operating system of the internal SSD is Windows 10 and its Bios is UEFI in case that matters. Getting the bootloader of the internal SSD updated is not something I like. If I want to boot by default with the Ubuntu of the external SSD, then whenever I unplug the external SSD the computer will not boot with the Windows operating system of the internal SSD unless I update the order of boot devices in the UEFI bios.

Anyway, after that I formatted the external SSD and then I removed the Ubuntu option of the bootloader of the internal SSD to leave only Windows as single available option for booting.

After that I installed Ubuntu 18.04.4 in the same external SSD. This time I paid much attention to the choice of location for Ubuntu's bootloader installation because I wanted to make completely sure I selected the external SSD. However, to my surprise I found the bootloader of the computer internal's SSD had been updated once again, this time by adding a new entry for Ubuntu 18.04.4.

Therefore, I wonder, what am I doing wrong? How should I have proceeded in order to install not only Ubuntu 18.04.4 but also its bootloader in the external SSD?

I have been able to install 64 bits LXLE Ubuntu 18.04.3 ([https://sourceforge.net/projects/lxle/files/Final/OS/18.04.3-64/lxle-18043-64.iso/download](https://sourceforge.net/projects/lxle/files/Final/OS/18.04.3-64/lxle-18043-64.iso/download)) in a 250 GB external SSD in the past. Why am I having problems now to install the bootloader of Ubuntu 18.04.4 ([http://old-releases.ubuntu.com/releases/18.04.4/ubuntu-18.04.4-desktop-amd64.iso](http://old-releases.ubuntu.com/releases/18.04.4/ubuntu-18.04.4-desktop-amd64.iso)) in the 1TB external SSD?

Thanks

---

### Post by tea for one on 2021-03-06
You are not really doing anything wrong.
The Ubuntu installer will use the first EFI partition and does not follow user instructions to install grub anywhere else.

It is a known and irritating bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

I would isolate, disable or physically remove your Windows internal disk and then the Ubuntu installer will put grub on your external device as required.

---

### Post by ajgreeny on 2021-03-06
You have done nothing wrong; that is simply the way a UEFI system works.

No matter what you request during the installation, the bootloader will always go onto what is seen by the system as the first disk, ie, the internal hard disk.

You may have to temporarily disable the internal disk in the UEFI settings whilst installing and once done re-enable the disk.
However, I may be out of date on this as I've never done it on a new, non-BIOS computer so wait for more answers before rushing in a third time.

EDIT:
Just read that bug which seems to show the best way out is to use gparted in the live install medium to remove the EFI/ESP flag from your current hard disks efi partition but otherwise leave it alone. Then add another EFI partition to the external disk with the necessary flags and install the OS.

Good luck!

---

### Post by CelticWarrior on 2021-03-06
Yes, it's an oddity (some call it a "bug", others a "feature") that Ubuntu always installs the EFI bootloader in the internal or main drive's ESP regardless of the user selection during the installation process.

[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")'s advanced mode can be used to install Grub to another drives.

That said, the way it is actually makes more sense. Unless you want portability (sort of) there's no need to have the bootloader in the external drive. If you intend to boot Ubuntu in the external drive only occasionally then what makes sense is to set UEFI's boot order to the original OS (Windows) and use the on-time boot menu to select Ubuntu whenever the external drive is plugged-in. With UEFI bootloaders co-exist peacefully in the ESP and the internal drive ESP can contain many bootloaders. The additional bootloaders do not change the Windows bootloader manager in any way and Windows can be booted directly like it was the sole OS regardless of how many more bootloaders are there.

Again, having a different ESP in the external drive makes sense only when you want to use that drive in a different UEFI machine by changing its drive order priority to force reading the external drive's ESP instead of the internal one. For using it always in the same machine having Ubuntu (Grub) in the internal drive's ESP or in the external drive's ESP is irrelevant because either way you'd have to change the boot order whenever you want to boot Ubuntu and potentially have to change two settings instead of one in that scenario. And if the external drive is always or almost always connected then what makes sense is to change the UEFI's boot order to Ubuntu and select Windows bootloader manager from the Grub menu whenever desired. In this situation - always connected - having Ubuntu installed in an external drive, in a different or the same internal drive shouldn't make any difference whatsoever.

---

### Post by tea for one on 2021-03-06
As a matter of interest, the Ubuntu installer is being re-written:-

[https://www.omgubuntu.co.uk/2021/02/ubuntu-is-working-on-a-brand-new-installer](https://www.omgubuntu.co.uk/2021/02/ubuntu-is-working-on-a-brand-new-installer)

---

