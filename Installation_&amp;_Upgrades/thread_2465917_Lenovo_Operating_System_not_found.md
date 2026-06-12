---
title: "Lenovo: Operating System not found"
date: 2021-08-14
forum: Installation &amp; Upgrades
---

### Post by grapes-of on 2021-08-14
Getting an error (1962) trying to install 20.04 on a Lenovo Thinkcenter e72m with an SSD in it. I've run Boot Repair and tried renaming the boot drive in EFI to "windows boot manager" as suggested in some other threads though I am not sure if I did this correctly. Additionally I have tried flashing/updating the BIOS but that operation failed. Boots great from Live USB. Installs with no warnings. I did get it to boot once and get it to go to GRUB text interface once but can't get either to happen again. If there is any help anyone can provide I would appreciate it. Been trying to get it operational all day!

Heres the pastebin: [https://paste.ubuntu.com/p/Vdp5cvbzf2/](https://paste.ubuntu.com/p/Vdp5cvbzf2/) 

Thanks!

---

### Post by yancek on 2021-08-15
You should have a key which should be shown on boot to access the BIOS firmware and Boot Options.  Can you access Boot Options?  You do have an entry for Ubuntu there which shows on line 33 and 60 of boot repair.  Try accessing that to see if you can boot.  If you look at lines at lines 36 and 63, you will see windows boot manager but the entry points to an ubuntu file so you will have to change that back before you can boot windows.  If you look at the contents of the EFI partition, lines 92 to 103, you will not see and windows files so those will have to be replaced and you will need some windows tool for that.  Not sure how that would have happened..

---

### Post by oldfred on 2021-08-15
Years ago for some difficult UEFIs we used to suggest the renaming of Windows Boot Manager to use /efi/ubuntu/shimx64.efi.
But that normally did not work with dual boot as Windows updates reset it. And then things did not work again.

But since you only have Ubuntu, with no Windows install, the use of Windows Boot Manager entry to boot ubuntu is ok. Should not be needed, but a few systems want a "Windows Boot Manager" UEFI entry.

The error 1962 is from Lenovo's UEFI, as grub2 does not have error codes. (Old grub legacy did, but is not for newer systems). 

Is system set to boot in mode you have installed?
The boot setting for installed systems UEFI or BIOS/legacy/CSM is separate from the mode you select to boot live installer. 
Make sure UEFI is set for UEFI boot.

Generally you should update UEFI as it includes many fixes. Some help Linux even though often not documented.
Spectre virus, repoline firmware update
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 

Another 1962 thread
[https://ubuntuforums.org/showthread.php?t=2243715](https://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by grapes-of on 2021-08-15
Thanks for various explanations. Oldfred is right I am not trying to duel boot just get Ubuntu. Kinda good to hear that changing the name to to "Windows Boot Manager" is not so important these days.

I've tried to set to UEFI only as well as auto. If I go into the boot manager with F12 from startup I can see:
SATA 2: ADATA SX900
   ->Legacy: ADATA SX900
   ->UEFI: windows Boot Manager
Network 1
Enter setup

selecting UEFI results in hitting 1962 error again.

I have tried updating BIOS/UEFI from a flashdrive but that operation failed so maybe I better try that again.

---

### Post by grapes-of on 2021-08-15
Managed to install UEFI updates. Instead of installing **f1jt74 **I had to go back a version and do F1KT73A. Now it boots.

---

