---
title: "Ubuntu 15.04 install using USB failed: &quot;Unable to mount root fs&quot; (EFI-boot problem?)"
date: 2015-06-27
forum: Installation &amp; Upgrades
---

### Post by fh-faraz-hussain on 2015-06-27
Hi,

I was installing Ubuntu on a friend's laptop and it seemed to have successfully completed.  I got a message to reboot the machine, but then it said:  "Reboot and select proper Boot device or insert Boot media in selected Boot device and press a key"

Now it won't even boot with the usb drive. It gives a long message starting "ACPI PCC probe failed." and ending: "Kernel panic -- not syncing: VFS: Unable to mount root fs on unknown-block(1,0)"

I searched and saw this thread: [http://ubuntuforums.org/showthread.php?t=1751574](http://ubuntuforums.org/showthread.php?t=1751574)

Here is my output when I went to a basic shell from Grub:

$ ls
(memdisk) (hd0) (hd0,msdos1) (hd1) (hd1,gpt3) (hd1,gpt1) (hd1,gpt1) (hd2)

$ ls (hd0)
error: file `/boot/grub/x86_64-efi/zfs.mod' not found
error: file `/boot/grub/x86_64-efi/tar.mod' not found
error: file `/boot/grub/x86_64-efi/sfs.mod' not found
error: file `/boot/grub/x86_64-efi/nilfs2.mod' not found
error: file `/boot/grub/x86_64-efi/minix.mod' not found
error: file `/boot/grub/x86_64-efi/afs.mod' not found
error: file `/boot/grub/x86_64-efi/affs.mod' not found
Device hd0: No known filesystem detected - Sector size 512B - Total size 15702912KiB

$ ls (hd0,msdos1)
Partition hd0,mdsod1: Filesystem type fat, UUID 6593-A809 - Partition start at 1024KiB - Total size 15701888KiB

$ ls (hd1)
Device hd0: No known filesystem detected - Sector size 512B - Total size 7325745854KiB

$ ls (hd1,gpt3)
Partition hr1,gpt3: No known filesystem detected - Partition start at 726374400KiB - Total size 6199296KiB

$ ls (hd1,gpt2)
Partition hd1,gpt2: Filesystem type ext* - Last modification time 2015-05-26 20:58:33 Friday, UUID <full-uuid-here> - Partition start at 525312KiB - Total size 725849088KiB

$ ls (hd1,gpt1)
Partition hd1,gpt1: Filesystem type fat, UUID B07D-77C0 - Partition start at 1024KiB - Total size 524288KiB

$ls (hd2)
Device hd2: No known filesystem detected - Sector size 2048B - Total size 514KiB

Note: I just wanted Ubuntu, not dual boot, so I had done a normal "erase-all" install.

Thanks in advance.
F.

---

### Post by oldfred on 2015-06-27
What brand/model laptop?

Do you  have secure boot on or off, usually better to have it off. But should work if secure boot is on, if you booted flash drive installer in secure boot mode to install. Only then does it install in secure boot mode.

Some brands have modified UEFI, to boot by UEFI description and only valid description is "Windows". That is not UEFI standard.
But if only booting Ubuntu we can rename it to have Windows description or copy grub into /EFI/Boot and rename it to bootx64.efi which is the hard drive boot entry (which you may have to add to UEFI menu).

Can you enter exit and press enter?

Can you in UEFI choose the Ubuntu entry. Or use one time boot key( often f10 or f12)?

Sometimes you have to do a full power down or cold reboot. If laptop you also need to remove battery. Hold power switch for 10 sec or so, to drain any residual power. Then you may be able to reboot into UEFI or boot?

Details on several alternatives or work arounds are in link in my signature.

If you can boot live installer again:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by fh-faraz-hussain on 2015-06-27
Toshiba Satellite C55. I had disabled secure boot earlier.

btw, CSM boot makes things worse (doesn't enter grub), so I'm back to UEFI.

$ /boot/grub
x86_64-efi efi.img font2.pf2 grub.cfg loopback.cfg

$ /efi/boot
BOOTx64.EFI grubx64.efi

---

### Post by oldfred on 2015-06-27
Have you tried backing up bootx64.efi and renaming grubx64.efi to bootx64.efi?

Then boot the hard drive entry that is bootx64.efi?

---

### Post by fh-faraz-hussain on 2015-06-28
Thanks again oldfred. On my USB, I just backed up and renamed as you told me, then tried booting -- no luck.

> **oldfred said:**
> Then boot the hard drive entry that is bootx64.efi?

Sorry, I don't think I really know what this means ... I need to specify something somewhere? In grub?

btw, my usb's /boot/grub/x86_64-efi/ dir. has 238 files (out of which 229 are .mod files), but it is indeed missing the .mod files listed in my first post.

Just a reminder, I had used this usb for the original install. But now I can't boot using this usb. Wondering why did it not complain about the missing .mod files to begin with.

---

### Post by fh-faraz-hussain on 2015-06-28
My /boot/grub/grub.cfg says: 

```

menuentry "Try Ubuntu without installing" {    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --- cdrom-detect/try-usb=true noprompt persistent
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --- cdrom-detect/try-usb=true noprompt persistent
    initrd    /casper/initrd.lz
}

```

Is the "/cdroom" the culprit? ...

**Update: Removing "/cdrom" doesn't help.**

---

### Post by fh-faraz-hussain on 2015-06-28
Boor-repair-disk results: [http://paste.ubuntu.com/11786680/](http://paste.ubuntu.com/11786680/)


I think I may need to turn on the boot flag for my EFI System Partition. How do I do that?

(source: [https://askubuntu.com/questions/493051/just-installed-ubuntu-14-04-but-after-restart-it-wont-boot/493060#493060](https://askubuntu.com/questions/493051/just-installed-ubuntu-14-04-but-after-restart-it-wont-boot/493060#493060))

---

### Post by sudodus on 2015-06-28
I have a two year old Toshiba, SATELLITE PRO C850-19W (PSCBXE), and it is rather easy to boot with and without UEFI. But I have read that newer models are more difficult to boot.

At least I can help with the boot flag. How did you get the boot-repair boot-info results? Did you use the boot-repair iso file to make a USB boot drive and use that drive? I have the version with a green wallpaper (with a jumping person). I did not find the version number. In that case you find gparted via the menu at the bottom left corner, and ***gparted can edit flags***.

-o-

It is very strange if the computer boots from a boot-repair pendrive, but not from the Ubuntu pendrive, that you used to install the system earlier. Maybe the Ubuntu pendrive is damaged now (for some reason). You could try to re-install the Ubuntu iso file into that pendrive.

But *oldfred* knows these things better than I, so I suggest that we wait for him to reply. He lives in another time zone ...

---

### Post by oldfred on 2015-06-28
It seems like you may be modifying the USB live installer's grub files. That has  a somewhat different grub that is configured with just the files it needs to boot, not all grub files to boot any configuration you may install. Do not modify installer, or you may have modified it enough already that you need to create a new one. You should always have a current version live installer to be able to boot to make repairs or certain changes if needed.

You have boot flag on sda1 as it says it is the ESP - efi system partition.

UEFI is the very first thing that loads and has replaced BIOS. It also normally has a fast boot setting where it does not check for changes (which is often the case) and just immediately turns over to boot system. A standard startup goes thru various checks for what hardware you have and stores that where operating system can find it, so operating system knows what hardware you have. Often best to turn off fast boot in UEFI or some have time settings (my motherboard let me set it to 3 sec) so you can press correct key (often del or f2) to get into UEFI to change settings or choose which system to boot.

You should also have a one time boot key like f10 or f12 that should show boot options. It may show both CSM/BIOS & UEFI but since your install is UEFI you must only use UEFI settings.

These are your UEFI boot entries. Not sure why you have duplicate network boot entries, which rarely are used. And Ubuntu entry is not standard, but I do not fully understand all the versions of entries that efibootmgr shows.

```
 efibootmgr -v
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0000,0001,0002,0003,0009,000A,000B
Boot0000* [COLOR=#ff0000]ubuntu[/COLOR]    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0001* UEFI: IP4 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(f8a963be35db,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0002* UEFI: IP6 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(f8a963be35db,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0003* UEFI: PNY USB 2.0 FD 1100    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(1,0)HD(1,800,1df2f00,0434dcc3)..BO
Boot0009* UEFI: IP4 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(f8a963be35db,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot000A* UEFI: IP6 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(f8a963be35db,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot000B* UEFI: PNY USB 2.0 FD 1100    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(1,0)HD(1,800,1df2f00,837ec5d8)..BO


```

That is not showing any CSM/BIOS entries nor a hard drive boot entry.

This is my ubuntu entry & my hard drive boot entry, but a different UEFI, so your may never be identical. I manually added the bootx64.efi entry, just to see how it works, but do not have to use it as my UEFI will directly boot the ubuntu entry. I also do not need shim as I have secure boot off. With secure boot off, you can use shimx64.efi or grubx64.efi where shim only works (and signed kernels) if secure boot is on.
```
 Boot0000* ubuntu    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File([COLOR=#ff0000]\EFI\UBUNTU\SHIMX64.EFI[/COLOR])
Boot0009* UEFI OS    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File([COLOR=#ff0000]\EFI\BOOT\BOOTX64.EFI[/COLOR])..BO


```

You may have to scroll right to see the exact files it is using to boot. And in both cases it boots with a grub.cfg in /EFI/ubuntu folder All the number info is related to the hard drive number and GUID for the ESP.

Some example UEFI screens, your may be similar but not identical.

---

### Post by fh-faraz-hussain on 2015-07-04
This problem is now solved, not in an ideal way, but I will still describe it in case its helpful for anyone.

[B]tl;dr version: I created a bootable flash drive for "Boot-repair-disk" ([http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)), booted using it, and chose "Recommended repair (repairs most frequent problems)". That's it.
[/B]

More details:
This was a friend's laptop, and I wanted to resolve this quickly, so couldn't do things the way I would have wanted. Ideally, I would have wanted to identify the exact problem, and also install it in a way that could be replicated in the future. Anyway, here goes.

> It is very strange if the computer boots from a boot-repair pendrive, but not from the Ubuntu pendrive, that you used to install the system earlier. Maybe the Ubuntu pendrive is damaged now (for some reason). You could try to re-install the Ubuntu iso file into that pendrive.

sudodus: That's right it did boot from the boot-repair flash drive. I had earlier re-installed the Ubuntu-iso and re-installed, but again saw the same problem: installed went through fine, but did not boot due "Unable to mount root fs" error. So boot-repair probably just fixed the file locations, or links or something like that needed for grub to work -- I don't really know for sure.

**oldfred: Many thanks** for your help! I don't understand UEFI well enough, but your simple suggestion about boot-repair has done the job. 

I will mark this thread as solved.

---

