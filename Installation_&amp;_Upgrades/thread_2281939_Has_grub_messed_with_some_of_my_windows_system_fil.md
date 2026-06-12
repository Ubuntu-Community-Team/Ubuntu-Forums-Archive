---
title: "Has grub messed with some of my windows system files?"
date: 2015-06-10
forum: Installation &amp; Upgrades
---

### Post by Hodor on 2015-06-10
Is it possible that GRUB has messed some of my windows system files?
Backrgound:
- I have windows 8.1 64 installed on one SSD and Ubuntu 14.04.2 64 (almost) independently installed on another SSD (until recently, I booted independently into either by altering settings in uefi  - but recently, when I select options to boot into ubuntu, GRUB loads and it now sees the windows boot manager - this  is new, I installed ubuntu with the windows disk removed and initially it booted straight into ubuntu without going through a grub boot options menu);
- I run SFC / scannow in windows and get a lot of errors like this: '[DIRSD OWNER WARNING] Directory [ml:520{260},l:88{44}]"\??\C:\Windows\Help\Windows\IndexStore\en-US" is not owned but specifies SDDL in component ...';
- I can maybe live with the corrupted windows system files for a while, but to make sure the system is stable they should be fixed - problem is, if GRUB did this, not sure how to stop a repeat.
- GRUB is of course a thing of beauty and I don't want to falsely accuse it of meddling with windows, but before I go through the hassle of a clean re-install I would like to know if I'm heading for deja vu.

Thanks very much for any help.

---

### Post by oldfred on 2015-06-10
Grub automatically adds Windows to grub menu whenever grub-update occurs. That could have been a new kernel or new update to grub.

That should not have changed anything with Windows, just add a Windows entry to grub.

But grub will not boot Windows if the NTFS partition is hibernated and Windows 8 is always hibernated with its fast startup setting. You must turn that off, if you want to use grub menu to dual boot. You should be able to dual boot directly from UEFI boot tab, or one time boot key if both Windows & Ubuntu are booting in UEFI mode.

You may have had an efi partition on your Ubuntu drive, not sure if update would have added one to the Windows drive on an update.

You can post this to see where files are.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Hodor on 2015-06-10
Thanks oldfred,
Good to hear that Grub does/has done the right thing.
I'll go ahead with a re-install of windows 8.1 (with my Ubuntu drive removed) to clean up the mess.  
I think the change in Grubs behaviour follows an upgrade - I'm happy with the Windows and Ubuntu booting processes and don't want to fiddle with the efi partitions yet (Windows gave me an awfull experience with an excess boot loader which took me a while to fix).

Kind regards.

---

