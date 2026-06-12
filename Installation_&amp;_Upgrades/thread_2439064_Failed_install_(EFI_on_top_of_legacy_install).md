---
title: "Failed install (EFI on top of legacy install)"
date: 2020-03-22
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2020-03-22
I just replaced a failed HD with a new Western Digital HD in a System76 Lemur laptop. I'm installing using a flash drive with MultiSystem to boot the Ubuntu ISO install. 
(EFI on top of legacy install) choosing "replace" or "resize" options in partitioning may lead to an install failure
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1766945](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1766945)

I get the error message
Grub Installation Failed
The 'grub-efi-amd64-signed' package failed to install into / target/. Without the GRUB boot loader, the installed system will not boot.

How do I fix this?

I got the same error using an Ubuntu 18 iso and an Ubuntu 16 iso.

---

### Post by oldfred on 2020-03-22
You cannot mix BIOS & UEFI boot on same drive.
And best to only have one or the other & with newer UEFI hardware best to just use UEFI with gpt partitioning.

If you partition in advance, use gpt and you must have an ESP - efi system partition for grub's UEFI version to correctly install.

See link in my signature below.
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by dragonfly41 on 2020-03-22
> [COLOR=#000000]You cannot mix BIOS & UEFI boot on same drive.[/COLOR]

@oldfred
[This thread which I have bookmarked]("https://forums.linuxmint.com/viewtopic.php?t=287353") claims that you *can* have a hybrid BIOS/UEFI system but I have never dared try this option,

The thread was the one which pointed me to use rEFInd (which only works in UEFI).

---

### Post by oldfred on 2020-03-22
On a gpt drive you can create both BIOS/CSM & UEFI boot. But often with a full install grub gets out of sync.
It can be used with the live installer as that is configured for both, so one ISO can be used to boot & install in either mode. But it is not updateable. 

You also can have one drive as UEFI and another drive as BIOS boot. But may have to change settings in UEFI to allow boot. Most now seem to know which entry in UEFI is BIOS or UEFI and will let you boot without changing UEFI settings. You probably have to have UEFI or BIOS setting in UEFI on. You cannot have UEFI Secure Boot on to boot in CSM mode.

Ubuntu will let you install in UEFI mode to an old MBR drive, but really should not.
Windows requires MBR for BIOS boot and requires gpt for UEFI boot.

What is it you are trying to do?

---

