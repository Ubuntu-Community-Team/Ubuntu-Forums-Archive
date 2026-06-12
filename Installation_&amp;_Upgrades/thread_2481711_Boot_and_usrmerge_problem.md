---
title: "Boot and usrmerge problem"
date: 2022-12-07
forum: Installation &amp; Upgrades
---

### Post by kvedr on 2022-12-07
Hello,


After upgrading from 20.04 to 22.04.1. problem showed up with usrmerge. I have manually running ```
sudo /usr/lib/usrmerge/convert-usrmerge
``` repaired some errors and stuck with:

> 


Smartmatch is experimental at /usr/lib/usrmerge/convert-usrmerge line 172
not a dynamic executable 

FATAL ERROR:

Can't close(GLOB(0x55f5127f58e0)) filehandle: '' at
/usr/lib/usrmerge/convert-usrmerge line 193

You can try correcting the errors reported and running again
/usr/lib/usrmerge/convert-usrmerge until it will complete without errors.
Do not install or update other Debian packages until the program
has been run successfully.



Later I have accidently install updates which now prevent system from booting:

> Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I have used live-CD  and ran Boot-Repair:

```
[COLOR=#111111][FONT=monospace]boot-repair-4ppa203                                              [/FONT][/COLOR][COLOR=#666666][FONT=monospace][[/FONT][/COLOR][COLOR=#111111][FONT=monospace]20221207_0851[/FONT][/COLOR][COLOR=#666666][FONT=monospace]][/FONT][/COLOR]
[COLOR=#666666]==============================[/COLOR] Boot Info [COLOR=#B8860B]Summary[/COLOR] [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/nvme0n1 and looks at sector 
    [COLOR=#666666]1[/COLOR] of the same hard drive [COLOR=#AA22FF]**for**[/COLOR] core.img. core.img is at this location and 
    looks [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos1[COLOR=#666666])[/COLOR]/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR][COLOR=#666666]5[/COLOR].00 and higher[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda.

nvme0n1p1: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu [COLOR=#666666]22[/COLOR].04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

nvme0n1p2: _____________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

nvme0n1p5: _____________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX [COLOR=#666666]6[/COLOR].04
    Boot sector info:  Syslinux looks at sector [COLOR=#666666]32800[/COLOR] of /dev/sda1 [COLOR=#AA22FF]**for**[/COLOR] its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /efi/BOOT/mmx64.efi /ldlinux.sys


[COLOR=#666666]================================[/COLOR] [COLOR=#666666]1[/COLOR] OS [COLOR=#B8860B]detected[/COLOR] [COLOR=#666666]=================================[/COLOR]

OS#1:   Ubuntu [COLOR=#666666]22[/COLOR].04.1 LTS on [COLOR=#B8860B]nvme0n1p1[/COLOR]

[COLOR=#666666]================================[/COLOR] Host/Hardware [COLOR=#666666]=================================[/COLOR]

CPU architecture: [COLOR=#666666]64[/COLOR]-bit
Video: HD Graphics [COLOR=#666666]620[/COLOR] GM108M [COLOR=#666666][[/COLOR]GeForce 940MX[COLOR=#666666]][/COLOR] from Intel Corporation NVIDIA Corporation
Live-session OS is Ubuntu [COLOR=#666666]64[/COLOR]-bit [COLOR=#666666]([/COLOR]Ubuntu [COLOR=#666666]20[/COLOR].04 LTS, focal, x86_64[COLOR=#666666])[/COLOR]

[COLOR=#666666]=====================================[/COLOR] [COLOR=#B8860B]UEFI[/COLOR] [COLOR=#666666]=====================================[/COLOR]

BIOS/UEFI firmware: N1VET44W [COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR].34 [COLOR=#666666])[/COLOR] from LENOVO
The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode [COLOR=#666666]([/COLOR]not in EFI mode[COLOR=#666666])[/COLOR].

[COLOR=#666666]=============================[/COLOR] Drive/Partition [COLOR=#B8860B]Info[/COLOR] [COLOR=#666666]=============================[/COLOR]

Disks info: ____________________________________________________________________

nvme0n1    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    [COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

nvme0n1p1    : is-os,    [COLOR=#666666]64[/COLOR], apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ng,    update-grub,    farbios

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

nvme0n1p1    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]3[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

nvme0n1p1    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1

fdisk -l [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ___________________________________________________________

Disk nvme0n1: [COLOR=#666666]476[/COLOR].96 GiB, [COLOR=#666666]512110190592[/COLOR] bytes, [COLOR=#666666]1000215216[/COLOR] sectors
Disk identifier: 0x64e1decc
          Boot     Start        End   Sectors   Size Id Type
nvme0n1p1 *         [COLOR=#666666]2048[/COLOR]  [COLOR=#666666]984469503[/COLOR] [COLOR=#666666]984467456[/COLOR] [COLOR=#666666]469[/COLOR].4G [COLOR=#666666]83[/COLOR] Linux
nvme0n1p2      [COLOR=#666666]984471550[/COLOR] [COLOR=#666666]1000214527[/COLOR]  [COLOR=#666666]15742978[/COLOR]   [COLOR=#666666]7[/COLOR].5G  [COLOR=#666666]5[/COLOR] Extended
nvme0n1p5      [COLOR=#666666]984471552[/COLOR] [COLOR=#666666]1000214527[/COLOR]  [COLOR=#666666]15742976[/COLOR]   [COLOR=#666666]7[/COLOR].5G [COLOR=#666666]82[/COLOR] Linux swap / Solaris
Disk sda: [COLOR=#666666]14[/COLOR].42 GiB, [COLOR=#666666]15472047104[/COLOR] bytes, [COLOR=#666666]30218842[/COLOR] sectors
Disk identifier: 0x0091b37f
      Boot Start      End  Sectors  Size Id Type
sda1  *     [COLOR=#666666]2048[/COLOR] [COLOR=#666666]30218841[/COLOR] [COLOR=#666666]30216794[/COLOR] [COLOR=#666666]14[/COLOR].4G  c W95 FAT32 [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]

parted -lm [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _________________________________________________________

sda:15.5GB:scsi:512:512:msdos:Kingston DataTraveler [COLOR=#666666]3[/COLOR].0:;
[COLOR=#666666]1[/COLOR]:1049kB:15.5GB:15.5GB:fat32::boot, lba;
nvme0n1:512GB:nvme:512:512:msdos:SAMSUNG MZVLB512HAJQ-000L7:;
[COLOR=#666666]1[/COLOR]:1049kB:504GB:504GB:ext4::boot;
[COLOR=#666666]2[/COLOR]:504GB:512GB:8060MB:::;
[COLOR=#666666]5[/COLOR]:504GB:512GB:8060MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;

blkid [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                        
&#9492;&#9472;sda1      vfat     A4A4-5360                            0091b37f-01                          UBUNTU 20_0 
nvme0n1                                                                                                    
&#9500;&#9472;nvme0n1p1 ext4     da4fc179-9cef-4d1c-be48-91c82110b9f9 64e1decc-01                                      
&#9500;&#9472;nvme0n1p2                                               64e1decc-02                                      
&#9492;&#9472;nvme0n1p5 swap     c92522c5-0783-4f79-b224-eb73e6c8a771 64e1decc-05                                      

Mount points [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _______________________________________________________

                Avail Use% Mounted on
/dev/nvme0n1p1 [COLOR=#666666]106[/COLOR].7G  [COLOR=#666666]72[/COLOR]% /mnt/boot-sav/nvme0n1p1
/dev/sda1       [COLOR=#666666]11[/COLOR].9G  [COLOR=#666666]18[/COLOR]% /cdrom

Mount options [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: [COLOR=#B8860B]______________________________________________________[/COLOR]


[COLOR=#666666]===================[/COLOR] nvme0n1p1/boot/grub/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]====================[/COLOR]

Ubuntu   da4fc179-9cef-4d1c-be48-91c82110b9f9
Ubuntu, with Linux [COLOR=#666666]5[/COLOR].15.0-56-generic   da4fc179-9cef-4d1c-be48-91c82110b9f9
Ubuntu, with Linux [COLOR=#666666]5[/COLOR].15.0-53-generic   da4fc179-9cef-4d1c-be48-91c82110b9f9
Ubuntu, with Linux [COLOR=#666666]5[/COLOR].15.0-52-generic   da4fc179-9cef-4d1c-be48-91c82110b9f9
Ubuntu, with Linux [COLOR=#666666]5[/COLOR].13.0-52-generic   da4fc179-9cef-4d1c-be48-91c82110b9f9
Ubuntu, with Linux [COLOR=#666666]5[/COLOR].8.0-48-generic   da4fc179-9cef-4d1c-be48-91c82110b9f9
Ubuntu, with Linux [COLOR=#666666]5[/COLOR].4.0-70-generic   da4fc179-9cef-4d1c-be48-91c82110b9f9
Ubuntu, with Linux [COLOR=#666666]5[/COLOR].4.0-67-generic   da4fc179-9cef-4d1c-be48-91c82110b9f9
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#666666]========================[/COLOR] nvme0n1p1/etc/fstab [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]========================[/COLOR]

[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
[COLOR=#008800]*# / was on /dev/nvme0n1p1 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]da4fc179-9cef-4d1c-be48-91c82110b9f9 /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro [COLOR=#666666]0[/COLOR]       [COLOR=#666666]1[/COLOR]
[COLOR=#008800]*# swap was on /dev/nvme0n1p5 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]c92522c5-0783-4f79-b224-eb73e6c8a771 none            swap    sw              [COLOR=#666666]0[/COLOR]       [COLOR=#B8860B]0[/COLOR]

[COLOR=#666666]====================[/COLOR] nvme0n1p1/etc/default/grub [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]=====================[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT_STYLE[/COLOR][COLOR=#666666]=[/COLOR]hidden
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]10[/COLOR]
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]`[/COLOR]lsb_release -i -s [COLOR=#666666]2[/COLOR]> /dev/null [COLOR=#666666]||[/COLOR] [COLOR=#AA22FF]echo[/COLOR] Debian[COLOR=#BB4444]`[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]

[COLOR=#666666]=================[/COLOR] nvme0n1p1: Location of files loaded by [COLOR=#B8860B]Grub[/COLOR] [COLOR=#666666]==================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]
 [COLOR=#666666]344[/COLOR].410652161 [COLOR=#666666]=[/COLOR] [COLOR=#666666]369[/COLOR].808121856  boot/grub/grub.cfg                             [COLOR=#666666]1[/COLOR]
 [COLOR=#666666]204[/COLOR].195899963 [COLOR=#666666]=[/COLOR] [COLOR=#666666]219[/COLOR].253678080  boot/grub/i386-pc/core.img                     [COLOR=#666666]1[/COLOR]
 [COLOR=#666666]447[/COLOR].636734009 [COLOR=#666666]=[/COLOR] [COLOR=#666666]480[/COLOR].646283264  boot/vmlinuz                                   [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]435[/COLOR].518268585 [COLOR=#666666]=[/COLOR] [COLOR=#666666]467[/COLOR].634180096  boot/vmlinuz-5.13.0-52-generic                 [COLOR=#666666]1[/COLOR]
 [COLOR=#666666]410[/COLOR].800788879 [COLOR=#666666]=[/COLOR] [COLOR=#666666]441[/COLOR].093988352  boot/vmlinuz-5.15.0-52-generic                 [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]421[/COLOR].274410248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]452[/COLOR].339953664  boot/vmlinuz-5.15.0-53-generic                 [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]447[/COLOR].636734009 [COLOR=#666666]=[/COLOR] [COLOR=#666666]480[/COLOR].646283264  boot/vmlinuz-5.15.0-56-generic                 [COLOR=#666666]2[/COLOR]
  [COLOR=#666666]57[/COLOR].793174744 [COLOR=#666666]=[/COLOR] [COLOR=#666666]62[/COLOR].054948864   boot/vmlinuz-5.4.0-67-generic                  [COLOR=#666666]1[/COLOR]
 [COLOR=#666666]409[/COLOR].019737244 [COLOR=#666666]=[/COLOR] [COLOR=#666666]439[/COLOR].181598720  boot/vmlinuz-5.4.0-70-generic                  [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]84[/COLOR].447582245 [COLOR=#666666]=[/COLOR] [COLOR=#666666]90[/COLOR].674900992   boot/vmlinuz-5.8.0-48-generic                  [COLOR=#666666]1[/COLOR]
 [COLOR=#666666]421[/COLOR].274410248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]452[/COLOR].339953664  boot/vmlinuz.old                               [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]445[/COLOR].016597748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]477[/COLOR].832933376  boot/initrd.img                                [COLOR=#666666]6[/COLOR]
 [COLOR=#666666]436[/COLOR].981678009 [COLOR=#666666]=[/COLOR] [COLOR=#666666]469[/COLOR].205504000  boot/initrd.img-5.13.0-52-generic              [COLOR=#666666]6[/COLOR]
 [COLOR=#666666]444[/COLOR].938472748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]477[/COLOR].749047296  boot/initrd.img-5.15.0-52-generic              [COLOR=#666666]5[/COLOR]
 [COLOR=#666666]442[/COLOR].704097748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]475[/COLOR].349905408  boot/initrd.img-5.15.0-53-generic              [COLOR=#666666]5[/COLOR]
 [COLOR=#666666]445[/COLOR].016597748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]477[/COLOR].832933376  boot/initrd.img-5.15.0-56-generic              [COLOR=#666666]6[/COLOR]
  [COLOR=#666666]87[/COLOR].392948151 [COLOR=#666666]=[/COLOR] [COLOR=#666666]93[/COLOR].837463552   boot/initrd.img-5.4.0-26-generic               [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]370[/COLOR].243160248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]397[/COLOR].545566208  boot/initrd.img-5.4.0-67-generic               [COLOR=#666666]7[/COLOR]
 [COLOR=#666666]436[/COLOR].188472748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]468[/COLOR].353806336  boot/initrd.img-5.4.0-70-generic               [COLOR=#666666]8[/COLOR]
 [COLOR=#666666]325[/COLOR].711910248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]349[/COLOR].730500608  boot/initrd.img-5.8.0-48-generic               [COLOR=#666666]9[/COLOR]
 [COLOR=#666666]442[/COLOR].704097748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]475[/COLOR].349905408  boot/initrd.img.old                            [COLOR=#B8860B]5[/COLOR]

[COLOR=#666666]===================[/COLOR] nvme0n1p1: ls -l /etc/grub.d/ [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]===================[/COLOR]

-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]18683[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 10_linux
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]43031[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 10_linux_zfs
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]14180[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 20_linux_xen
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]13369[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 30_os-prober
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root  [COLOR=#666666]1372[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] 30_uefi-firmware
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]700[/COLOR] Feb [COLOR=#666666]21[/COLOR]  [COLOR=#666666]2022[/COLOR] 35_fwupd
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]214[/COLOR] Feb  [COLOR=#666666]8[/COLOR]  [COLOR=#666666]2018[/COLOR] 40_custom
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]215[/COLOR] Apr [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2022[/COLOR] [COLOR=#B8860B]41_custom[/COLOR]

[COLOR=#666666]======================[/COLOR] sda1/boot/grub/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]======================[/COLOR]

Ubuntu
Ubuntu [COLOR=#666666]([/COLOR]safe graphics[COLOR=#666666])[/COLOR]
OEM install [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**for**[/COLOR] manufacturers[COLOR=#666666])[/COLOR]
Boot from next volume
UEFI Firmware [COLOR=#B8860B]Settings[/COLOR]

[COLOR=#666666]=========================[/COLOR] sda1/syslinux.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]=========================[/COLOR]

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

[COLOR=#666666]====================[/COLOR] sda1: Location of files loaded by [COLOR=#B8860B]Grub[/COLOR] [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             boot/grub/grub.cfg                             [COLOR=#B8860B]1[/COLOR]

[COLOR=#666666]==================[/COLOR] sda1: Location of files loaded by [COLOR=#B8860B]Syslinux[/COLOR] [COLOR=#666666]==================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             syslinux.cfg                                   [COLOR=#666666]1[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             ldlinux.sys                                    [COLOR=#666666]1[/COLOR]

Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge [COLOR=#666666]([/COLOR]in order to unsign[COLOR=#666666])[/COLOR] and reinstall the grub2 of
nvme0n1p1 into the MBR of nvme0n1.
Grub-efi would not be selected by default because no ESP detected. [COLOR=#111111][FONT=monospace]Additional repair would be performed: unhide-bootmenu-10s
```

Shall I use suggested repair or do i need to change something else before because of unsuccessful merging with usrmerge. Good advice would be welcome.

---

### Post by tea for one on 2022-12-07
Do you have personal data backups?

---

### Post by kvedr on 2022-12-07
Yes I do.

---

### Post by tea for one on 2022-12-07
Splendid - then try the repair offered by boot-repair.

However, I will add some observations:-
You have a modern nvme drive yet your installation is in old-fashioned Legacy mode.
You have msdos partition table with extended partitions.
Boot-repair mentions "The firmware seems EFI-compatible"
You have a live session using 20.04 Bionic yet your installed OS is 22.04 (may be an unsuccessful repair, difficult to be certain)

In your position, I would seriously consider a fresh installation of 22.04LTS in UEFI mode with GPT
Then restore my backup.

---

### Post by kvedr on 2022-12-09
Boot-repair didn't completely delete and further repair grub2 but left me with no grub2, which I had to manually reinstall and recreate. 

System still doesn't boot:

```
[FONT=arial][SIZE=2]Kernel panic - not syncing: No init found.  Try passing init= option  to kernel.[/SIZE][/FONT]
```

---

### Post by tea for one on 2022-12-09
> Do not install or update other Debian packages until the program
has been run successfully. 
> **kvedr said:**
> Later I have accidently install updates which now prevent system from booting
I was hoping that boot-repair may have triggered a successful outcome but obviously it hasn't worked.

As you have data backups, I suggest you install from scratch and restore your files.
Please consider GPT with UEFI mode as I mentioned in post 4.

You should be up and running in a couple of hours.

---

