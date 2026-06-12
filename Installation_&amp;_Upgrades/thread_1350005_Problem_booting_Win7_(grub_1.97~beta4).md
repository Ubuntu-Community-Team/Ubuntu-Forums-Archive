---
title: "Problem booting Win7 (grub 1.97~beta4)"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by martin69 on 2009-12-08
I never had problems installing  windows xp and ubuntu, but know
i've upgraded winxp to win7, after that i installed ubuntu and know i only can 
use ubuntu, because every time i try to boot win7, **grub immediately restart the computer.**

this is my configurations:

 Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37e2575b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   409602047   204697600    7  HPFS/NTFS
/dev/sda3       409602048   921602047   256000000    7  HPFS/NTFS
/dev/sda4       921616920  1124726714   101554897+   5  Extended
/dev/sda5       921616983  1116919124    97651071   83  Linux
/dev/sda6      1116919188  1124726714     3903763+  82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c963c95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2        78782760   283579379   102398310    f  W95 Ext'd (LBA)
/dev/sdb3       290278485   387937619    48829567+   7  HPFS/NTFS
/dev/sdb4       387937620   488392064    50227222+   7  HPFS/NTFS
/dev/sdb5        78782823   283579379   102398278+   7  HPFS/NTFS

#####################################################################


/boot/grub/menu.lst

title           Ubuntu 9.10, kernel 2.6.31-16-generic
uuid            0950559e-0983-48c2-9f5c-ac43fad44736
kernel          /boot/vmlinuz-2.6.31-16-generic root=UUID=0950559e-0983-48c2-9f5c-ac43fad4473$
initrd          /boot/initrd.img-2.6.31-16-generic

title           Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid            0950559e-0983-48c2-9f5c-ac43fad44736
kernel          /boot/vmlinuz-2.6.31-16-generic root=UUID=0950559e-0983-48c2-9f5c-ac43fad4473$
initrd          /boot/initrd.img-2.6.31-16-generic

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            0950559e-0983-48c2-9f5c-ac43fad44736
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=0950559e-0983-48c2-9f5c-ac43fad4473$
initrd          /boot/initrd.img-2.6.31-14-generic

title           Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid            0950559e-0983-48c2-9f5c-ac43fad44736
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=0950559e-0983-48c2-9f5c-ac43fad4473$
initrd          /boot/initrd.img-2.6.31-14-generic

title           Chainload into GRUB 2
root            0950559e-0983-48c2-9f5c-ac43fad44736
kernel          /boot/grub/core.img

title           Ubuntu 9.10, memtest86+
uuid            0950559e-0983-48c2-9f5c-ac43fad44736
kernel          /boot/memtest86+.bin

title         Windows 7
root          (hd0,1)
savedefault
makeactive
chainloader   +1

#####################################################

/boot/grub/grub.cfg

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set 0950559e-0983-48c2-9f5c-ac43fad44736
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=0950559e-0983-48c2-9f5c-ac43fad4473$
        initrd  /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set 0950559e-0983-48c2-9f5c-ac43fad44736
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=0950559e-0983-48c2-9f5c-ac43fad4473$
        initrd  /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set c0d4a82fd4a82a1c
        chainloader +1
}

##############################################################

I first try to install ubuntu in my second hard drive (sdb)
and the problem was the same.... i google it and try every thing
but nothing resolved this problem...

If anyone can help me i'll be appreciated

Martin

---

### Post by presence1960 on 2009-12-08
which bootloader are you using GRUB Legacy 0.97 or GRUB 2? You have both a menu.lst and a grub.cfg file! I need more info here. Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by martin69 on 2009-12-09
I just found the solution.... we dont need to do nothing with ubuntu, and grub config files. The problem is the win bootloader.
 
After installed ubuntu i make all the updates (update grub to 1.97 version to) and did nothing else.
 
Then with the win7 install dvd, used the repair command line and type:
bootrec /fixmbr                (press enter)
bootrec /fixboot               (press enter)
bootrec /rebuildbcd          (press enter)

after that reboot, and win7 will boot properlly, then i used EasyBCD 2.0 Beta
and make a new boot entry for linux, type grub2 and select the option Grub isnt installed to MBR/bootsector, add entry and reboot.
 
Everything is back to normal.

---

### Post by darkod on 2009-12-09
> **martin69 said:**
> I just found the solution.... we dont need to do nothing with ubuntu, and grub config files. The problem is the win bootloader.
 
After installed ubuntu i make all the updates (update grub to 1.97 version to) and did nothing else.
 
Then with the win7 install dvd, used the repair command line and type:
bootrec /fixmbr                (press enter)
bootrec /fixboot               (press enter)
bootrec /rebuildbcd          (press enter)

after that reboot, and win7 will boot properlly, then i used EasyBCD 2.0 Beta
and make a new boot entry for linux, type grub2 and select the option Grub isnt installed to MBR/bootsector, add entry and reboot.
 
Everything is back to normal.

I don't understand how are you booting ubuntu exactly from what you've written but if you say it's working as you want it, that's good.

---

