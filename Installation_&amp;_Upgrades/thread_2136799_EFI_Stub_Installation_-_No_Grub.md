---
title: "EFI Stub Installation - No Grub"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by Enlil on 2013-04-18
Hello!

 I've decided to return to Ubuntu after quite a long hiatus with the upcoming 13.04. My question is that I'm curious if anyone has been able to install Ubuntu on a UEFI based computer while not using Grub. I want to be able to turn on my computer, and have it load right into Ubuntu. I've been able to do this on other Distro's with EFI Stub, efibootmgr, etc. Only problem with that was that I was compiling my own kernel's and had to add certain parameters into the config to allow it to boot without a bootloader. I'm not looking for refind, or gummiboot, or anything like that. I'm just looking for a way to bypass Grub, and add a boot option in my UEFI to boot right into Ubuntu.

 Has anyone been able to accomplish this, or is there a guide out there somewhere? I've looked around, but I've found nothing. I'd be grateful if anyone could help me out, thanks! :)

---

### Post by oldfred on 2013-04-18
Not done anything, but some info here.

[https://wiki.archlinux.org/index.php/Beginners%27_Guide#EFISTUB](https://wiki.archlinux.org/index.php/Beginners%27_Guide#EFISTUB)

I think you still need a menu, unless you want to go into UEFI each time?
 Alternative efi boot loader for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by Enlil on 2013-04-18
Thanks for the information oldfred. I've actually set it up to work properly in Arch Linux in the past, I just wasn't aware if it could be done the same way in Ubuntu. With EFI stub, no menu is needed. You just set in UEFI the boot order as you would in any bios, and make the primary boot option to your custom Linux option. When you turn on your computer, UEFI will load Linux right into the kernel bypassing any need for a bootloader. 

 I'm not positive how Ubuntu's kernel is configured though, and if EFI options are enabled in it. If not, that would be a problem.  I also don't know if Ubuntu uses an initramfs, as that would have to be included. As long as I can run efibootmgr from the live dvd, I can probably get things running using the Arch wiki reference, but it would be helpful if someone has done this before in Ubuntu. :)

---

### Post by oldfred on 2013-04-18
I thought I saw in the rodbooks site some reference that Ubuntu did not work with the efi stub. It either needed recompiling or perhaps the initramfs?
But Ubuntu has made lots of changes to support UEFI and secure boot UEFI so changes are always happening.

You can always file a bug if it does not work.

Not many here now much about UEFI, much less all the internal details of how it works.

---

### Post by Enlil on 2013-04-18
Thanks, I'll make sure to file a bug report if necessary. I tried looking around rodbook's site, but haven't come up with much of anything related to efi stub minus an article regarding installing Ubuntu on a Mac with UEFI. If you come across the article, I'd love to read it. If it's possible, I'd like to keep this thread open as there may be someone out there that has done this before, which would be great. When I get down to trying it out, and I succeed I'll have to write a tutorial of sorts so other's can use it.

---

### Post by oldfred on 2013-04-18
It looks like it may work for you.

[http://www.rodsbooks.com/refind/linux.html](http://www.rodsbooks.com/refind/linux.html)
> 
If you're not sure you want to use the EFI stub loader in the long term,  you can perform a fairly quick initial test of it. This procedure  assumes that you have access to a 3.3.0 or later Linux kernel with EFI  stub support compiled into it. (Fedora 17, Ubuntu 12.10, and probably  other distributions ship with such kernels.) Creating this configuration  poses no risk to your current boot options, provided you don't  accidentally delete existing files. The procedure for a quick test is:

---

### Post by Enlil on 2013-04-19
Ah, thanks for the link! That does look hopeful. I'm not looking to install refind, but if I use the commands given in the Arch wiki I'll probably be able to make it happen.

---

