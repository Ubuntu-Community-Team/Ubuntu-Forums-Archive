---
title: "Boot error after Ubuntu installation"
date: 2017-04-01
forum: Installation &amp; Upgrades
---

### Post by mdob on 2017-04-01
Hello,
I decided to replace Windows with Ubuntu on my Lenovo ideapad 100S laptop and for the past couple of hours I keep trying to resolve issues, but they keep coming. I was hoping that someone here might be able to help me. 
I found a similar topic here:
[https://ubuntuforums.org/showthread.php?t=1252323](https://ubuntuforums.org/showthread.php?t=1252323)
but the solution doesn't seem to be working for me. 

A bit of a background, the laptop is equipped with eMMC 32GB, there is only one partition and I'm not trying to have both Windows and Ubuntu installed, as I mentioned before I am trying to get rid of Windows and install Ubuntu. I managed to create bootable USB using rufus, and after many many issues I managed to do two things:
1. Forced the laptop to boot using that USB (I've done that by moving the USB to the first place on the priority booting list - everything else stayed the same)
2. Change the UEFI BIOS to Legacy BIOS (not sure if this was needed, I was checking many things and someone, somewhere mentioned that it might help, so I did that)

After that I chose an option to replace Windows with Ubuntu, the installation went smoothly and I thought the struggle is over, but after the system restarted, I went back to the installation screen. My first idea was that something was not installed properly, hence I decided to run the installation again, but it didn't change anything. 
The next thing I've done was removing the USB stick and then turning the laptop back on. When I do that, the laptop opens a boot menu, with two options:
1. Windows Boot Manager
2. eMMC Disk: SanDisk iNAND 32GB
At this point it doesn't matter which one I pick, because the result is the same - after a few seconds of having the screen black it returns back to the same boot menu. I am unable to skip that menu, or check any settings here, I can just pick one or the other and press enter. 
It became clear to me that the USB stick has to be plugged in, so I've done that and went to BIOS settings yet again. I was trying to find a way to either change the priority list back to the way it was or to somehow just boot the laptop using the hard drive instead of the USB. I chose the option "Boot from first hard disk", but the result is the error message: "Booting from local disc... Boot error".

The last thing I've done was following the instruction provided in the topic I posted above, where the user **presence1960 **suggests to run the boot info script and then install grub and follow the list of the steps:

> 
[COLOR=#000000][FONT=Ubuntubeta]Do this:[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]1. Boot your computer up with Ubuntu CD[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]2. Open a terminal window or switch to a tty.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]3. Type sudo grub. Should get text of which last line is grub>[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,1)". [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]Use whatever your computer spits out for the following lines.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]5. Type "root (hd1,1)", or whatever your hard disk + boot partition [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]numbers are for Ubuntu.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]6. Type "setup (hd1)", to install GRUB to MBR, or "setup (hd0,1)" or [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]whatever your hard disk + partition # is, to install GRUB to a [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]partition.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]7. Quit grub by typing "quit".[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]8. Reboot and remove the bootable CD.[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]In # 6 use setup (hd1)[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]Reboot and go into BIOS. Set the 500 Gb disk to boot first in hard disk boot order. save the change and continue booting
[/FONT][/COLOR]
I get stuck on step 4, because grub outputs "no such file" error message. To sum up, I honestly have no idea what else I could try, so I would really appreciate any hints. If there is anything I can still check, please let me know. 

Not sure if this is helpful, but here is the output from the boot info script:

```

[FONT=arial]============================= Boot Info Summary: ==============================[/FONT][FONT=arial]=[/FONT]

[FONT=arial] => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.[/FONT]

[FONT=arial]sda1: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       vfat[/FONT]
[FONT=arial]    Boot sector type:  SYSLINUX 6.03[/FONT]
[FONT=arial]    Boot sector info:  Syslinux looks at sector 16392 of /dev/sda1 for its [/FONT]
[FONT=arial]                       second stage. The integrity check of Syslinux failed. [/FONT]
[FONT=arial]                       No errors found in the Boot Parameter Block.[/FONT]
[FONT=arial]    Operating System:  [/FONT]
[FONT=arial]    Boot files:        /boot/grub/grub.cfg /syslinux.cfg [/FONT]
[FONT=arial]                       /efi/BOOT/grubx64.efi /ldlinux.sys[/FONT]

[FONT=arial]============================ Drive/Partition Info: =============================[/FONT]

[FONT=arial]Drive: sda ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]_________[/FONT]
[FONT=arial]Disk /dev/sda: 3.6 GiB, [/FONT][3868430336]("tel:(386)%20843-0336")[FONT=arial] bytes, 7555528 sectors[/FONT]
[FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disklabel type: dos[/FONT]

[FONT=arial]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System[/FONT]

[FONT=arial]/dev/sda1    *          2,048     7,555,527     7,553,480   c W95 FAT32 (LBA)[/FONT]


[FONT=arial]"blkid" output: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]____[/FONT]

[FONT=arial]Device           UUID                          [/FONT][FONT=arial]         TYPE       LABEL[/FONT]

[FONT=arial]/dev/loop0                    [/FONT][FONT=arial]                          squashfs   [/FONT]
[FONT=arial]/dev/mmcblk0                  [/FONT]
[FONT=arial]/dev/mmcblk0p1   9c785595-d5fb-4b9f-96d4-[/FONT][FONT=arial]70f988936b02   ext4       [/FONT]
[FONT=arial]/dev/mmcblk0p5   2650d3a2-cd91-441f-8d26-[/FONT][FONT=arial]3f5aaa1c44f4   swap       [/FONT]
[FONT=arial]/dev/sda1        7A93-3379                     [/FONT][FONT=arial]         vfat       UBUNTU 16_0[/FONT]

[FONT=arial]==============================[/FONT][FONT=arial]== Mount points: ==============================[/FONT][FONT=arial]===[/FONT]

[FONT=arial]Device           Mount_Point              Type       Options[/FONT]

[FONT=arial]/dev/loop0       /rofs                    squashfs   (ro,noatime)[/FONT]
[FONT=arial]/dev/mmcblk0p1   /media/ubuntu/9c785595-d5fb-[/FONT][FONT=arial]4b9f-96d4-70f988936b02 ext4       (rw,nosuid,nodev,relatime,[/FONT][FONT=arial]data=ordered,uhelper=udisks2)[/FONT]
[FONT=arial]/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=[/FONT][FONT=arial]0022,codepage=437,iocharset=[/FONT][FONT=arial]iso8859-1,shortname=mixed,[/FONT][FONT=arial]errors=remount-ro)[/FONT]


[FONT=arial]=========================== sda1/boot/grub/grub.cfg: ===========================[/FONT]

[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]

[FONT=arial]if loadfont /boot/grub/font.pf2 ; then[/FONT]
[FONT=arial]    set gfxmode=auto[/FONT]
[FONT=arial]    insmod efi_gop[/FONT]
[FONT=arial]    insmod efi_uga[/FONT]
[FONT=arial]    insmod gfxterm[/FONT]
[FONT=arial]    terminal_output gfxterm[/FONT]
[FONT=arial]fi[/FONT]

[FONT=arial]set menu_color_normal=white/black[/FONT]
[FONT=arial]set menu_color_highlight=black/[/FONT][FONT=arial]light-gray[/FONT]

[FONT=arial]menuentry "Try Ubuntu without installing" {[/FONT]
[FONT=arial]    set gfxpayload=keep[/FONT]
[FONT=arial]    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.[/FONT][FONT=arial]seed boot=casper quiet splash ---[/FONT]
[FONT=arial]    initrd    /casper/initrd.lz[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]menuentry "Install Ubuntu" {[/FONT]
[FONT=arial]    set gfxpayload=keep[/FONT]
[FONT=arial]    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.[/FONT][FONT=arial]seed boot=casper only-ubiquity quiet splash ---[/FONT]
[FONT=arial]    initrd    /casper/initrd.lz[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]menuentry "OEM install (for manufacturers)" {[/FONT]
[FONT=arial]    set gfxpayload=keep[/FONT]
[FONT=arial]    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.[/FONT][FONT=arial]seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---[/FONT]
[FONT=arial]    initrd    /casper/initrd.lz[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]menuentry "Check disc for defects" {[/FONT]
[FONT=arial]    set gfxpayload=keep[/FONT]
[FONT=arial]    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---[/FONT]
[FONT=arial]    initrd    /casper/initrd.lz[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]

[FONT=arial]============================== sda1/syslinux.cfg: ==============================[/FONT]

[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]
[FONT=arial]DEFAULT loadconfig [/FONT]

[FONT=arial]LABEL loadconfig [/FONT]
[FONT=arial]  CONFIG /isolinux/isolinux.cfg [/FONT]
[FONT=arial]  APPEND /isolinux/ [/FONT]
[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]

[FONT=arial]=================== sda1: Location of files loaded by Grub: ====================[/FONT]

[FONT=arial]           GiB - GB             File                          [/FONT][FONT=arial]       Fragment(s)[/FONT]


[FONT=arial]================= sda1: Location of files loaded by Syslinux: ==================[/FONT]

[FONT=arial]           GiB - GB             File                          [/FONT][FONT=arial]       Fragment(s)[/FONT]


[FONT=arial]========= Devices which don't seem to have a corresponding hard drive: =========[/FONT]

[FONT=arial]no block devices found [/FONT]

[FONT=arial]==============================[/FONT][FONT=arial]= StdErr Messages: ==============================[/FONT][FONT=arial]=[/FONT]

[FONT=arial]cat: /tmp/BootInfo-T4vbuVnc/Tmp_[/FONT][FONT=arial]Log: No such file or directory[/FONT]
[FONT=arial]cat: /tmp/BootInfo-T4vbuVnc/Tmp_[/FONT][FONT=arial]Log: No such file or directory[/FONT]
```

Thank you for reading and your assistance!

---

### Post by ajgreeny on 2017-04-01
That thread you linked to above was from 2009 and the version of grub used then was very different from the one used now so it is not surprising that it did not help you.

I do think you may, however, have more luck using UEFI and allowing the machine to install with the defaults, rather than trying to make your own partitions using "Something Else" in the installation procedure.
See [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) and [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for more info on UEFI installations.

I do not use and have little knowledge of SSD disks which is what I assume your ** eMMC Disk: SanDisk iNAND 32GB** is, but there are some known problems with certain SSD NVMe types that can usually be overcome, so a search for NVMe installation problems in the forum may give you some better clues.

---

### Post by oldfred on 2017-04-01
I think your Ideapad is one of the crippled designs using 32 bit UEFI and class 3 UEFI which means no BIOS boot.
That choice was made to make a Windows only system as then Linux did not have 32 bit UEFI. And they wanted it like Apple to be proprietary.

But Linux now has a 32 bit UEFI.
 LENOVO Ideapad 100 Laptop 16.04 Dual Boot 
[https://ubuntuforums.org/showthread.php?t=2336544](https://ubuntuforums.org/showthread.php?t=2336544)
LENOVO Ideapad 100S Laptop  32 bit UEFI bootia32.efi
[https://ubuntuforums.org/showthread.php?t=2350606](https://ubuntuforums.org/showthread.php?t=2350606) 

 Lenovo 110s  My Experience Installing and Using Linux on my Lenovo 110s UEFI settings better support than 100
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394)

---

