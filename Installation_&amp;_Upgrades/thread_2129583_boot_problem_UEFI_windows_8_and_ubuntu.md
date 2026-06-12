---
title: "boot problem UEFI windows 8 and ubuntu"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by salimnaruto on 2013-03-26
i have a problem, i have follox this link [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to install ubuntu in my pc pré installed windows 8.
Now i can run ubuntu, but impossible tu boot windows 8, please helllllllllllllllp meeeeeeeeeeeeeeeeeeeeee, this is the link after boot repair [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by salimnaruto on 2013-03-26
sorry this is the report : [http://paste.ubuntu.com/5650293/](http://paste.ubuntu.com/5650293/)

---

### Post by oldfred on 2013-03-26
You have 3 efi partitions, you can only have one per drive as UEFI boots from efi partition.
Use gparted and remove boot flag from sda6 & sda11.

Are you using this entry in grub. Have you tried with secure boot on and with it off. Some computers only work with it on once Ubuntu is installed, Others work either way.

 menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root CCF4-6432
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

It looks like you tried to install wubi, which does not work on gpt partitioned drives.

---

### Post by echo6 on 2013-03-27
Regarding Secure Boot, it won't boot Linux unless you have added UEFI key signatures.  Also, kernel version 3.8 and above is required.
[http://blog.hansenpartnership.com/category/uefi/uefi-secure-boot/](http://blog.hansenpartnership.com/category/uefi/uefi-secure-boot/)
So I note that [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) states that support has started from 12.10 x64 and 12.04.2 x64 "but it is not fully reliable yet".

I had to disable secure boot in order to boot and install Ubuntu, once I had re-enabled I got "Secure Boot forbids loading module"

[http://paste.ubuntu.com/5652258/](http://paste.ubuntu.com/5652258/) it would appear efivars module is not available on 13.04.

---

### Post by oldfred on 2013-03-27
Ubuntu 12.10 & now 12.04.2 come with the Microsoft key. You can use those with secure boot. But some UEFI implementations work better than others. Some work, some give difficultly and some just about do not work. Often requires a combination of settings in UEFI, and sometimes secure boot on or off.

@echo6
You have Raring which is still in development. You should post only in that sub-forum. Your install also was in BIOS/MBR mode, but it looks like Boot-Repair changed to UEFI.
Your link and requirement for new kernel and UEFI tools is to allow using your own key, not the Microsoft key that is a temporarily workaround.

---

### Post by echo6 on 2013-03-30
@oldfred, BIOS/MBR mode I guess whilst I was working around the BIOS options for booting.  I've now installed 12.10 and it Secure Boot is indeed working, but I need a driver for wifi which is in the kernel proper from 3.8.  From reading [http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/) I should be ok with compiling my own kernels?

---

### Post by oldfred on 2013-03-30
I have never compiled a kernel. But I do not understand why you need to for wifi? Those have always been separate and usually when you install it downloads driver. Some have to download special drivers. Better to post issues with wifi in a new thread with that and model chip in title.

---

