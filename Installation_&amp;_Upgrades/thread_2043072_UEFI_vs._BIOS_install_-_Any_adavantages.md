---
title: "UEFI vs. BIOS install - Any adavantages?"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by El Potro on 2012-08-15
Hello community,

I'm setting up a computer with an ASUS P8H77-M PRO motherboard which offers two options: UEFI or BIOS, and I'm here wondering which option should I choose.

Is there any real advantage to choose UEFI? and disadvantages?

A small remark: I'm planning to use LVM and install several distros to this computer, using GRUB 2.

Thanks!

---

### Post by oldfred on 2012-08-15
I do not know LVM, but someone posted that the practical advantages are not as much as the theoretical.

Is Windows one of the installs as that requires gpt with UEFI or BIOS with MBR(msdos). But if only Linux then you can use gpt whether UEFI or BIOS.

UEFI is the new thing, not sure if there are a lot of advantages or not. Then main disadvantage is that as new, not many know it and some software still is resolving bugs. In Ubuntu most of the grub2 bugs are resolved or have work arounds.

Either way I would create the efi partition as the first partition or leave space for it. As the efi partition has to be first it can be difficult to try to add it later when drive is full of data. If using gpt and BIOS with Linux you need a tiny 1MB unformatted bios_grub partition.

gpt has some minor advantages over MBR.
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)

My system is BIOS only, but I have gpt on two drives including my newish SSD and BIOS on my old XP and an older data drive. I just used gparted to partition.

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.Must be 64bit version to have UEFI

---

### Post by El Potro on 2012-08-15
Hi Fred

Well, the case is not so much about LVM, but particularly about UEFI vs. BOOT in a system with multiple distros. I don't plan to use Window$ at all.

It sounds like a good idea to leave some space at the beginning. Actually I usually create a separate GRUB2 partition after the BIOS_BOOT, so that I don't depend on any particular distro for my boot-loader.

But now with UEFI the things are different. As far as I know, I'll have to create a ESP partition instead of a BIOS_BOOT, but the question that arises is, is it a good idea to install GRUB2 as the main .efi image in the ESP partition and then load all the distros from GRUB2?

Or is it a better idea to use rEFInd and that each distro will have a separate .efi image? is GRUB2 capable of loading different .efi images? I believe it loads directly the kernels and initrm, so I'm asking myself, what would be the difference/advantage then?

---

### Post by oldfred on 2012-08-15
I do not know  rEFInd.

And grub2's os-prober does not correctly find other efi installs. Boot-Repair now creates a Windows chainload which really could be for any install in efi partition. Not sure how many of the other Linux have UEFI versions.

A Windows chainload:

menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

Not sure if all installs are grub2 how each would write a .efi file to boot a different partition. At this point you just may have to back up each. Or maybe with grub2 if one system is booted efi, then all it has to do is find the kernel & init files in the other install to boot? Not seen a dual Linux UEFI boot yet.

---

### Post by El Potro on 2012-08-16
Well Fred, if you don't know and nobody else can help with GRUB2, multiple distros and UEFI, then I guess I'm going to disable the UEFI feature and go back with a traditional BIOS+GPT approach. Because I'm setting up this computer for a friend and I don't want to mess around too much.

The day I get a UEFI motherboard for myself there will be more information available on this and then I'll experiment further. 

Anyways if anybody knows more about this topic, I'll be glad to receive more information.

Thanks

---

### Post by smartboyhw on 2012-08-16
Well, unless you like Windows 8 (which requires Secure Boot on EFI), I don't recommend using UEFI. Use BIOS. It's better.

---

### Post by El Potro on 2012-08-16
Hi smartboyhw

why exactly you say I shouldn't use UEFI? And why BIOS as far as you concern is better? 

I don't use Windows at all, who cares about that trash anyway? ;)

---

### Post by smartboyhw on 2012-08-16
> **El Potro said:**
> Hi smartboyhw
 
why exactly you say I shouldn't use UEFI? I don't use Windows at all, who cares about that trash anyway? ;)
 Well, it takes quite a lot of steps to make a UEFI boot CD, that's why I choose BIOS.

---

### Post by El Potro on 2012-08-16
That's a great reason to consider! I remember that I read that somewhere. Thanks for reminding it to me.

Is there any other(s)?

---

### Post by smartboyhw on 2012-08-16
> **El Potro said:**
> That's a great reason to consider! I remember that I read that somewhere. Thanks for reminding it to me.
 
