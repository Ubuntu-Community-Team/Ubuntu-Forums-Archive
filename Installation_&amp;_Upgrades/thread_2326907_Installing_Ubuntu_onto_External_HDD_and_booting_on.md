---
title: "Installing Ubuntu onto External HDD and booting onto Razer Stealth"
date: 2016-06-06
forum: Installation &amp; Upgrades
---

### Post by jacob106 on 2016-06-06
Hi guys,

So I used to have an alienware m14x r2, which I loaded ubuntu 15.10 from using an external hard drive. However I recently bought the new Razer Blade Stealth, which does not recognize the external hard drive in the boot menu. The drive is still working as I can boot it using different machines (old alienware, desktop, other laptops). After calling tech support and having it checked out by my IT department, the conclusion is that the Razer blade stealth does not support Legacy boot (which the drive uses) and therefore does not recognize it. (Note: the drive is formatted that it has two partitions: one is used for ubuntu, the other is used for regular storage, and the Razer stealth does pick up the storage partition). If this is incorrect, you can ignore the rest of the post and maybe propose an alternate solution.

The proposed solution was to try and install ubuntu in a way that the drive uses UEFI boot, but I couldn't find a straight forward article. The method I used to install ubuntu originally does not have the option for using uefi or legacy so I cannot redo that. I am also not going to make my razer stealth an ubuntu only laptop or dual bootable because there is not much space (I went with the 128gb ssd). Let me know if there are any good solutions to this problem, thanks.

---

### Post by oldfred on 2016-06-06
Are you wanting to try to convert existing install to UEFI, or are willing to start from scratch.

Drive will need to be gpt partitioned. That erased drive, but gdisk or sgdisk can convert a drive. Either way really good backups are required.

Ubuntu's grub does not make it easy to install to a second drive. I have several installs on second internal drives and external flash drives.
You have to partition in advance to be sure to have ESP on second drive. I typically include a bios_grub also just in case later I want to experiment with BIOS boot. I then add a 25GB / and use rest of flash drive as data partition.

But even if during Something Else you tell grub to install to sdb. And grub will say installing to sdb, it overwrites or installs to sda.

You then copy /EFI/ubuntu twice, once to /EFI/ubuntu on sdb's ESP and again to sdb into /EFI/Boot. In /EFI/boot you rename shimx64.efi to bootx64.efi.
UEFI only boots external drives in UEFI mode from /EFI/Boot/bootx64.efi. Both Ubuntu & Windows installers use that file name, even though different files. So that file has to exist on an external. 

When we copy the grub or shim from a full install on sda, that version of grub is hard coded to find files in /EFI/ubuntu, so you must have both /EFI/ubuntu and /EFI/Boot/bootx64.efi.

---

### Post by jacob106 on 2016-06-06
Hi, thanks for your reply,

I ended up going through BIOS and after turning off secure boot, it enabled me to turn on CSM (compatibility mode) which then opened a new menu to enable legacy boot. So I don't think I need to go on into this further. We spent hours on friday trying to figure this out, not sure how we missed this as I found it by accident just now (wasn't convinced a the laptop didn't allow for legacy boot.)

However I have two new problems, touchpad and wifi isnt working on the Ubuntu (works on windows) but this is a different problem in which I am currently looking for the solution.

---

