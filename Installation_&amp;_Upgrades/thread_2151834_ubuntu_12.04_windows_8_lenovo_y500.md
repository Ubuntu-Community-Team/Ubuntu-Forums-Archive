---
title: "ubuntu 12.04 windows 8 lenovo y500"
date: 2013-06-05
forum: Installation &amp; Upgrades
---

### Post by ontbij on 2013-06-05
Greetings,
I have reached point where I can boot into Ubuntu, but not Windows 8.
I have ran the boot repair --> [http://paste.ubuntu.com/5734329](http://paste.ubuntu.com/5734329)

Currently I have BIOs set with secureBoot off, Legacy Support, priority (UEFI)

With these settings I can boot straight into Ubuntu from GRUB, but if I choose Window8 loader it does not complete.

It will load GRUB (can go into Ubuntu as normal, to reach windows must click 'Windows UEFI boot recovery')
     --trying to use standard windows loader, the windows 8 boot selection lists drive path error, and UEFI  error

Any help is much appreciated

Thanks

---

### Post by oldfred on 2013-06-06
Actually the one labelled recovery is your correct boot entry for Windows. It should not be recovery.

 /dev/sdb2        06A8-EB17                              vfat       SYSTEM_DRV
/dev/sdb3        3AA9-2AC2                              vfat       LRS_ESP

   /dev/sdb2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sdb3       2,582,528     4,630,527     2,048,000 -

You can only have one efi system partition (sdb2 and 06a8-eb17), but your system put other efi files into sdb3 also. So somehow it is mis-identified.

        
 menuentry "Windows UEFI [COLOR=#ff0000]recovery[/COLOR] bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]06A8-EB17[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

Above entry should not say recovery. All the entires in 25_custom were created by Boot-Repair, so you can manually edit to correct them. 

See **efi Menu cleanup**
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