Is there any other(s)?
 No.:)

---

### Post by El Potro on 2012-08-16
And what if the UEFI is BIOS backward compatible, that would mean I could use a UEFI setup and also boot easily from CD/DVD/BD-ROMS, thumbdrives, etc?

---

### Post by smartboyhw on 2012-08-16
> **El Potro said:**
> And what if the UEFI is BIOS backward compatible, that would mean I could use a UEFI setup and also boot easily from CD/DVD/BD-ROMS, thumbdrives, etc?
 If you know how to, Yes.

---

### Post by El Potro on 2012-08-16
OK, so those are the disadvantages. And what are the advantages? (if anybody of you know of any)

---

### Post by smartboyhw on 2012-08-16
> **El Potro said:**
> OK, so those are the disadvantages. And what are the advantages? (if anybody of you know of any)
 
Advantages: BIOS will be killed in years, so it's best to start using UEFI now.:)

---

### Post by El Potro on 2012-08-16
Sadly this is likely to be true only because of MS plans to restrict pc user's to their malware forcing hardware producers to comply with their restrictions. Anyway I don't see why the GNU/Linux community should embrace UEFI if there are no real benefits at all. Perhaps somebody better versed in the topic should express their opinions.

---

### Post by smartboyhw on 2012-08-16
> **El Potro said:**
> Sadly this is likely to be true only because of MS plans to restrict pc user's to their malware forcing hardware producers to comply with their restrictions. Anyway I don't see why the GNU/Linux community should embrace UEFI if there are no real benefits at all. Perhaps somebody better versed in the topic should express their opinions.
 Maybe you should buy a Ubuntu pre-installed computer to avert UEFI.

---

### Post by darkod on 2012-08-16
Like oldfred, I don't know UEFI much and don't have any UEFI board. But from what I have seen here, booting the cd is not difficult, you only need to be aware that with UEFI boards the cd-rom device has two different types, the standard bios mode and the uefi mode.

If you plan to install ubuntu on UEFI you HAVE to boot the cd in uefi mode, otherwise it will not install correctly. And many people seem not to know this, so most attempted UEFI installs end in failures.

Personally i would stick with BIOS as long as it fits your requirements. There will still be number of years until it's phased out and by then you will probably want new hardware anyway. :)

I haven't wasted time to look into win8 and the requirements, but I have installed the preview release in VBox and it's not in UEFI mode. Yet it did install correctly and it's working. Not sure if the final version will require UEFI but the preview release doesn't seem to.

---

### Post by El Potro on 2012-08-16
Thanks for your opinion darkod. I hope somebody else that really knows UEFI good can say something else, because it seems we are all in the same situation. And by the way, is it really so necessary to mention MS crap? Who said anybody needs that?

---

### Post by smartboyhw on 2012-08-16
> **El Potro said:**
> Thanks for your opinion darkod. I hope somebody else that really knows UEFI good can say something else, because it seems we are all in the same situation. And by the way, is it really so necessary to mention MS crap? Who said anybody needs that?
 Well, sorry, that's what happened...Windows 8 wants to kill everybody (including Ubuntu) once and for all, so they used UEFI to stop other bootloaders.... So if your board supports UEFI and that you install Win 8 with a EFI shell, you can't install Ubuntu then.

---

### Post by oldfred on 2012-08-16
I very much doubt that Window can even force you to convert to secure boot on your system. 
The requirement is that for a Vendor to sell a new system with Windows 8 they must turn on the secure bit in UEFI. So new computers will be an issue and several Linux vendors have somewhat different proposals on how to work around the dual boot issue. And from what I have seen so far it is even more complex.:frown:

---

### Post by YannBuntu on 2012-08-16
Hello

> **smartboyhw said:**
> Well, sorry, that's what happened...Windows 8 wants to kill everybody (including Ubuntu) once and for all, so they used UEFI to stop other bootloaders.... So if your board supports UEFI and that you install Win 8 with a EFI shell, you can't install Ubuntu then.

Don't mistake EFI vs SecureBoot:
- (U)EFI is not a problem for FOSS, it is correctly handled by Ubuntu/GRUB2 (some bugs exist, eg [1025555]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555") [1017880]("https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/1017880") [1024383]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383") but they can be fixed by FOSS devs, and currently they have easy workarounds).
- The problem will probably be Microsoft "Secure Boot", in case it can't be disabled. I have little information about it, but i saw articles showing that Ubuntu/Fedora have started working on it.

---

