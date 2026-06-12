---
title: "Ubuntu won't load from GRUB2"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by ssaint04 on 2013-02-07
So, I can't get into Ubuntu after installing it. It loaded once after I installed it, and has not loaded since. When I select Ubuntu in GRUB, I get a blank screen that does... nothing.

My machine is an ASUS N56VM. It came preinstalled with Windows 7 Home Premium.

This is the pastebin from Boot-Repair: [http://paste.ubuntu.com/1622383/](http://paste.ubuntu.com/1622383/)



Anyone have any ideas? I'm stumped.

---

### Post by oldfred on 2013-02-08
Since you have Windows 7, you do not have secure boot issues. But your Windows is in UEFI mode and Ubuntu in BIOS mode. To dual boot you also need Ubuntu in UEFI mode. 

Boot-Repair can convert a BIOS install to UEFI install by un-installing grub-pc and installing grub-efi. And that looks like what it did.

But then you have to go directly into UEFI with whatever key your system uses and change to UEFI boot and choose the ubuntu entry.

In Pastebin line 984
BootOrder: 0001,0000,000B,000C
And line 988
Boot0001* ubuntu

Which is from your UEFI, so Ubuntu is there.

---

### Post by ssaint04 on 2013-02-12
Alright, that's a little annoying, as I'd prefer to not have to manually choose Ubuntu every time I turn my machine on.

Is there a way to fix it once I'm in the Ubuntu install? Like reinstalling GRUB? Or would removing Ubuntu and reinstalling it fix it?

---

### Post by oldfred on 2013-02-12
Did not Boot-Repair convert from BIOS to UEFI? But to boot Ubuntu in UEFI mode you have to boot directly from UEFI menu and choose ubuntu. With UEFI mode on. Any boot into Windows leaves Windows as the default.

grub-pc is for BIOS boot, grub-efi is for UEFI boot.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

---

### Post by ssaint04 on 2013-02-12
It did convert from BIOS to UEFI.

So, what you're saying you're saying is the ***only*** way for me to get into Ubuntu is to go into my EFI, and tell it to boot Ubuntu? I can't just let GRUB load, and let it load Ubuntu like I did on my old machine?

(I'm a bit of a Linux novice, sorry if that seems redundant)

---

### Post by oldfred on 2013-02-12
After you use UEFI once, then that choice should be the default until you go back into UEFI and change it.
And if you choose ubuntu then you will get the grub menu.

---

### Post by ssaint04 on 2013-02-12
UEFI booting is the default. Ubuntu still won't loadunless I use the EFI interface, which then loads GRUB, which then will load Ubuntu. If I just let GRUB load, and try and load Ubuntu, nothing happens.

---

### Post by oldfred on 2013-02-13
I guess I do not understand the difference. 

Booting grub one way works and the other does not? But if UEFI boot then both should be the same unless you are somehow switching from UEFI to BIOS and UEFI does that in background when efi does not work? 
Some older UEFI systems used to do that. If efi partition would not boot then it would try BIOS.

Post new copy of BootInfo report

---

