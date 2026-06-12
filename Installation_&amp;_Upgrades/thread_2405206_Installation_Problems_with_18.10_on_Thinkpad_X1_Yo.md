---
title: "Installation Problems with 18.10 on Thinkpad X1 Yoga 3rd Gen"
date: 2018-11-02
forum: Installation &amp; Upgrades
---

### Post by hyottositara on 2018-11-02
Currently, when I try booting with an 18.10 ISO image I copied to a USB flash drive, in order to run the installer on my new laptop, I get the following error message:

```
Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\BOOT\mmx64.efi: Not found
Failed to start MokManager: Not Found
Something has gone seriously wrong: import_mok_state() failed
: Not Found
```
The computer then shuts down.

How I got here:
[LIST=1]
[*]Downloaded the ISO from the website 
[*]Used Rufus 3.3 to copy it to a bootable USB flash drive 
[*]Ran through the installation and selected third party drivers on the *Updates and other software* page 
[*]Was prompted to create a password, something to do with UEFI and driver signing 
[*]Proceeded to the *Installation Type* page 
[*]Canceled the installation since I decided it was prudent to create a Windows recovery drive in case I wanted to go back to Windows (I don't plan on dual booting.) 
[*]Tried to boot with the USB flash drive, got the error above. 
[/LIST]

What I have found:
This [bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171"), which is marked fixed. It would seem that it may fix my issue, but I'm not sure, and I don't know when the fix will be propagated to a new installation image. Would that be when the next version is released, say 18.11?

---

### Post by hyottositara on 2018-11-03
I installed 18.04.1 instead. No notable problems to report, it worked like a charm. (Expect for some issues with my external Thunderbolt 3 dock, but that's another story.)

---

