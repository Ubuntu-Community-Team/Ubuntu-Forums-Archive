---
title: "Trying to set up a Win 8.1 + Ubuntu UEFI dual-boot"
date: 2015-03-03
forum: Installation &amp; Upgrades
---

### Post by kansasnoob on 2015-03-03
I feel really stupid, but step #1 was to install [Windows enterprise free-trial]("https://technet.microsoft.com/en-us/windows/windows-8.aspx?f=255&MSPPError=-2147217396") in UEFI mode, so I installed a refurb 160 GB SATA drive, booted into BIOS and selected UEFI boot = yes, booted an Ubuntu live DVD (which did boot in UEFI mode), and used Gparted to create a GPT partition table on the drive. I did not create any partitions. I then booted the Windows DVD and installed it with no real fanfare. Looks like a fail to me:

[http://paste.ubuntu.com/10519037/](http://paste.ubuntu.com/10519037/)

Don't know what went wrong as I'd done this once before, albeit with [different installation media]("http://getintopc.com/softwares/operating-systems/windows-8-1-enterprise-free-download-iso-32-bit-64-bit/") and Windows had installed in UEFI mode just fine:

[http://ubuntuforums.org/showthread.php?t=2264348](http://ubuntuforums.org/showthread.php?t=2264348)

So, first question, am I right that Windows did not install in UEFI mode?

Second question, if Windows is not installed in UEFI mode I'm fairly certain that I would not want to install Ubuntu in UEFI mode. Is that correct?

If that's the case then I probably will install Ubuntu in non-UEFI mode and perform some ubiquity testing as long as I'm in this situation. BTW testing is the entire purpose of this exercise. I'd not be repeating this but I had to rush setting this mobo up originally to perform some testing prior to the release of 14.04.2 so I used a hard drive that had been purchased for another purpose.

Third question, what in the world did I do wrong? I'd swear that I followed the same procedure as with my prior dual-boot but I obviously blundered somewhere along the way :oops:

I'm certain that I downloaded the 64 bit version:

```
lance@lance-desktop:~$ ls Downloads/Misc_iso
**[COLOR="#FF0000"]9600.17050.WINBLUE_REFRESH.140317-1640_X64FRE_ENTERPRISE_EVAL_EN-US-IR3_CENA_X64FREE_EN-US_DV9.ISO[/COLOR]**
gparted-live-0.19.1-4-i486.iso
gparted-live-0.4.6-1.iso
SeaToolsDOS223ALL.ISO
super_grub2_disk_hybrid_2.00s2.iso
super_grub_disk_hybrid-1.98s1.iso

```

I certainly feel like a mighty humble Bumble ;)

---

### Post by oldfred on 2015-03-03
You have to also boot Windows in UEFI mode. Default setting in UEFI and maybe other settings are required. But from UEFI boot menu you should get two options, one clearly UEFI - name/label of flash drive and the other just the name of flash drive which is a BIOS boot option.

How you boot both Windows & Ubuntu  is how it installs as boot mode cannot be changed once you start. 
I thought newer Windows offered both UEFI & BIOS in UEFI menu, similar to Ubuntu.

You now have another issue. When drive is gpt, but you install Windows in BIOS mode, it auto converts to MBR(msdos), but does not do it correctly. It leaves backup gpt partition table. Linux tools see both MBR & gpt, get confused and only offer to totally erase on a new install.
But you can use fixparts to remove backup gpt data.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

Once drive is MBR, you must have Ubuntu in BIOS mode. If you install in UEFI with gpt then it has to erase Windows in MBR mode. 
Only if Windows is UEFI with gpt, can you then have Ubuntu either UEFI (preferred) or in BIOS boot mode.
But you can only switch from one boot mode to another by rebooting, so if not same boot mode cannot use grub to choose unless in same boot mode.

And the girl in the blue dress lives in the white house, and the boy in the yellow shirt in in the green house, what color house does the girl in the yellow dress live in. -- ohh wait that is a different puzzle.

---

### Post by grahammechanical on 2015-03-03
If Windows was installed in EFI mode than sda2 would show something like this

> 


Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi [COLOR=#222222][FONT=Verdana][/FONT][/COLOR]
I have picked that off of a Boot Repair report from another thread. A successful EFI install of Ubuntu would add this

>                        /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 

I have no idea why things went differently this time. I lack a UEFI motherboard to get experience on.

Regards.

---

### Post by kansasnoob on 2015-03-04
Arrrgh - I see now - whereas Ubuntu boots into UEFI mode with no user interaction if UEFI mode is selected in BIOS, booting Win 8.1 installation media in UEFI mode requires that I press F10 to display the BIOS boot menu. Then from there I must specifically select booting the media in UEFI mode. So I guess our installation media is smarter than theirs ;)

@ oldfred, thanks for the reminder about fixparts. I've used it before but so seldom I hadn't thought about it.

@ grahammechanical, I'm still asking myself why I thought it was a good idea to wish for UEFI capable hardware. My brain's all twisted into a pretzel :-?

---

### Post by oldfred on 2015-03-04
With my new UEFI motherboard I had a heck of time trying to get it to boot in UEFI mode. 
Although it had UEFI & BIOS settings and even a UEFI or BIOS, the only setting that would boot Ubuntu on flash drive in UEFI mode was UEFI only.

I think UEFI varies a lot by vendor.

---

