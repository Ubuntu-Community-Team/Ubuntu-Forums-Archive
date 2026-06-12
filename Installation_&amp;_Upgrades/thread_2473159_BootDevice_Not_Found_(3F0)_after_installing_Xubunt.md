---
title: "BootDevice Not Found (3F0) after installing Xubuntu"
date: 2022-03-25
forum: Installation &amp; Upgrades
---

### Post by peyre on 2022-03-25
I'm trying to install Xubuntu 21.10 on an HP EliteBook Folio 1040 G2.  I've installed Xubuntu many times before, just not on this model.  I made an install drive using the Startup Drive utility on an existing Xubuntu machine (I didn't just copy the ISO to a flash drive).  I fired up the new machine, ran through the Xubuntu installation, telling it to Erase the disk and install Xubuntu--I didn't customize the partitions or anything.  Everything looked normal, but when it says it's done and I tell it to go ahead and reboot, it tells me there's no operating system present.  I've tried several different settings in the UEFI, but currently:

**SecureBoot** is **off **and **Boot Mode **is set to **Legacy**.
The **Legacy Boot Order** has Notebook Hard Drive at the top.

I reinstalled from scratch again after setting those settings, of course.  On reboot after the install, I get the following nonsense (I'm not sure what genius thought backslashes would work in a URL, but that's all right):

> BootDevice Not Found

Please install an operating system on your hard disk.

Hard Disk - (3F0)

F2 System Diagnostics

For more information, please visit: [www.hp.com\go\techcenter\startup](www.hp.com\go\techcenter\startup)

This is one of our standard models in the office, so I tried with another, and it does the same thing--so it's not something wrong with this specific machine.

It also does the same thing if I burn the ISO to a DVD and run the installation from it using a USB optical drive.

---

### Post by DuckHook on 2022-03-25
So, it's an NVME SSD. If the drive is too new, the kernel will not have the driver baked in yet. This seems to be happening more often these days.

Can you see it if you boot from a LiveUSB? If so, then this indicates that a modular driver is available but probably didn't load post install because the system had trouble scanning for it.

TBH I'm out of my depth here, so I can't provide you much guidance. I've only recently started dealing with NVME drives so they are new gadgets to me. I do know that they require different utilities and some of the old standbys&#8212;utilities like hddtemp and smartmontools&#8212;don't work with them. It wouldn't surprise me if kernel modules suffer indigestion too.

---

### Post by peyre on 2022-03-25
These machines are from 2015; they're not super-new.  Also they're M.2 form factor, but not NVME.

:(  I *was* booting from a live USB, the one created by the Startup Disk utility.

---

### Post by oldfred on 2022-03-25
If from 2015 and supports M.2 it will be UEFI hardware.
You may be better with an UEFI install, but BIOS should work.

Many with HP need updates to latest UEFI/BIOS and if SSD, updates to SSD firmware.
Boot order with HP can only be changed in UEFI settings, not UEFI boot menu.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by peyre on 2022-03-28
I just checked the BIOS version, and it's running the latest available on HP Support's site (01.19 Rev.A from May 2020).

Maybe I wasn't clear about it, but I left the UEFI settings on when I tried it the first time.  I've tried both ways.  With UEFI on, it starts up, shows the HP logo, then a black screen saying only "Reset System" in the top left, then reboots.

I'll try the Bootinfo thing.

---

### Post by peyre on 2022-03-28
Ok, here's the Bootinfo summary.  I've had a devil of a time with these, since after a few reboots with that "Reset System" message, the computer refuses to turn back on.

```
boot-repair-4ppa125                                              [20220328_2205]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 21.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32784 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


================================ 1 OS detected =================================

OS#1:   Ubuntu 21.10 on sda2

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.

efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0003,0002,0001,0000
Boot0000*     HD(2,GPT,5ae77c4b-3c77-4f2c-b3b0-6e7d2a8b33fd,0xfa000,0x31800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot0001* Windows Boot Manager    HD(2,GPT,5ae77c4b-3c77-4f2c-b3b0-6e7d2a8b33fd,0xfa000,0x31800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...9................
Boot0002* Windows Boot Manager    HD(2,GPT,5ae77c4b-3c77-4f2c-b3b0-6e7d2a8b33fd,0xfa000,0x31800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...9................
Boot0003* ubuntu    HD(1,GPT,a0233ffb-794e-40f1-9406-a59afcbb37ed,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)

c152ec201c37b6e97bbc2207e49d1271   sda1/BOOT/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/BOOT/mmx64.efi
eca92010a3d461e0f52639d330f3f43d   sda1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/BOOT/BOOTX64.efi


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda2    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: 84CC47D5-F614-4AAF-95DA-239E89DE54CF
        Start       End   Sectors  Size Type
sda1     2048   1050623   1048576  512M EFI System
sda2  1050624 500117503 499066880  238G Linux filesystem
Disk sdb: 7.2 GiB, 7756087296 bytes, 15148608 sectors
Disk identifier: 0x00ca680a
      Boot Start      End  Sectors  Size Id Type
sdb1  *     2048 15148607 15146560  7.2G  c W95 FAT32 (LBA)
Disk zram0: 979.6 MiB, 1027125248 bytes, 250763 sectors
Disk zram1: 979.6 MiB, 1027125248 bytes, 250763 sectors
Disk zram2: 979.6 MiB, 1027125248 bytes, 250763 sectors
Disk zram3: 979.6 MiB, 1027125248 bytes, 250763 sectors
Disk sdc: 1010 MiB, 1059061760 bytes, 2068480 sectors
Disk identifier: 0x500a0dff
      Boot      Start        End    Sectors   Size Id Type
sdc1       1948285285 3650263507 1701978223 811.6G 6e unknown
sdc2                0          0          0     0B 74 unknown
sdc4         28049408   28049848        441 220.5K  0 Empty
Partition table entries are not in disk order.

parted -lm (filtered): _________________________________________________________

sda:256GB:scsi:512:512:gpt:ATA LITEON IT L8T-25:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:256GB:256GB:ext4::;
sdb:7756MB:scsi:512:512:msdos:Kingston DataTraveler 2.0:;
1:1049kB:7756MB:7755MB:fat32::boot, lba;
zram3:1027MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1027MB:1027MB:linux-swap(v1)::;
zram1:1027MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1027MB:1027MB:linux-swap(v1)::;
zram2:1027MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1027MB:1027MB:linux-swap(v1)::;
zram0:1027MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1027MB:1027MB:linux-swap(v1)::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
â&#8221;&#339;â&#8221;&#8364;sda1 vfat     660A-7D98                            a0233ffb-794e-40f1-9406-a59afcbb37ed             EFI System Partition
â&#8221;&#8221;â&#8221;&#8364;sda2 ext4     c532fd40-5edb-4426-9c59-35d2336b04d6 97b7c1e9-5044-4d83-88e3-da6f8d4e6d45             
sdb                                                                                                   
â&#8221;&#8221;â&#8221;&#8364;sdb1 vfat     44D4-069F                            00ca680a-01                          BOOT-REPAIR 
sdc    vfat     4E93-DC4A                                                                 SILVER1GB   
zram0                                                                                                 
zram1                                                                                                 
zram2                                                                                                 
zram3                                                                                                 

df (filtered): _________________________________________________________________

        Avail Use% Mounted on
sda1    505.8M   1% /mnt/boot-sav/sda1
sda2    212.7G   4% /mnt/boot-sav/sda2
sdb1      6.4G  12% /cdrom
sdc    1004.6M   0% /media/lubuntu/SILVER1GB

Mount options: __________________________________________________________________

sda1   rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sda2   rw,relatime
sdb1   ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sdc    rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid c532fd40-5edb-4426-9c59-35d2336b04d6 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   c532fd40-5edb-4426-9c59-35d2336b04d6
Ubuntu, with Linux 5.13.0-37-generic   c532fd40-5edb-4426-9c59-35d2336b04d6
Ubuntu, with Linux 5.13.0-19-generic   c532fd40-5edb-4426-9c59-35d2336b04d6
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=c532fd40-5edb-4426-9c59-35d2336b04d6 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=660A-7D98  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 100.648674011 = 108.070690816  boot/grub/grub.cfg                             1
   7.627700806 = 8.190181376    boot/vmlinuz                                   1
   5.415035248 = 5.814349824    boot/vmlinuz-5.13.0-19-generic                 2
   7.627700806 = 8.190181376    boot/vmlinuz-5.13.0-37-generic                 1
   5.415035248 = 5.814349824    boot/vmlinuz.old                               2
   8.111351013 = 8.709496832    boot/initrd.img                                1
   7.353462219 = 7.895719936    boot/initrd.img-5.13.0-19-generic              1
   8.111351013 = 8.709496832    boot/initrd.img-5.13.0-37-generic              1
   7.353462219 = 7.895719936    boot/initrd.img.old                            1

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18151 Sep  2  2021 10_linux
-rwxr-xr-x 1 root root 43031 Sep  2  2021 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Sep  2  2021 20_linux_xen
-rwxr-xr-x 1 root root 12059 Sep  2  2021 30_os-prober
-rwxr-xr-x 1 root root  1424 Sep  2  2021 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Sep  2  2021 40_custom
-rwxr-xr-x 1 root root   216 Sep  2  2021 41_custom

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Boot-Repair-Disk session
Boot-Repair-Disk session (failsafe)

========================= sdb1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sdb1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1


=============================== StdErr Messages ================================

File descriptor 63 (pipe:[40216]) leaked on lvs invocation. Parent PID 1788: /bin/bash

Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of
sda2,
using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s  use-standard-efi-file    

Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the Ubuntu 21.10 entry (sda1/efi/****/shim****.efi (**** will be updated in the final message) file) !

```

---

### Post by oldfred on 2022-03-28
Please use code tags for longer terminal or text.
Easy to do with Forum's Go Advanced editor and# icon.

But with Boot-Repair better to post the link it gives to the pastebin site.

Try with UEFI Secure boot off.

HP sometimes wants to only boot Windows by description and we can make a Windows entry that boots Ubuntu.
sudo efibootmgr -v
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Or what video card/chip?
May be a video driver issue.

---

### Post by peyre on 2022-03-29
Sorry for the delay.  The video card shows as an Intel HD Graphics 5500.

Ok, the Secure Boot is off and I'm back to Legacy boot.  I reinstalled from scratch, and once again I'm getting  

> BootDevice Not Found
Please install an operating system on your hard disk.
Hard Disk - (3F0)
F2 System Diagnostics
For more information, please visit: [www.hp.com\go\techcenter\startup](www.hp.com\go\techcenter\startup)

So how do I go about adding those bits of code you're suggesting?  Like, what do I add them to?

---

### Post by oldfred on 2022-03-30
What video card?

You use live installer and run commands from terminal.
With HP, just about everyone has posted the boot order change using efiboomgr does not work. And grub uses efibootmgr to change to make Ubuntu/grub first in boot order. Every other system than HP seems to work with efibootmgr.
To change boot order with HP, they say it works if you go into UEFI settings (not the UEFI boot menu) and change boot order there.

---

### Post by peyre on 2022-03-30
Oh, the video card is
> **peyre said:**
> an Intel HD Graphics 5500.
Or did you mean I should be more specific?  I can try to find out more about it.

I'm not quite with you here on changing the boot order by going into UEFI settings but not the UEFI boot menu.  Do you mean the boot menu I get (on an HP) by pressing F9 on startup?  Or are you referring to the Secure Boot option, or the Boot Mode [Legacy / UEFI Hybrid (With CSM) / UEFI Native (Without CSM) ] ?  If you mean the boot menu, no problem; I've been making my changes in the UEFI (former BIOS).

[https://www.dropbox.com/s/p9wghfclvw7cq6y/SecureBoot2.png?dl=0]("https://www.dropbox.com/s/p9wghfclvw7cq6y/SecureBoot2.png?dl=0")

---

### Post by tea for one on 2022-03-30
For HP machines (during start up/power on):-

F9 - One time boot menu where you can select a device but not change the priority.
F10 - UEFI Settings > System Configuration > UEFI Boot Order > OS Boot Manager 

Your PC may well have a different path in the F10 (UEFI Settings) Menu, but there must be something similar to set a priority boot device.

---

### Post by peyre on 2022-03-30
Um, thanks tea.  I do know about the F9 and F10 options.  I used the UEFI settings (F10) to toggle legacy/secure settings, but cannot get it to boot.  That's the whole problem.

---

### Post by tea for one on 2022-03-30
if you remain stumped with this non-booting Xubuntu and you want to try an alternative approach, have a look at rEFInd.
You can even make a temporary rEFInd bootable USB Flash Drive to see if it helps.
Option 5 here [COLOR="#0000FF"]USB Flash Drive Image File[/COLOR] [https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)

I've used the application on a USB drive (just for fun, I did not have a problem to solve) and it looked to be pretty useful.
You could describe it as an Advanced Portable Boot Assistant.

---

### Post by peyre on 2022-03-30
Thanks.  I downloaded the CD image file and used Rufus to create a bootable flash drive, but get the same (3F0) error.  If I turn the secure boot stuff back on, booting from the flash drive simply tells me Selected boot image did not authenticate.

Sigh.  Maybe I should just give up on this one.

---

### Post by tea for one on 2022-03-30
That's a bit disappointing.

You can use the rEFInd USB to select the UEFI Shell of your PC.
It's a bit cumbersome to boot from there but it should be possible.

I'm not suggesting this to be a long term solution but just to see if the beast will co-operate?

If you try this, you'll need to identify your sda drive - it could be FS0: or FS1:
Then, using [COLOR="#0000FF"]cd[/COLOR] and [COLOR="#0000FF"]ls[/COLOR], you have to navigate down to find [COLOR="#0000FF"]EFI/ubuntu/[/COLOR]
Within the ubuntu directory, there should be a file [COLOR="#0000FF"]shimx64.efi[/COLOR].
Type this in the terminal and hit Enter.

---

### Post by peyre on 2022-03-30
But...I can't get the machine to boot from the flash drive at all.

---

### Post by tea for one on 2022-03-30
Ah- I misunderstood your post 14.
I thought that you had created a rEFInd USB but then failed to find and boot Xubuntu.

I used the instruction on the rEFInd website to make the USB - why not try it?

---

### Post by peyre on 2022-03-30
You mean the instructions from "A USB flash drive image file", using dd to copy the files to the flash drive?  I no longer have a Linux machine to run dd from.  I expect if I copy the files over using my Windows machine, that won't make the flash drive bootable.

---

### Post by tea for one on 2022-03-30
Yes, indeed, I meant the use of dd but I did not realise that you do not have access to a Linux machine.
But you can boot up your Xubuntu installer and use that.

Before you try rEFInd, can you have another look at the options after F9?
Do you have [COLOR="#0000FF"]Boot from EFI File[/COLOR]?

That option should be similar to the UEFI shell.
If the first and only entry is an odd-looking set of letters, brackets and numbers, hit enter.
Then you may see EFI and hit enter
Then ubuntu 
Then [COLOR="#0000FF"]shimx64.efi[/COLOR]

---

### Post by peyre on 2022-03-30
Sure, once I select that I get the following options:
Exit
EFI
System Volume Information
banners
docs
fonts
keys
redind

Selecting EFI, options are:
Exit
.
..
boot
tools

Selecting boot, options are:
Exit
.
..
drivers_aa64
drivers_ia32
drivers_x64
icons
bootaa64.efi
bootia32.efi
boot64.efi

Selecting drivers_x64, my options are
Exit
.
..
btrfs_x64.efi
ext2_x64.efi
ext4_x64.efi
hfs_x64.efi
iso9660.efi
reiserfs_x64.efi

Selecting ext4_x64.efi, I get:
Selected EFI application image is not valid.
Cancel image load.
Continue loading the image.

Selecting Continue, I get
Selected boot image did not authenticate.
Cancel image load.

Going back up to \EFI\boot and selecting bootx64.efi, I get:
Selected boot image did not authenticate.
Cancel image load.

---

### Post by tea for one on 2022-03-31
No indication of EFI/ubuntu/shimx64.efi - I was hoping for some positive signs but not yet.

I re-read the thread and wanted to confirm something with you?
Post 6 - The boot-repair report shows a system installed in UEFI mode with ESP.
Post 8 - I'm back to Legacy boot. I reinstalled from scratch

What is the current position - Legacy or UEFI installation?
I think that I may have misled you with all these UEFI/EFI comments if your latest installed system is Legacy.
Apologies, if that is the position.

---

### Post by peyre on 2022-03-31
Uh oh, the machine's at work and today's a holiday, so I'll have to check that tomorrow.  I've gone back and forth so many times.

---

### Post by peyre on 2022-04-01
Ok, the machine is currently on SecureBoot with UEFI Native.

---

### Post by tea for one on 2022-04-01
> **peyre said:**
> Ok, the machine is currently on SecureBoot with UEFI Native.

Can you disable secure boot and run the boot-repair report again.
It's very surprising that previously there was no sign of the EFI/ubuntu/shimx64.efi given that you report that your installation is in UEFI mode.

---

### Post by peyre on 2022-04-01
:(  I turned off SecureBoot, plugged in the flash drive, used F9 to bring up the boot menu and selected it.  Then it gives the same (3F0) error.

---

### Post by oldfred on 2022-04-01
Try a full cold boot or total power down.
Turn off system, unplug it, remove battery if laptop & press power switch for 10 sec or so to totally drain all power.
Then boot and use correct key to get into UEFI boot menu.

I think you need UEFI Secure boot off. Most say to also have CSM/Legacy/BIOS mode off. Years ago some needed that on.

---

### Post by peyre on 2022-04-01
Ok, I unplugged the battery and held down the power button.  Battery's still unplugged.  I went into UEFI and verified that SecureBoot is still disabled and Boot Menu is set to Legacy.  Then I got out of UEFI, F9ed, selected the flash drive, and I get the same error.

Edit:  Ah, I redid the flash drive, telling Rufus to use **dd** mode rather than what it normally recommends, and it booted successfully.  Here's the log:

```

boot-repair-4ppa125                                              [20220401_2040]

============================== Boot Info Summary ===============================


sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


================================ 0 OS detected =================================


============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)


===================================== UEFI =====================================

This live-session is not in EFI-mode.



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________


Partitions info (1/3): _________________________________________________________


Partitions info (2/3): _________________________________________________________


Partitions info (3/3): _________________________________________________________


fdisk -l (filtered): ___________________________________________________________

Disk sda: 7.2 GiB, 7756087296 bytes, 15148608 sectors
Disk identifier: 0x2c534026
      Boot Start     End Sectors  Size Id Type
sda1  *        0 1802239 1802240  880M  0 Empty
sda2         964    5891    4928  2.4M ef EFI (FAT-12/16/32)
Disk zram0: 979.6 MiB, 1027149824 bytes, 250769 sectors
Disk zram1: 979.6 MiB, 1027149824 bytes, 250769 sectors
Disk zram2: 979.6 MiB, 1027149824 bytes, 250769 sectors
Disk zram3: 979.6 MiB, 1027149824 bytes, 250769 sectors
Disk sdb: 1010 MiB, 1059061760 bytes, 2068480 sectors
Disk identifier: 0x500a0dff
      Boot      Start        End    Sectors   Size Id Type
sdb1       1948285285 3650263507 1701978223 811.6G 6e unknown
sdb2                0          0          0     0B 74 unknown
sdb4         28049408   28049848        441 220.5K  0 Empty
Partition table entries are not in disk order.

parted -lm (filtered): _________________________________________________________

sda:7756MB:scsi:512:512:msdos:Kingston DataTraveler 2.0:;
2:494kB:3017kB:2523kB:::esp;
zram3:1027MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1027MB:1027MB:linux-swap(v1)::;
zram1:1027MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1027MB:1027MB:linux-swap(v1)::;
zram2:1027MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1027MB:1027MB:linux-swap(v1)::;
zram0:1027MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1027MB:1027MB:linux-swap(v1)::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda    iso9660  2020-06-13-00-42-55-00                                                    Boot-Repair-Disk 64bit 
â&#8221;&#339;â&#8221;&#8364;sda1 iso9660  2020-06-13-00-42-55-00               2c534026-01                          Boot-Repair-Disk 64bit 
â&#8221;&#8221;â&#8221;&#8364;sda2 vfat     D055-8513                            2c534026-02                          Boot-Repair-Disk 64bit 
sdb    vfat     4E93-DC4A                                                                 SILVER1GB              
zram0                                                                                                            
zram1                                                                                                            
zram2                                                                                                            
zram3                                                                                                            

df (filtered): _________________________________________________________________

        Avail Use% Mounted on
sda          0 100% /cdrom
sdb    1004.6M   0% /media/lubuntu/SILVER1GB

Mount options: __________________________________________________________________

sda    ro,noatime,nojoliet,check=s,map=n,blocksize=2048
sdb    rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro

====================== sda/boot/grub/grub.cfg (filtered) =======================

Boot-Repair-Disk session
Boot-Repair-Disk session (failsafe)

==================== sda: Location of files loaded by Grub =====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sda

00000000  33 ed 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |3...............|
00000010  90 90 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f3 06 b4 42 eb 15 eb 02  |...t.f.....B....|
00000070  31 c9 5a 51 b4 08 cd 13  5b 0f b6 c6 40 50 83 e1  |1.ZQ....[...@P..|
00000080  3f 51 f7 e1 53 52 50 bb  00 7c b9 04 00 66 a1 b0  |?Q..SRP..|...f..|
00000090  07 e8 44 00 0f 82 80 00  66 40 80 c7 02 e2 f2 66  |..D.....f@.....f|
000000a0  81 3e 40 7c fb c0 78 70  75 09 fa bc ec 7b ea 44  |.>@|..xpu....{.D|
000000b0  7c 00 00 e8 83 00 69 73  6f 6c 69 6e 75 78 2e 62  ||.....isolinux.b|
000000c0  69 6e 20 6d 69 73 73 69  6e 67 20 6f 72 20 63 6f  |in missing or co|
000000d0  72 72 75 70 74 2e 0d 0a  66 60 66 31 d2 66 03 06  |rrupt...f`f1.f..|
000000e0  f8 7b 66 13 16 fc 7b 66  52 66 50 06 53 6a 01 6a  |.{f...{fRfP.Sj.j|
000000f0  10 89 e6 66 f7 36 e8 7b  c0 e4 06 88 e1 88 c5 92  |...f.6.{........|
00000100  f6 36 ee 7b 88 c6 08 e1  41 b8 01 02 8a 16 f2 7b  |.6.{....A......{|
00000110  cd 13 8d 64 10 66 61 c3  e8 1e 00 4f 70 65 72 61  |...d.fa....Opera|
00000120  74 69 6e 67 20 73 79 73  74 65 6d 20 6c 6f 61 64  |ting system load|
00000130  20 65 72 72 6f 72 2e 0d  0a 5e ac b4 0e 8a 3e 62  | error...^....>b|
00000140  04 b3 07 cd 10 3c 0a 75  f1 cd 18 f4 eb fd 00 00  |.....<.u........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  04 17 00 00 00 00 00 00  26 40 53 2c 00 00 80 00  |........&@S,....|
000001c0  01 00 00 3f e0 6f 00 00  00 00 00 80 1b 00 00 fe  |...?.o..........|
000001d0  ff ff ef fe ff ff c4 03  00 00 40 13 00 00 00 00  |..........@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages ================================

File descriptor 63 (pipe:[40143]) leaked on lvs invocation. Parent PID 1697: /bin/bash

Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

```

---

### Post by tea for one on 2022-04-01
```

boot-repair-4ppa125                                              [20220401_2040]

================================ 0 OS detected =================================
      Boot      Start        End    Sectors   Size Id Type
sdb1       1948285285 3650263507 1701978223 811.6G 6e unknown
sdb2                0          0          0     0B 74 unknown
sdb4         28049408   28049848        441 220.5K  0 Empty
Partition table entries are not in disk order.

```
Not wanting to be the bearer of bad news, but there is no sign of Xubuntu.
The boot-repair report from post 6 showed the OS (albeit un-bootable).
Do you know what happened?

---

### Post by peyre on 2022-04-01
No, not sure.  Maybe it's that the last time I installed the OS the machine had SecureBoot turned on, but now it's turned off?

---

