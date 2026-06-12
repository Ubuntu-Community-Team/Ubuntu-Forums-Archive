---
title: "What happens if I disable secure boot on a Windows to set up a dual boot?"
date: 2021-01-27
forum: Installation &amp; Upgrades
---

### Post by bobnutfield on 2021-01-27
Hello Everyone

I have an HP laptop with an A10 AMD processor and 16GB RAM.  It's always had Windows 10 on it.  I've been predominately a Linux user since 1999, but I'm not very techy.  I know my way around Linux, but I have never been able to set up a dual boot on this aptop because of the UEFI secure boot.  I can get into the BIOS and I've changed the boot order to run a live DVD for Linux, but it continues to boot from the hard drive, ignoring the settings.  I'm assuming this is because of secure boot being enable.  I gave up a few years ago because I had a warranty on this laptop and didn't want to void it.  The warranty has run out and I'd like to set it up to dual boot Ubuntu LTS (I don't distro hop.)  

Am I correct that it is the secure boot being enable that is preventing me from booting from the DVD or USB drive?  Are there additional considerations?  I have been using this laptop for so long with Windows on it (for family members who want it.)  I don't want to damage the Windows installation (even though I am sure Ubuntu will run smoother and faster).  I have set up dual boots many times in the past, but never with a UEFI configuration.

Any thoughts would be greatly appreciated.
Regards

Bob

---

### Post by jeremy31 on 2021-01-27
Secure Boot does not prevent Ubuntu from booting, either from ISO or from an install.  After installing Ubuntu alongside Windows, go into the BIOS settings, system configuration, there might be a OS boot manager  there that needs to have ubuntu first on the list, you will likely have to press F10 twice after placing ubuntu entry on top

---

### Post by bobnutfield on 2021-01-27
Thank you for your reply, but the issue is I can only boot from the hard drive, not from any other installation media.  I have the boot order set to boot from the DVD drive first, USB second and hard drive third.  But it ignores the settings and boots from the hard drive regardless.  I thought it might be because secure boot is enabled (which I can disable), but I wasn't sure what damage it might cause to the Windows installation (I've seen warnings that Windows may not boot at all if I disable it.)

The last time I dual booted (years ago) the was a choice at the boot screen which system to boot into.  Is that no longer the case?

Thanks

Bob

---

### Post by jeremy31 on 2021-01-27
I know I have Linux Mint on a 2 year old HP and it booted the ISO without an issue and I doubt Ubuntu would be any different.  It might be an issue with how the ISO is put on DVD or USB.  I am not an expert on that subject

---

### Post by bobnutfield on 2021-01-27
Thanks for your help.  Finally figured it out.  It was in fact the secure boot.   It was attempting authenticate the Linux boot disk and of course it couldn't, so it just booted the hard drive.  I disabled secure boot and it behaved as I expected.

Thanks again,

Bob

---

### Post by jeremy31 on 2021-01-27
That is strange as the boot loader is signed by Microsoft

---

### Post by CatKiller on 2021-01-27
The mitigations for BootHole (a Secure Boot vulnerability) invalidated a bunch of Microsoft keys. New images should be using new keys, but if you're trying to boot an old image and the keys have been invalidated in your UEFI by a Windows update then it won't work.

---

### Post by grahammechanical on 2021-01-27
> That is strange as the boot loader is signed by Microsoft

I agree. But it depends on the age of the ISO image. Last July a serious vulnerability was discovered in Grub2. It was given the name of BootHole. Developers from several Linux distributions worked together to fix the issue and in cooperation with Microsoft as well.

New builds of ISO images would contain the patched Grub2 code but nothing could be done to upgrade Grub2 on already downloaded ISO images. It was decided that Microsoft should update its secure boot database to prevent the loading of ISO images that did not have the patched version of Grub2.

I do not know if that is the cause of the original poster's problem. Some recommend turning off secure boot as standard procedure for installing a dual boot with Windows. As you say, that should not be necessary. Here is the Canonical report on mitigating BootHole:

[https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities](https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities)

Regards

---

### Post by bobnutfield on 2021-01-28
Thanks for the replies.  As I mentioned above, I got it sorted.  But, I'll mention that the only ISO on DVD I had available was Mint 19.3.  That may be too old for Microsoft to have signed, and that would have been the problem.  I would not have installed Mint because I use Ubuntu as my main system.  I just wanted to test the laptop and see how it would behave since it had never been introduced to Linux if any kind.  It appears that disabling secure boot has no affect on Windows.

Thanks for all your help

Bob

---

