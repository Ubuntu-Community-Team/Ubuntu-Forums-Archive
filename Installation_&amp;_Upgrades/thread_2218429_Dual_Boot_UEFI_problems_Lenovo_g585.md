---
title: "Dual Boot UEFI problems Lenovo g585"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by WanderingAlbatross on 2014-04-20
Dear friends,
Just installed 14.04 on a Lenovo g585 and it proved to be unusual.  When the computer is in UEFI mode it will only allow you to boot from windows EFI partition or two(???) network entries.  It does not allow booting from USB or CD in UEFI mode.  Secure boot setting in Bios has no effect on this.  Even doing the Restart+Shift trick in windows makes windows believe it's okay, but then the BIOS gives an error message when you reboot that it can't boot from USB.

Since I could only boot from CD or USB in Legacy mode, I installed in legacy mode.  Of course,_ this made it impossible for Grub to boot Windows_.  I tried out the boot-repair-disk to see what it would do.  (I learned the repository isn't up yet for Trusty Tahr, so I made the ISO.)  When it ran it acknowledged that it too knew this was not in EFI mode.  After the work it said there had been an error, but to reboot and give it a try.  The final result was _Windows would boot, but Ubuntu would not_.
[http:/paste.ubuntu.com/7289843]("http://paste.ubuntu.com/7289843/")

This was my second crack at a Windows 8 machine.  I am also surprised to find on it a second start button, smaller, to the right of the actual start button.  This button is for activating some special recovery setups including Bios, Boot Order, and probably Lenovo's version of recovering Windows.  If no one can find a solution, I could set it up in such a way that it could be booted from that button for Windows (albeit rather convoluted) , and the other button for Linux.  Strange, isn't it?

Can anyone help me figure out how to get Windows and Ubuntu to boot from the same menu?

---

### Post by oldfred on 2014-04-20
It looks like Boot-Repair tried converting install to UEFI boot. It added the efi partition to fstab, but grub did not install to the efi partition. The converison is just uninstalling grub-pc(BIOS) and installing grub-efi(UEFI). 

It did add a lot of efi boot entries into 25_custom. They for some reason all say recover but some are booting the Windows in efi partition sda2 and some in sda3 which is a recovery efi partition(hidden).

 menuentry "Windows UEFI recovery bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]D00C-B97E[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

   menuentry "Windows UEFI recovery LrsBootmgr.efi" {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]980D-B6A0[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/LrsBootmgr.efi
}


This may be part of the issue or it may be that the efi partition is locked.
 grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.


Does above folder exist in your install?
Can you write into efi partition or does it prevent all writes.

I might try Supergrub to boot into your install. The run dpkg to see it that restores grub correctly.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
    
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

or totally reinstall grub, but I think that is what Boot-Repair did.

Some older slightly different models
 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[URL="http://ubuntuforums.org/showthread.php?t=2112271"]http://ubuntuforums.org/showthread.php?t=2112271

[/URL] Lenovo Ideapad z585 Precise Installed wifi OK Dual Boot Win 7 no Sound SOLVED - other issues
[http://ubuntuforums.org/showthread.php?t=2170099](http://ubuntuforums.org/showthread.php?t=2170099)
Now old as many fixes in 14.04
[URL="https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS"]https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS

[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=2112271"]
[/URL]

---

### Post by WanderingAlbatross on 2014-04-20
Yes. Sound worked already.  Wireless seemed to work, but I couldn't really test it out.  I have a broadband modem I usually use that registers as an ethernet on most installs.  14.04 seemed to have a problem with it.  So I had to use a "normal" broadband modem instead.  I will deal with that problem later.  For now, I will focus on your suggestions on boot repairs.

/usr/lib/grub/i386-pc/ does not exist, only /usr/lib/grub/x86_64-efi.  I seem to recall while I was watching it that it actually removed the 386 grub and installed x86_64-efi afterwards.

I see that the new way of partitioning allows more than four primary partitions, because this is an absolute mess.  There are 10 partitions to get this thing to work.  Would the efi partition be given the flag "bios_grub"?  That's probably not it.  The other possibility to me would be the one flagged "boot,hidden".  That one is formatted to fat32 and labelled "SYSTEM_DRV".  It has read/write capabilities.

---

### Post by WanderingAlbatross on 2014-04-20
Wow!  SuperGrubDisk is a neat trick.  I've played around a little with chroot on a Chromebook before, and Arch, but don't have the whole thing completely understood yet.  Anyway, I booted into Ubuntu.  It currently does not have grub-pc installed.  I'm pretty sure the boot-repair-disk removed it.  If I were to install it it will also add grub-gfxpayload-lists and grub-pc-bin.  More important_ it will remove grub-efi and grub-efi-amd64_.  Doesn't this seem to be going contrary to the direction we want to go?  I'm trying to understand what we are up to.

Are we putting this system in EFI?  If we do then it must already be setup for it, because I will have no way to boot from anything else in EFI than the windows boot partition (sda2).  The whole thing must be done while in Legacy mode.  Then switched over on the next boot to EFI.  Boot-repair-disk seemed to have a problem with that.  It seems to want to have been booted in EFI mode.  Am I operating under a false premise?

---

### Post by oldfred on 2014-04-20
You want UEFI unless you have one of the few systems that will not work in UEFI and can only dual boot with BIOS.
One or two have found that no matter what they do it will not work in UEFI. Vendors and modified UEFI so much that it just does not work. You can still dual boot but have to use UEFI and in BIOS mode boot Ubuntu and in UEFI boot Windows.

But most systems can dual boot with UEFI but may need some boot parameters or issues resolved.

With gpt partitioning you have an efi partition for all boot loaders for UEFI boot. Grub has to write its files into the efi partition. But with BIOS boot on gpt, grub2 has to have the bios_grub partition as a place for core.img.

I think Boot-Repair uninstalled grub-pc which is for BIOS boot and installed grub-efi which is for UEFI boot. You actually can install both but it is a bit tricky as each wants to uninstall the other.

---

### Post by WanderingAlbatross on 2014-04-21
That helps some.  I read your linked page and it brings up an idea I will try.  Someone claimed there are more options available once you put in an adminstrator password in the BIOS.

---

### Post by WanderingAlbatross on 2014-04-24
Well, I settled on using the secondary boot key to get to windows.

The real problem with this machine is that there is no way to boot in UEFI except through network or the Windows partition.  No matter what I tried I couldn't get any other option to come up.  (If anyone else is successful with the Lenovo 585 on this I would love to know.)  Since I could not boot Linux in UEFI, I could not install it in UEFI, because Ubuntu installs in the format that it was booted.  That is logical, of course.

There was one possibility I ran across that I didn't try.  One of the links on Oldfred's signature ([http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)) suggests getting Windows to point to another bootloader.
There it is suggested to run _something like_ this at the C: prompt in Windows:

```
 bcdedit /set {bootmgr} path \EFI\fedora\grubx64.efi 
```

This was promising, but I do not like leaving the well being of Ubuntu in the hands of Windows.  Also, doing this seems to me to be dangerous.  It seems you get one shot to get it right, or else you need to reinstall Windows to get it's boot manager and bootloader working correctly again.  Perhaps I would have been more daring with my own machine.

In the end, I might even like a LEnovo 585 for myself because of the secondary boot key (which they call one-key recovery).  It actually presents an easy solution to the whole mess that has come about because of UEFI.

This also taught me that before I buy a machine I will check to see if I can boot a UEFI capable live CD of Linux there first.  If I can, then all the rest of the game can be played.

---

