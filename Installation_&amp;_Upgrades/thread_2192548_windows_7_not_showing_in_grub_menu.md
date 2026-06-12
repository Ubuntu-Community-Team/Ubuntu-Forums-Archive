---
title: "windows 7 not showing in grub menu"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by jorgebautista on 2013-12-08
Hello everyone, i installed ubuntu 13.10 and i'm happy with it so far, however i still need to use my windows 7 partitions to use specific windows software but i'm not able to boot windows 7. I've tried to use boot repair but i haven't had luck so far.

I hope you guys can help me out, I wouldn't like to install windows again :(

Thank you so much.

```
[COLOR=#000000]Boot Info Script e7fc706 + Boot-Repair extra info      [/COLOR][COLOR=#666666][[/COLOR][COLOR=#000000]Boot-Info 6Nov2013[/COLOR][COLOR=#666666]][/COLOR]

[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    in partition 94 [COLOR=#AA22FF]**for**[/COLOR] .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  FAT32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda7 starts at sector 827746304.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Grub2 [COLOR=#666666]([/COLOR]v1.99-2.00[COLOR=#666666])[/COLOR]
    Boot sector info:  Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the boot sector of sda8 
                       and looks at sector 862232232 of the same hard drive 
                       [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
                       in partition 94 [COLOR=#AA22FF]**for**[/COLOR] .
    Operating System:  Ubuntu 13.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1               2,048    31,746,047    31,744,000  27 Hidden NTFS [COLOR=#666666]([/COLOR]Recovery Environment[COLOR=#666666])[/COLOR]
/dev/sda2          31,746,048    31,950,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          31,950,848   452,483,071   420,532,224   7 NTFS / exFAT / HPFS
/dev/sda4         452,485,118   976,771,071   524,285,954   f W95 Extended [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]
/dev/sda5         452,485,120   810,964,991   358,479,872   7 NTFS / exFAT / HPFS
/dev/sda6         810,967,040   827,744,255    16,777,216  82 Linux swap / Solaris
/dev/sda7    *    827,746,304   828,037,119       290,816  83 Linux
/dev/sda8         828,039,168   976,771,071   148,731,904  83 Linux


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E482898882895FC2                       ntfs       PQSERVICE
/dev/sda2        401EC38F1EC37D02                       ntfs       SYSTEM RESERVED
/dev/sda3        0C64CB3264CB1CF8                       ntfs       ACER
/dev/sda5        B0D2262CD225F6EE                       ntfs       Datos
/dev/sda6        36131b93-704a-4bcd-837a-201cbd7fd562   swap       
/dev/sda7        5314-8790                              vfat       
/dev/sda8        9f9c46bb-6218-413f-9a36-f84164b1b8b8   ext4       
/dev/sr1                                                iso9660    [COLOR=#B8860B]Tigo[/COLOR]

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/sda7        /boot/efi                vfat       [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
/dev/sda8        /                        ext4       [COLOR=#666666]([/COLOR]rw,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sda8/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# DO NOT EDIT THIS FILE*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# It is automatically generated by grub-mkconfig using templates*[/COLOR]
[COLOR=#008800]*# from /etc/grub.d and settings from /etc/default/grub*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/00_header ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -s [COLOR=#B8860B]$prefix[/COLOR]/grubenv [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]have_grubenv[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
load_env
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"0"[/COLOR]

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#BB4444]"${feature_menuentry_id}"[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]menuentry_id_option[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"--id"[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#B8860B]menuentry_id_option[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]export [/COLOR]menuentry_id_option

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${prev_saved_entry}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${prev_saved_entry}"[/COLOR]
  save_env saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]prev_saved_entry[/COLOR][COLOR=#666666]=[/COLOR]
  save_env prev_saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]savedefault [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${chosen}"[/COLOR]
    save_env saved_entry
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]recordfail [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]recordfail[/COLOR][COLOR=#666666]=[/COLOR]1
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -n [COLOR=#BB4444]"${have_grubenv}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]save_env recordfail; [COLOR=#AA22FF]**fi**[/COLOR]; [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]load_video [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_all_video_module[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
insmod all_video
  [COLOR=#AA22FF]**else**[/COLOR]
insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_default_font_path[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]font[/COLOR][COLOR=#666666]=[/COLOR]unicode
[COLOR=#AA22FF]**else**[/COLOR]
insmod part_msdos
insmod ext2
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos8'[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos8  9f9c46bb-6218-413f-9a36-f84164b1b8b8
[COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 9f9c46bb-6218-413f-9a36-f84164b1b8b8
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#B8860B]font[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"/usr/share/grub/unicode.pf2"[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**if **[/COLOR]loadfont [COLOR=#B8860B]$font[/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]auto
  load_video
  insmod gfxterm
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]locale_dir[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]$prefix[/COLOR]/locale
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]lang[/COLOR][COLOR=#666666]=[/COLOR]en_US
  insmod gettext
[COLOR=#AA22FF]**fi**[/COLOR]
terminal_output gfxterm
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] [COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]-1
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/00_header ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/05_debian_theme ###*[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_normal[/COLOR][COLOR=#666666]=[/COLOR]white/black
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_highlight[/COLOR][COLOR=#666666]=[/COLOR]black/light-gray
[COLOR=#AA22FF]**if **[/COLOR]background_color 44,0,30; [COLOR=#AA22FF]**then**[/COLOR]
clear
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/05_debian_theme ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/10_linux ###*[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]gfxmode [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${1}"[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${1}"[/COLOR] [COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"keep"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]vt.handoff[COLOR=#666666]=[/COLOR]7
    [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] ![COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] -e [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    if **[/COLOR]hwmatch [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt 3; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**      if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]match[/COLOR][COLOR=#AA22FF]**}**[/COLOR] [COLOR=#666666]=[/COLOR] 0 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
      [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
      [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**    else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**  else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]export [/COLOR]linux_gfx_mode
menuentry [COLOR=#BB4444]'Ubuntu'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-simple-9f9c46bb-6218-413f-9a36-f84164b1b8b8'[/COLOR] [COLOR=#666666]{[/COLOR]
recordfail
    load_video
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos8'[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos8  9f9c46bb-6218-413f-9a36-f84164b1b8b8
    [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 9f9c46bb-6218-413f-9a36-f84164b1b8b8
    [COLOR=#AA22FF]**fi**[/COLOR]
linux    /boot/vmlinuz-3.11.0-14-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]9f9c46bb-6218-413f-9a36-f84164b1b8b8 ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.11.0-14-generic
[COLOR=#666666]}[/COLOR]
submenu [COLOR=#BB4444]'Advanced options for Ubuntu'[/COLOR] [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-advanced-9f9c46bb-6218-413f-9a36-f84164b1b8b8'[/COLOR] [COLOR=#666666]{[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.11.0-14-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.11.0-14-generic-advanced-9f9c46bb-6218-413f-9a36-f84164b1b8b8'[/COLOR] [COLOR=#666666]{[/COLOR]
    recordfail
        load_video
        gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos8'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos8  9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.11.0-14-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.11.0-14-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]9f9c46bb-6218-413f-9a36-f84164b1b8b8 ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.11.0-14-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.11.0-14-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.11.0-14-generic-recovery-9f9c46bb-6218-413f-9a36-f84164b1b8b8'[/COLOR] [COLOR=#666666]{[/COLOR]
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos8'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos8  9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.11.0-14-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.11.0-14-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]9f9c46bb-6218-413f-9a36-f84164b1b8b8 ro recovery nomodeset 
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.11.0-14-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.11.0-13-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.11.0-13-generic-advanced-9f9c46bb-6218-413f-9a36-f84164b1b8b8'[/COLOR] [COLOR=#666666]{[/COLOR]
    recordfail
        load_video
        gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos8'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos8  9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.11.0-13-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.11.0-13-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]9f9c46bb-6218-413f-9a36-f84164b1b8b8 ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.11.0-13-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.11.0-13-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.11.0-13-generic-recovery-9f9c46bb-6218-413f-9a36-f84164b1b8b8'[/COLOR] [COLOR=#666666]{[/COLOR]
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos8'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos8  9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.11.0-13-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.11.0-13-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]9f9c46bb-6218-413f-9a36-f84164b1b8b8 ro recovery nomodeset 
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.11.0-13-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.11.0-12-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.11.0-12-generic-advanced-9f9c46bb-6218-413f-9a36-f84164b1b8b8'[/COLOR] [COLOR=#666666]{[/COLOR]
    recordfail
        load_video
        gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos8'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos8  9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.11.0-12-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.11.0-12-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]9f9c46bb-6218-413f-9a36-f84164b1b8b8 ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.11.0-12-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.11.0-12-generic-recovery-9f9c46bb-6218-413f-9a36-f84164b1b8b8'[/COLOR] [COLOR=#666666]{[/COLOR]
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos8'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos8 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos8  9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 9f9c46bb-6218-413f-9a36-f84164b1b8b8
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.11.0-12-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.11.0-12-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]9f9c46bb-6218-413f-9a36-f84164b1b8b8 ro recovery nomodeset 
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.11.0-12-generic
    [COLOR=#666666]}[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/10_linux ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_uefi-firmware ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/40_custom ###*[/COLOR]
[COLOR=#008800]*# This file provides an easy way to add custom menu entries.  Simply type the*[/COLOR]
[COLOR=#008800]*# menu entries you want to add after this comment.  Be careful not to change*[/COLOR]
[COLOR=#008800]*# the 'exec tail' line above.*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/40_custom ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/41_custom ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -f  [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]config_directory[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]source[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]config_directory[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/custom.cfg
[COLOR=#AA22FF]**elif**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${config_directory}"[/COLOR] -a -f  [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]source[/COLOR] [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg;
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/41_custom ###*[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]===============================[/COLOR] sda8/etc/fstab: [COLOR=#666666]================================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# /etc/fstab: static file system information.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Use 'blkid' to print the universally unique identifier for a*[/COLOR]
[COLOR=#008800]*# device; this may be used with UUID= as a more robust way to name devices*[/COLOR]
[COLOR=#008800]*# that works even if disks are added and removed. See fstab(5).*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
[COLOR=#008800]*# / was on /dev/sda8 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]9f9c46bb-6218-413f-9a36-f84164b1b8b8 /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro 0       1
[COLOR=#008800]*# /boot/efi was on /dev/sda7 during installation*[/COLOR]
[COLOR=#008800]*#UUID=5314-8790  /boot/efi       vfat    defaults        0       1*[/COLOR]
[COLOR=#008800]*# swap was on /dev/sda6 during installation*[/COLOR]
[COLOR=#008800]*# UUID=ee4889d6-d637-4691-b9c2-dd318e13698d none            swap    sw              0       0*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]36131b93-704a-4bcd-837a-201cbd7fd562 none            swap    sw              0       0
[COLOR=#008800]*#UUID=5314-8790    /boot/efi    vfat    defaults    0    1*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]5314-8790    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

[COLOR=#666666]===================[/COLOR] sda8: Location of files loaded by Grub: [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]


[COLOR=#666666]=========[/COLOR] Devices which don[COLOR=#BB4444]'t seem to have a corresponding hard drive: =========[/COLOR]

[COLOR=#BB4444]sdb [/COLOR]

[COLOR=#BB4444]=============================== StdErr Messages: ===============================[/COLOR]

[COLOR=#BB4444]cat: write error: Broken pipe[/COLOR]
[COLOR=#BB4444]cat: /tmp/BootInfo-kIGZ2Cop/Tmp_Log: No such file or directory[/COLOR]

[COLOR=#BB4444]ADDITIONAL INFORMATION :[/COLOR]
[COLOR=#BB4444]=================== log of boot-repair 2013-12-08__13h41 ===================[/COLOR]
[COLOR=#BB4444]boot-repair version : 3.199~ppa38~saucy[/COLOR]
[COLOR=#BB4444]boot-sav version : 3.199~ppa38~saucy[/COLOR]
[COLOR=#BB4444]glade2script version : 3.2.2~ppa47~saucy[/COLOR]
[COLOR=#BB4444]boot-sav-extra version : 3.199~ppa38~saucy[/COLOR]
[COLOR=#BB4444]boot-repair is executed in installed-session (Ubuntu 13.10, saucy, Ubuntu, x86_64)[/COLOR]
[COLOR=#BB4444]CPU op-mode(s):        32-bit, 64-bit[/COLOR]
[COLOR=#BB4444]BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=9f9c46bb-6218-413f-9a36-f84164b1b8b8 ro quiet splash vt.handoff=7[/COLOR]

[COLOR=#BB4444]=================== os-prober:[/COLOR]
[COLOR=#BB4444]/dev/sda8:The OS now in use - Ubuntu 13.10 CurrentSession:linux[/COLOR]

[COLOR=#BB4444]=================== blkid:[/COLOR]
[COLOR=#BB4444]/dev/sda1: LABEL="PQSERVICE" UUID="E482898882895FC2" TYPE="ntfs"[/COLOR]
[COLOR=#BB4444]/dev/sda2: LABEL="SYSTEM RESERVED" UUID="401EC38F1EC37D02" TYPE="ntfs"[/COLOR]
[COLOR=#BB4444]/dev/sda3: LABEL="ACER" UUID="0C64CB3264CB1CF8" TYPE="ntfs"[/COLOR]
[COLOR=#BB4444]/dev/sda5: LABEL="Datos" UUID="B0D2262CD225F6EE" TYPE="ntfs"[/COLOR]
[COLOR=#BB4444]/dev/sda6: UUID="36131b93-704a-4bcd-837a-201cbd7fd562" TYPE="swap"[/COLOR]
[COLOR=#BB4444]/dev/sda7: UUID="5314-8790" TYPE="vfat"[/COLOR]
[COLOR=#BB4444]/dev/sda8: UUID="9f9c46bb-6218-413f-9a36-f84164b1b8b8" TYPE="ext4"[/COLOR]
[COLOR=#BB4444]/dev/sr1: LABEL="Tigo" TYPE="iso9660"[/COLOR]


[COLOR=#BB4444]1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.[/COLOR]

[COLOR=#BB4444]Windows not detected by os-prober on sda3.[/COLOR]
[COLOR=#BB4444]Warning: extended partition does not start at a cylinder boundary.[/COLOR]
[COLOR=#BB4444]DOS and Linux will interpret the contents differently.[/COLOR]

[COLOR=#BB4444]=================== /etc/grub.d/ :[/COLOR]
[COLOR=#BB4444]drwxr-xr-x  2 root root     4096 nov 12 18:42 grub.d[/COLOR]
[COLOR=#BB4444]drwxr-xr-x  2 root root     4096 oct 20 22:35 grub.d.bak[/COLOR]
[COLOR=#BB4444]total 68[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root  7850 oct 23 15:44 00_header[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root  5949 ago 15 03:26 05_debian_theme[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 11479 oct 23 15:44 10_linux[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 10258 oct 23 15:44 20_linux_xen[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 11531 oct 23 15:44 30_os-prober[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root  1426 oct 23 15:44 30_uefi-firmware[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root   214 oct 23 15:44 40_custom[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root   216 oct 23 15:44 41_custom[/COLOR]
[COLOR=#BB4444]-rw-r--r-- 1 root root   483 oct 23 15:44 README[/COLOR]




[COLOR=#BB4444]=================== /etc/default/grub :[/COLOR]

[COLOR=#BB4444]# If you change this file, run '[/COLOR]update-grub[COLOR=#BB4444]' afterwards to update[/COLOR]
[COLOR=#BB4444]# /boot/grub/grub.cfg.[/COLOR]
[COLOR=#BB4444]# For full documentation of the options in this file, see:[/COLOR]
[COLOR=#BB4444]#   info -f grub -n '[/COLOR]Simple configuration[COLOR=#BB4444]'[/COLOR]

[COLOR=#BB4444]GRUB_DEFAULT=0[/COLOR]
[COLOR=#BB4444]#GRUB_HIDDEN_TIMEOUT=0[/COLOR]
[COLOR=#BB4444]GRUB_HIDDEN_TIMEOUT_QUIET=true[/COLOR]
[COLOR=#BB4444]GRUB_TIMEOUT=10[/COLOR]
[COLOR=#BB4444]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/COLOR]
[COLOR=#BB4444]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]
[COLOR=#BB4444]GRUB_CMDLINE_LINUX=""[/COLOR]

[COLOR=#BB4444]# Uncomment to enable BadRAM filtering, modify to suit your needs[/COLOR]
[COLOR=#BB4444]# This works with Linux (no patch required) and with any kernel that obtains[/COLOR]
[COLOR=#BB4444]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/COLOR]
[COLOR=#BB4444]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/COLOR]

[COLOR=#BB4444]# Uncomment to disable graphical terminal (grub-pc only)[/COLOR]
[COLOR=#BB4444]#GRUB_TERMINAL=console[/COLOR]

[COLOR=#BB4444]# The resolution used on graphical terminal[/COLOR]
[COLOR=#BB4444]# note that you can use only modes which your graphic card supports via VBE[/COLOR]
[COLOR=#BB4444]# you can see them in real GRUB with the command `vbeinfo'[/COLOR]
[COLOR=#008800]*#GRUB_GFXMODE=640x480*[/COLOR]

[COLOR=#008800]*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]

[COLOR=#008800]*# Uncomment to disable generation of recovery mode menu entries*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]

[COLOR=#008800]*# Uncomment to get a beep at grub start*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]



/boot/efi detected in the fstab of sda8: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]5314-8790     [COLOR=#666666]([/COLOR]sda7[COLOR=#666666])[/COLOR]
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi
ls /sys/firmware/efi/vars : Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c,Time-470733de-df43-448b-8b45-4eeb0df8c812,System-e947fcf9-dd01-4965-b808-32a7b6815657,SmmS3NvsData-8983fd2d-113c-4e2b-8f47-0abfeb20a41a,SMBIOSMEMSIZE-c3eeae98-23bf-412b-ab60-efcbb48e1534,SMBIOSLEN-c3eeae98-23bf-412b-ab60-efcbb48e1534,SMBIOSELOGNUMBER-c3eeae98-23bf-412b-ab60-efcbb48e1534,SMBIOSELOG000-c3eeae98-23bf-412b-ab60-efcbb48e1534,Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,ProtectedBootOptions-8be4df61-93ca-11d2-aa0d-00e098032b8c,PreDefinedBootOptions-8be4df61-93ca-11d2-aa0d-00e098032b8c,PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c,PbaStatusVar-0ec1a7f5-4904-40a0-8eab-4bcc4666da45,OpromDevicePath-8be4df61-93ca-11d2-aa0d-00e098032b8c,OilSystemConfig-3e4794ab-aa64-4619-a8d6-2a1803ed8efe,new_var,MTC-eb704011-1402-11d3-8e77-00a0c969723b,MemoryTypeInformationBackup-4c19049f-4137-4dd3-9c10-8b97a83ffdfa,MemoryTypeInformation-4c19049f-4137-4dd3-9c10-8b97a83ffdfa,LastBootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c,Key0003-8be4df61-93ca-11d2-aa0d-00e098032b8c,Key0002-8be4df61-93ca-11d2-aa0d-00e098032b8c,Key0001-8be4df61-93ca-11d2-aa0d-00e098032b8c,Key0000-8be4df61-93ca-11d2-aa0d-00e098032b8c,HDDPWD-8be4df61-93ca-11d2-aa0d-00e098032b8c,ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ErrOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,DIAGSPLSHSCRN-8be4df61-93ca-11d2-aa0d-00e098032b8c,del_var,ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOrderDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOptionSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0009-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0008-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0007-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0006-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0005-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0004-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0003-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0009-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0008-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0007-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0005-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0004-8be4df61-93ca-11d2-aa0d-00e098032b8c,AmdSetup-3a997502-647a-4c82-998e-52ef9486a247,AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e,AcerRuntimePassword-0997fb62-c849-4d91-9266-05333bc55ce7,AcerD2d-8be4df61-93ca-11d2-aa0d-00e098032b8c,
Please report this message to boot.repair@gmail.com

efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0005,0008,0004,0006,0007,0009
Boot0000  Setup
Boot0001  Boot Menu
Boot0002  Diagnostic Splash
Boot0003  Acer D2D
Boot0004* HDD0: WDC WD5000BPVT-22HXZT3                      ACPI[COLOR=#666666]([/COLOR]a0341d0,0[COLOR=#666666])[/COLOR]PCI[COLOR=#666666]([/COLOR]11,0[COLOR=#666666])[/COLOR]ATAPI[COLOR=#666666]([/COLOR]0,0,0[COLOR=#666666])[/COLOR]..bYVD.A...O.*..
Boot0005* ATAPI CDROM: HL-DT-STDVDRAM GT32N                        ACPI[COLOR=#666666]([/COLOR]a0341d0,0[COLOR=#666666])[/COLOR]PCI[COLOR=#666666]([/COLOR]11,0[COLOR=#666666])[/COLOR]ATAPI[COLOR=#666666]([/COLOR]1,0,0[COLOR=#666666])[/COLOR]......!N.:^G.V.T
Boot0006* USB FDD:    030a2400d23878bc820f604d8316c068ee79d25b6ff015a28830b543a8b8641009461e49
Boot0007* Network Boot:    030a2400d23878bc820f604d8316c068ee79d25b78a84aaf2b2afc4ea79cf5cc8f3d3803
Boot0008* USB HDD:    030a2400d23878bc820f604d8316c068ee79d25b33e821aaaf33bc4789bd419f88c50803
Boot0009* USB CDROM:    [COLOR=#B8860B]030a2400d23878bc820f604d8316c068ee79d25b86701296aa5a7848b66cd49dd3ba6a55[/COLOR]
[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode [COLOR=#AA22FF]**for **[/COLOR]this installed-session.
SecureBoot maybe enabled. [COLOR=#666666]([/COLOR]maybe sec-boot, Please report this message to boot.repair@gmail.com[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sda8    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sda7    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /boot/efi.

sda    : not-GPT,    BIOSboot-not-needed,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA WDC WD5000BPVT-2 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 500GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  16.3GB  16.3GB  primary   ntfs            diag
2      16.3GB  16.4GB  105MB   primary   ntfs
3      16.4GB  232GB   215GB   primary   ntfs
4      232GB   500GB   268GB   extended                  lba
5      232GB   415GB   184GB   logical   ntfs
6      415GB   424GB   8590MB  logical   linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]
7      424GB   424GB   149MB   logical   fat32           boot
8      424GB   500GB   76.2GB  logical   ext4



                                                                          
Warning: Unable to open /dev/sr1 [COLOR=#AA22FF]read[/COLOR]-write [COLOR=#666666]([/COLOR]Read-only file system[COLOR=#666666])[/COLOR].  /dev/sr1
has been opened [COLOR=#AA22FF]read[/COLOR]-only.

                                                                          
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.

[COLOR=#666666]===================[/COLOR] parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA WDC WD5000BPVT-2;
1:1049kB:16.3GB:16.3GB:ntfs::diag;
2:16.3GB:16.4GB:105MB:ntfs::;
3:16.4GB:232GB:215GB:ntfs::;
4:232GB:500GB:268GB:::lba;
5:232GB:415GB:184GB:ntfs::;
6:415GB:424GB:8590MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;
7:424GB:424GB:149MB:fat32::boot;
8:424GB:500GB:76.2GB:ext4::;


                                                                          
Warning: Unable to open /dev/sr1 [COLOR=#AA22FF]read[/COLOR]-write [COLOR=#666666]([/COLOR]Read-only file system[COLOR=#666666])[/COLOR].  /dev/sr1
has been opened [COLOR=#AA22FF]read[/COLOR]-only.

                                                                          
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.


[COLOR=#666666]===================[/COLOR] mount:
/dev/sda8 on / [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /sys/fs/cgroup [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/firmware/efi/efivars [COLOR=#AA22FF]type [/COLOR]efivarfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
none on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]5242880[COLOR=#666666])[/COLOR]
none on /run/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/user [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]104857600,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
none on /sys/fs/pstore [COLOR=#AA22FF]type [/COLOR]pstore [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
/dev/sda7 on /boot/efi [COLOR=#AA22FF]type [/COLOR]vfat [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
systemd on /sys/fs/cgroup/systemd [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,none,name[COLOR=#666666]=[/COLOR]systemd[COLOR=#666666])[/COLOR]
gvfsd-fuse on /run/user/1000/gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfsd-fuse [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]jorge[COLOR=#666666])[/COLOR]
/dev/sda1 on /mnt/boot-sav/sda1 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sda2 on /mnt/boot-sav/sda2 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sda3 on /mnt/boot-sav/sda3 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sda5 on /mnt/boot-sav/sda5 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 size slaves stat subsystem trace uevent
/sys/block/sdb [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sdb serial sg0 sg1 sg2 sg3 shm snapshot snd sr0 sr1 stderr stdin stdout uhid uinput urandom v4l vboxdrv vboxnetctl vboxusb vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control
ls /mnt/boot-sav/sda1/1:
ls /mnt/boot-sav/sda1: AcerBoot
boot
bootmgr
d2d
EFI
Factory
ImageInfo.dat
logs
LPCD.DAT
LPCD.ini
napp
napp.dat
nappx64
PreD2D.bat
PreNAPP.bat
RCD.DAT
sources
SWBOMPN.ini
SystemCD.dat
System Volume Information
WimTemp
WNAPP.in0
WNAPP.ini
WPatchProgress.ini  . Please report this message to boot.repair@gmail.com

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 5f e4 01 00 00 00 00  |........._......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  c2 5f 89 82 88 89 82 e4  |........._......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 5f 01 90 90 66 60 1e  |[COLOR=#666666]([/COLOR]........_...f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 [COLOR=#AA22FF]cd  [/COLOR]10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk [COLOR=#AA22FF]read [/COLOR]error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 e4 01  |........?....h..|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  02 7d c3 1e 8f c3 1e 40  |.........[COLOR=#666666]}[/COLOR].....@|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 5f 01 90 90 66 60 1e  |[COLOR=#666666]([/COLOR]........_...f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 [COLOR=#AA22FF]cd  [/COLOR]10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk [COLOR=#AA22FF]read [/COLOR]error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 e7 01  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff cf 10 19 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  f8 1c cb 64 32 cb 64 0c  |...........d2.d.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 fe 01 90 90 66 60 1e  |.............f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 [COLOR=#AA22FF]cd [/COLOR]10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk [COLOR=#AA22FF]read [/COLOR]error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff f7 5d 15 00 00 00 00  |..........[COLOR=#666666]][/COLOR].....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  ee f6 25 d2 2c 26 d2 b0  |..........%.,&..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 5f 01 90 90 66 60 1e  |[COLOR=#666666]([/COLOR]........_...f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 [COLOR=#AA22FF]cd  [/COLOR]10 eb f2 c3 0d 0a 45 72  |t.............Er|
00000190  72 6f 72 20 64 65 20 64  69 73 63 6f 00 0d 0a 46  |ror de disco...F|
000001a0  61 6c 74 61 20 62 6f 6f  74 6d 67 72 00 0d 0a 42  |alta bootmgr...B|
000001b0  6f 6f 74 6d 67 72 20 63  6f 6d 70 72 69 6d 69 64  |ootmgr comprimid|
000001c0  6f 00 0d 0a 50 72 65 73  2e 20 43 74 72 6c 2b 41  |o...Pres. Ctrl+A|
000001d0  6c 74 2b 53 75 70 72 20  70 61 72 61 20 72 65 69  |lt+Supr para rei|
000001e0  6e 69 63 69 61 72 0d 0a  00 6c 20 74 6f 20 72 65  |niciar...l to re|
000001f0  73 74 61 72 74 0d 0a 00  8c 9d ad c2 00 00 55 aa  |start.........U.|
00000200
ls /boot/efi/1:

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda7
00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 01 20 00  |.X.mkdosfs.... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 70 04 00 bd 08 00 00  00 00 00 00 02 00 00 00  |.p..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 90 87 14 53 4e  4f 20 4e 41 4d 45 20 20  |..[COLOR=#666666])[/COLOR]...SNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 [COLOR=#AA22FF]cd [/COLOR]10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 [COLOR=#AA22FF]cd [/COLOR]16 [COLOR=#AA22FF]cd [/COLOR]19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda8      ext4       70G   25G   42G  37% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  1.7G   12K  1.7G   1% /dev
tmpfs          tmpfs     343M  1.3M  342M   1% /run
none           tmpfs     5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs     1.7G  312K  1.7G   1% /run/shm
none           tmpfs     100M   32K  100M   1% /run/user
/dev/sda7      vfat      140M  1.6M  139M   2% /boot/efi
/dev/sda1      fuseblk    16G   15G  809M  95% /mnt/boot-sav/sda1
/dev/sda2      fuseblk   100M   25M   76M  25% /mnt/boot-sav/sda2
/dev/sda3      fuseblk   201G  155G   47G  77% /mnt/boot-sav/sda3
/dev/sda5      fuseblk   171G  130G   42G  76% /mnt/boot-sav/sda5

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes
Disk identifier: 0xa8ddeb86

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    31746047    15872000   27  Hidden NTFS WinRE
/dev/sda2        31746048    31950847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        31950848   452483071   210266112    7  HPFS/NTFS/exFAT
/dev/sda4       452485118   976771071   262142977    f  W95 Ext'd [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]
Partition 4 does not start on physical sector boundary.
/dev/sda5       452485120   810964991   179239936    7  HPFS/NTFS/exFAT
/dev/sda6       810967040   827744255     8388608   82  Linux swap / Solaris
/dev/sda7   *   827746304   828037119      145408   83  Linux
/dev/sda8       828039168   976771071    74365952   83  [COLOR=#B8860B]Linux[/COLOR]


[COLOR=#666666]===================[/COLOR] Final advice in [COLOR=#AA22FF]**case **[/COLOR]of recommended repair


The boot files of [COLOR=#666666][[/COLOR]The OS now in use - Ubuntu 13.10[COLOR=#666666]][/COLOR] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition [COLOR=#666666]([/COLOR]EXT4, >200MB, start of the disk[COLOR=#666666])[/COLOR]. This can be performed via tools such as gParted. Then [COLOR=#AA22FF]**select **[/COLOR]this partition via the [COLOR=#666666][[/COLOR]Separate /boot partition:[COLOR=#666666]][/COLOR] option of [COLOR=#666666][[/COLOR]Boot Repair[COLOR=#666666]][/COLOR]. [COLOR=#666666]([/COLOR]https://help.ubuntu.com/community/BootPartition[COLOR=#666666])[/COLOR]

[COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair
This setting would purge [COLOR=#666666]([/COLOR]in order to fix packages[COLOR=#666666])[/COLOR] and reinstall the grub2 of sda8 into the MBR of sda.
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s

[COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.


 [COLOR=#000000]No change has been performed on your computer.[/COLOR]
```


-Jorge

---

### Post by oldfred on 2013-12-08
It looks like you have a newer system with a UEFI/BIOS based motherboard. But Windows is installed in BIOS boot mode on a MBR(msdos) partitioned drive.
It looks like the Ubuntu installer installed in UEFI boot mode on a MBR drive which I thought does not work. But you also now have grub in the MBR and I assume that is how you really are booting.

You do need to be consistently booting in BIOS/CSM/Legacy mode. Ubuntu installer offers both UEFI and BIOS modes to boot and installs in the mode you boot with. But it should not install to a MBR drive. Sounds like a bug.

I suggest the recommended repair of a purge and reinstall of grub to the MBR. Then you will not have grub-efi but grub-pc and not conflicts.
A reinstall should run this and find your Windows install but does not work correctly with mixed UEFI & BIOS boot modes.
If Windows still not in grub menu after Boot-Repair try this:
sudo update-grub

If not post the link to a new copy of BootInfo report. Better to use link than post the entire report here.

---

