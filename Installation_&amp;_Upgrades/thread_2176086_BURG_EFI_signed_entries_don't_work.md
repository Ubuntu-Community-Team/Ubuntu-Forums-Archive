---
title: "BURG EFI signed entries don't work"
date: 2013-09-22
forum: Installation &amp; Upgrades
---

### Post by Resilldoux on 2013-09-22
Hi there,

So I've installed BURG, a fancy grub-like bootloader with more eye candy, on my Ubuntu 13.04 x64 box now and it wants to boot an EFI boot entry by default. Every time it does so I get thrown kernel panics and my system doesn't boot. I have to manually select the "normal" one in order to boot successfully. Personally, I don't have any use for the EFI entries and I don know how I got even them. Is there any way to remove these entries for good, even after an "sudo update-burg"?

---

### Post by oldfred on 2013-09-22
I do not think burg has been maintained for quite a while. If you want a boot manager, you can try rEFInd, if booting with UEFI. If BIOS then something is installed incorrectly. Then try Boot-Repair and post link to BootInfo report.

       Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Resilldoux on 2013-09-23
Thanks, but I actually don't need to boot with UEFI, I'm using regular BIOS. BootInfo report: [http://paste.ubuntu.com/6144934/](http://paste.ubuntu.com/6144934/)

---

### Post by oldfred on 2013-09-23
I do not see anything wrong. 

You do have LVM on sda, but I do not know about that or if that confuses os-prober.
Your Windows data partition on sdb has the hidden system reserved partition that Windows wants with UEFI installs. It may have just created it as it has to be before the first Windows install on gpt drives. 

If you have BIOS/CSM mode on in UEFI you should not get any UEFI boot. And you have no efi partitions for any boot loader or UEFI to see to implement UEFI boot.

---

### Post by Resilldoux on 2013-09-25
Yes, I use BIOS mode in UEFI, so I I would also presume I don't need the EFI entries. The problem is, my machine does seem to think so, irregardless. How can I help resolve this?

---

### Post by oldfred on 2013-09-25
Since it is a combined UEFI/BIOS system, your UEFI menu will always show some of both. But if you have only installed BIOS mode, that is all that should be shown to boot your system. You have no efi partition with efi boot files.


But for example Ubuntu live installer offers both UEFI & BIOS mode, so your system should offer to boot either way.

---

### Post by jason-r-prim on 2014-06-22
Remove efi.signed From Burg Menu


[LIST]
[*]**Navigate To Boot Directory**
[*]*cd /boot*
[LIST]
[*]**Enter Superuser Mode**
[*]*sudo su (***Enter Your Password)**
[LIST]
[*]**Change The Name Of Following File:**
[*]*mv * vmlinuz-3.13.0-29-generic.efi.signed #vmlinuz-3.13.0-29-generic.efi.signed
[LIST]
[*]**Update burg (So Next Time You Boot Up The Option To Boot Up In The .efi.signed Will Not Show Up).**
[*]*update-burg*
[/LIST]
[/LIST]
[/LIST]
[/LIST]
*&#8203;***Your Burg Menu Should Be With Out This Option And When Folded Default Should Be The First Os Listed**

---

