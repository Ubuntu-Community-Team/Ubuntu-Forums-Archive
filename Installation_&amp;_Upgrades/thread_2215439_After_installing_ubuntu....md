---
title: "After installing ubuntu..."
date: 2014-04-06
forum: Installation &amp; Upgrades
---

### Post by Sebastian_Ulloa on 2014-04-06
Hi everyone!):P
I just finished to install ubuntu, I had to do it manually so I didn't use wubi. After installing it I tried to change Windows boot loader (WBL) so I could boot on Ubuntu, but I didn't know the path, neither the device. My hard disk was this before installing Ubuntu:


[TABLE="width: 946"]
[TR]
[TD]Number[/TD]
[TD][/TD]
[TD]Start[/TD]
[TD][/TD]
[TD]End[/TD]
[TD][/TD]
[TD]Size[/TD]
[TD][/TD]
[TD]File[/TD]
[TD][/TD]
[TD]system[/TD]
[TD][/TD]
[TD]Name[/TD]
[TD][/TD]
[TD]Flags[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD="align: right"]1[/TD]
[TD][/TD]
[TD]1049kB[/TD]
[TD][/TD]
[TD]274MB[/TD]
[TD][/TD]
[TD]273MB[/TD]
[TD][/TD]
[TD]fat32[/TD]
[TD][/TD]
[TD]EFI[/TD]
[TD][/TD]
[TD]system[/TD]
[TD][/TD]
[TD]partition[/TD]
[TD]hidden[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="align: right"]2[/TD]
[TD][/TD]
[TD]274MB[/TD]
[TD][/TD]
[TD]20.4GB[/TD]
[TD][/TD]
[TD]20.1GB[/TD]
[TD][/TD]
[TD]ntfs[/TD]
[TD][/TD]
[TD]Basic[/TD]
[TD][/TD]
[TD]data[/TD]
[TD][/TD]
[TD]partition[/TD]
[TD]hidden,[/TD]
[TD]diag[/TD]
[/TR]
[TR]
[TD="align: right"]3[/TD]
[TD][/TD]
[TD]20.4GB[/TD]
[TD][/TD]
[TD]20.7GB[/TD]
[TD][/TD]
[TD]273MB[/TD]
[TD][/TD]
[TD]fat32[/TD]
[TD][/TD]
[TD]EFI[/TD]
[TD][/TD]
[TD]system[/TD]
[TD][/TD]
[TD]partition[/TD]
[TD]boot[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="align: right"]4[/TD]
[TD][/TD]
[TD]20.7GB[/TD]
[TD][/TD]
[TD]20.8GB[/TD]
[TD][/TD]
[TD]134MB[/TD]
[TD][/TD]
[TD]Microsoft[/TD]
[TD][/TD]
[TD]reserved[/TD]
[TD][/TD]
[TD]partition[/TD]
[TD][/TD]
[TD]msftres[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD="align: right"]5[/TD]
[TD][/TD]
[TD]20.8GB[/TD]
[TD][/TD]
[TD]346GB[/TD]
[TD][/TD]
[TD]326GB[/TD]
[TD][/TD]
[TD]ntfs[/TD]
[TD][/TD]
[TD]Basic[/TD]
[TD][/TD]
[TD]data[/TD]
[TD][/TD]
[TD]partition[/TD]
[TD]msftdata[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="align: right"]6[/TD]
[TD][/TD]
[TD]346GB[/TD]
[TD][/TD]
[TD]640GB[/TD]
[TD][/TD]
[TD]294GB[/TD]
[TD][/TD]
[TD]ntfs[/TD]
[TD][/TD]
[TD]Basic[/TD]
[TD][/TD]
[TD]data[/TD]
[TD][/TD]
[TD]partition[/TD]
[TD]msftdata[/TD]
[TD][/TD]
[/TR]
[/TABLE]

Then I Shrinked my disk and I installed Ubuntu in the new partition sda7. 
I don't which device and path choose on WBL. [CENTER][COLOR=#000000]:confused:[/COLOR][/CENTER]

---

### Post by oldfred on 2014-04-06
Best to see details.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

      
 With UEFI If you run any fixes from Boot-Repair do not say yes to 'buggy' UEFI fix. That is only for systems where UEFI has been modified by vendor to only allow Windows to boot. Only if we determine you have one of those systems then you may need it.

---

### Post by Sebastian_Ulloa on 2014-04-12
Sorry for the delay, here is the boot-info summary
[http://paste.ubuntu.com/7241969/](http://paste.ubuntu.com/7241969/)

I tried to use EasyBCD on windows, but it didn't work.

---

### Post by oldfred on 2014-04-12
Looks pretty normally to me.
From UEFI menu can you boot both the Windows efi file and the ubuntu efi file.
Or with one time boot key, you should see both Windows & ubuntu as boot options.

It looks like you have the signed kernel installed. UEFI may show both grub & shim if you have secure boot off. With secure boot on you only should get one ubuntu entry that is shim or the signed version of grub.

And then from grub menu you have both Ubuntu & Windows. There is a bug where with secure boot on, grub cannot boot Windows from grub menu.

Report does not show internal UEFI variables like most and does not show video chip.
What model computer and what video card/chip do you have.

Does this show the UEFI boot options & details on what they are?
 sudo efibootmgr -v

---

### Post by Sebastian_Ulloa on 2014-04-12
Well, I don't know how to change from windows boot loader to grub(if that's what you are trying to say me). 
I looked in the BIOS if secure boot was available, but my computer doesn't have that option:

Boot Configuration
Boot Mode                   [UEFI]
External Device Boot      [Enabled]
Network Boot                [Disabled]

My computer reference is Vaio e14p, my video card is AMD Radeon HD 7570M/HD 7670M Graphics.

I tried the command you told me in the LiveCD terminal, but it said that the command wasn't found, so I google-d it and I didn't find anything.

Thanks for the patience, I'm a total beginner in Ubuntu

---

### Post by oldfred on 2014-04-12
It seems a lot of Sony's are hard coded to only boot Windows.
But different models may also need other settings, not sure about your specific model.

 Sony Vaio & Ubuntu 13.10
 [http://www.slideshare.net/slideshow/embed_code/27418512](http://www.slideshare.net/slideshow/embed_code/27418512)
Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2200818](http://ubuntuforums.org/showthread.php?t=2200818)
Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)
Sony Vaio Pro 13 initrd issues - turn off UUID and libata.force=noncq splash parameter needed
[http://ubuntuforums.org/showthread.php?t=2189052](http://ubuntuforums.org/showthread.php?t=2189052)
Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)
Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

---

