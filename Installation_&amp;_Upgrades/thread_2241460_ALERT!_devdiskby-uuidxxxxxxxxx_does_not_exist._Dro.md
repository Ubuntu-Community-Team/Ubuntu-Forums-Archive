---
title: "ALERT! /dev/disk/by-uuid/xxxxxxxxx does not exist. Dropping to a shell  initramfs:_"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by gor4l on 2014-08-26
Hi gyus, I need your help with these
Few day ago I run in terminal ```
sudo apt-get update
``` on ubuntu 14.04 LTS 64 bits.
After restart I saw

```
udevadm triger is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
Gave up wating for root device. Common problems:
-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/X-X-X-X does not exist.
Dropping to a shell! 

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shel (ash)
Enter `help` for a list of built-in commands.
(initramfs)_
```

```
sudo fsck /dev/sda1fsck from util-linux 2.020.1
e2fsck 1.42.9 (4-Feb-2014)
/dev/sda1:clean, 491701/19054592 files, 27163705/76189184 blocks
```[COLOR=#2E8B57][FONT=Monaco]
[/FONT][/COLOR]
```
GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize

Libparted 2.3
Check and repair file system (ext4) on /dev/sda1  00:18:14    ( SUCCESS )
        
calibrate /dev/sda1  00:00:00    ( SUCCESS )
        
path: /dev/sda1
start: 2048
end: 609515519
size: 609513472 (290.64 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:18:14    ( SUCCESS )
        
e2fsck -f -y -v -C 0 /dev/sda1
        
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information


491701 inodes used (2.58%, out of 19054592)
3868 non-contiguous files (0.8%)
1026 non-contiguous directories (0.2%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 414151/441
27163705 blocks used (35.65%, out of 76189184)
0 bad blocks
3 large files


357576 regular files
39125 directories
57 character device files
25 block device files
0 fifos
48 links
94901 symbolic links (77011 fast symbolic links)
8 sockets
------------
491740 files
e2fsck 1.42.9 (4-Feb-2014)
grow file system to fill the partition  00:00:00    ( SUCCESS )
        
resize2fs -p /dev/sda1
        
resize2fs 1.42.9 (4-Feb-2014)
The filesystem is already 76189184 blocks long. Nothing to do!


========================================
```

I booted liveDVD and after boot-repair done its job, its still the same.
Here is log
```
[COLOR=#000000]Boot Info Script e7fc706 + Boot-Repair extra info      [/COLOR][COLOR=#666666][[/COLOR][COLOR=#000000]Boot-Info 23Dec2013[/COLOR][COLOR=#666666]][/COLOR]

[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    in partition 112 [COLOR=#AA22FF]**for**[/COLOR] .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1    *          2,048   609,515,519   609,513,472  83 Linux
/dev/sda2         609,517,566   625,139,711    15,622,146   5 Extended
/dev/sda5         609,517,568   625,139,711    15,622,144  82 Linux swap / Solaris


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        d558b77e-cff1-4a1c-881c-c99bfe9a735b   ext4       
/dev/sr0                                                iso9660    Ubuntu 14.04.1 LTS [COLOR=#B8860B]amd64[/COLOR]

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/sr0         /cdrom                   iso9660    [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sda1/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

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
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${next_entry}"[/COLOR] [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${next_entry}"[/COLOR]
   [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]next_entry[/COLOR][COLOR=#666666]=[/COLOR]
   save_env next_entry
   [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"0"[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

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
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos1'[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos1  d558b77e-cff1-4a1c-881c-c99bfe9a735b
[COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root d558b77e-cff1-4a1c-881c-c99bfe9a735b
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
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] [COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_timeout_style[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout_style[/COLOR][COLOR=#666666]=[/COLOR]menu
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
  [COLOR=#008800]*# Fallback normal timeout code in case the timeout_style feature is*[/COLOR]
  [COLOR=#008800]*# unavailable.*[/COLOR]
  [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
  [COLOR=#AA22FF]**fi**[/COLOR]
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
menuentry [COLOR=#BB4444]'Ubuntu'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-simple-d558b77e-cff1-4a1c-881c-c99bfe9a735b'[/COLOR] [COLOR=#666666]{[/COLOR]
    recordfail
    load_video
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos1'[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos1  d558b77e-cff1-4a1c-881c-c99bfe9a735b
    [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root d558b77e-cff1-4a1c-881c-c99bfe9a735b
    [COLOR=#AA22FF]**fi**[/COLOR]
linux    /boot/vmlinuz-3.13.0-27-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]d558b77e-cff1-4a1c-881c-c99bfe9a735b ro  quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.13.0-27-generic
[COLOR=#666666]}[/COLOR]
submenu [COLOR=#BB4444]'Advanced options for Ubuntu'[/COLOR] [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-advanced-d558b77e-cff1-4a1c-881c-c99bfe9a735b'[/COLOR] [COLOR=#666666]{[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.13.0-27-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.13.0-27-generic-advanced-d558b77e-cff1-4a1c-881c-c99bfe9a735b'[/COLOR] [COLOR=#666666]{[/COLOR]
        recordfail
        load_video
        gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos1'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos1  d558b77e-cff1-4a1c-881c-c99bfe9a735b
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root d558b77e-cff1-4a1c-881c-c99bfe9a735b
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.13.0-27-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.13.0-27-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]d558b77e-cff1-4a1c-881c-c99bfe9a735b ro  quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.13.0-27-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.13.0-27-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.13.0-27-generic-recovery-d558b77e-cff1-4a1c-881c-c99bfe9a735b'[/COLOR] [COLOR=#666666]{[/COLOR]
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos1'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos1  d558b77e-cff1-4a1c-881c-c99bfe9a735b
        [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root d558b77e-cff1-4a1c-881c-c99bfe9a735b
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.13.0-27-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.13.0-27-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]d558b77e-cff1-4a1c-881c-c99bfe9a735b ro recovery nomodeset 
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.13.0-27-generic
    [COLOR=#666666]}[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/10_linux ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_memtest86+ ###*[/COLOR]
menuentry [COLOR=#BB4444]'Memory test (memtest86+)'[/COLOR] [COLOR=#666666]{[/COLOR]
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos1'[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos1  d558b77e-cff1-4a1c-881c-c99bfe9a735b
    [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root d558b77e-cff1-4a1c-881c-c99bfe9a735b
    [COLOR=#AA22FF]**fi**[/COLOR]
knetbsd    /boot/memtest86+.elf
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Memory test (memtest86+, serial console 115200)'[/COLOR] [COLOR=#666666]{[/COLOR]
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos1'[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos1  d558b77e-cff1-4a1c-881c-c99bfe9a735b
    [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root d558b77e-cff1-4a1c-881c-c99bfe9a735b
    [COLOR=#AA22FF]**fi**[/COLOR]
linux16    /boot/memtest86+.bin [COLOR=#B8860B]console[/COLOR][COLOR=#666666]=[/COLOR]ttyS0,115200n8
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/20_memtest86+ ###*[/COLOR]

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

[COLOR=#666666]===============================[/COLOR] sda1/etc/fstab: [COLOR=#666666]================================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# /etc/fstab: static file system information.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Use 'blkid' to print the universally unique identifier for a*[/COLOR]
[COLOR=#008800]*# device; this may be used with UUID= as a more robust way to name devices*[/COLOR]
[COLOR=#008800]*# that works even if disks are added and removed. See fstab(5).*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR=#008800]*# / was on /dev/sda1 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]d558b77e-cff1-4a1c-881c-c99bfe9a735b /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro 0       1
[COLOR=#008800]*# swap was on /dev/sda5 during installation*[/COLOR]
[COLOR=#008800]*#UUID=1ccf2bb7-388f-4956-9710-0a091cdfa085 none            swap    sw              0       0*[/COLOR]
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

[COLOR=#666666]===================[/COLOR] sda1: Location of files loaded by Grub: [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]


[COLOR=#666666]===============================[/COLOR] StdErr Messages: [COLOR=#666666]===============================[/COLOR]

cat: /tmp/BootInfo-SvOf8swp/Tmp_Log: No such file or directory
File descriptor 9 [COLOR=#666666]([/COLOR]/proc/10409/mounts[COLOR=#666666])[/COLOR] leaked on lvscan invocation. Parent PID 17463: bash
File descriptor 63 [COLOR=#666666]([/COLOR]pipe:[COLOR=#666666][[/COLOR]67227[COLOR=#666666]])[/COLOR] leaked on lvscan invocation. Parent PID 17463: bash
  No volume groups found

ADDITIONAL INFORMATION :
[COLOR=#666666]===================[/COLOR] log of boot-repair 2014-08-26__13h39 [COLOR=#666666]===================[/COLOR]
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session [COLOR=#666666]([/COLOR]Ubuntu 14.04.1 LTS, trusty, Ubuntu, x86_64[COLOR=#666666])[/COLOR]
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]:        32-bit, 64-bit
[COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz quiet splash -- maybe-ubiquity

[COLOR=#666666]===================[/COLOR] os-prober:
/dev/sda1:Ubuntu 14.04.1 LTS [COLOR=#666666]([/COLOR]14.04[COLOR=#666666])[/COLOR]:Ubuntu:linux

[COLOR=#666666]===================[/COLOR] blkid:
/dev/sda1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"d558b77e-cff1-4a1c-881c-c99bfe9a735b"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ext4"[/COLOR]
/dev/loop0: [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"squashfs"[/COLOR]
/dev/sr0: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"Ubuntu 14.04.1 LTS amd64"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"iso9660"[/COLOR]


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown [COLOR=#AA22FF]type [/COLOR]OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

[COLOR=#666666]===================[/COLOR] sda1/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Aug 24 20:24 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Apr 11 10:51 00_header
-rwxr-xr-x 1 root root  6058 Apr 10 15:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 Apr 11 10:51 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11 10:51 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12 12:31 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11 10:51 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11 10:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 17  2012 40_custom
-rwxr-xr-x 1 root root   216 Apr 11 10:51 41_custom
-rw-r--r-- 1 root root   483 May 17  2012 [COLOR=#B8860B]README[/COLOR]




[COLOR=#666666]===================[/COLOR] sda1/etc/default/grub :

[COLOR=#008800]*# If you change this file, run 'update-grub' afterwards to update*[/COLOR]
[COLOR=#008800]*# /boot/grub/grub.cfg.*[/COLOR]
[COLOR=#008800]*# For full documentation of the options in this file, see:*[/COLOR]
[COLOR=#008800]*#   info -f grub -n 'Simple configuration'*[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR]0
[COLOR=#B8860B]GRUB_HIDDEN_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR]0
[COLOR=#B8860B]GRUB_HIDDEN_TIMEOUT_QUIET[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]`[/COLOR]lsb_release -i -s 2> /dev/null [COLOR=#666666]||[/COLOR] [COLOR=#AA22FF]echo [/COLOR]Debian[COLOR=#BB4444]`[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]

[COLOR=#008800]*# Uncomment to enable BadRAM filtering, modify to suit your needs*[/COLOR]
[COLOR=#008800]*# This works with Linux (no patch required) and with any kernel that obtains*[/COLOR]
[COLOR=#008800]*# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)*[/COLOR]
[COLOR=#008800]*#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"*[/COLOR]

[COLOR=#008800]*# Uncomment to disable graphical terminal (grub-pc only)*[/COLOR]
[COLOR=#008800]*#GRUB_TERMINAL=console*[/COLOR]

[COLOR=#008800]*# The resolution used on graphical terminal*[/COLOR]
[COLOR=#008800]*# note that you can use only modes which your graphic card supports via VBE*[/COLOR]
[COLOR=#008800]*# you can see them in real GRUB with the command `vbeinfo'*[/COLOR]
[COLOR=#008800]*#GRUB_GFXMODE=640x480*[/COLOR]

[COLOR=#008800]*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]

[COLOR=#008800]*# Uncomment to disable generation of recovery mode menu entries*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]

[COLOR=#008800]*# Uncomment to get a beep at grub start*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]




[COLOR=#666666]===================[/COLOR] [COLOR=#B8860B]sda1recordfail[/COLOR][COLOR=#666666]=[/COLOR]1/grub/grubenv :
[COLOR=#B8860B]recordfail[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]1[/COLOR]



[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ng    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA WDC WD3200BEVT-6 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 320GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
1      1049kB  312GB  312GB   primary   ext4         boot
2      312GB   320GB  7999MB  extended
5      312GB   320GB  7999MB  logical



                                                                          
Warning: Unable to open /dev/sr0 [COLOR=#AA22FF]read[/COLOR]-write [COLOR=#666666]([/COLOR]Read-only file system[COLOR=#666666])[/COLOR].  /dev/sr0
has been opened [COLOR=#AA22FF]read[/COLOR]-only.

                                                                          
Error: Can[COLOR=#BB4444]'t have a partition outside the disk![/COLOR]

[COLOR=#BB4444]=================== parted -lm:[/COLOR]

[COLOR=#BB4444]BYT;[/COLOR]
[COLOR=#BB4444]/dev/sda:320GB:scsi:512:512:msdos:ATA WDC WD3200BEVT-6;[/COLOR]
[COLOR=#BB4444]1:1049kB:312GB:312GB:ext4::boot;[/COLOR]
[COLOR=#BB4444]2:312GB:320GB:7999MB:::;[/COLOR]
[COLOR=#BB4444]5:312GB:320GB:7999MB:::;[/COLOR]



[COLOR=#BB4444]Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0[/COLOR]
[COLOR=#BB4444]has been opened read-only.[/COLOR]


[COLOR=#BB4444]Error: Can'[/COLOR]t have a partition outside the disk!


[COLOR=#666666]===================[/COLOR] mount:
/cow on / [COLOR=#AA22FF]type [/COLOR]overlayfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
/dev/sr0 on /cdrom [COLOR=#AA22FF]type [/COLOR]iso9660 [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/loop0 on /rofs [COLOR=#AA22FF]type [/COLOR]squashfs [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
none on /sys/fs/cgroup [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
tmpfs on /tmp [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]5242880[COLOR=#666666])[/COLOR]
none on /run/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/user [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]104857600,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
none on /sys/fs/pstore [COLOR=#AA22FF]type [/COLOR]pstore [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
systemd on /sys/fs/cgroup/systemd [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,none,name[COLOR=#666666]=[/COLOR]systemd[COLOR=#666666])[/COLOR]
gvfsd-fuse on /run/user/999/gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfsd-fuse [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]ubuntu[COLOR=#666666])[/COLOR]
/dev/sda1 on /mnt/boot-sav/sda1 [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sr0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  agpgart autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd freefall full fuse hpet input kmsg log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  [COLOR=#B8860B]control[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.5G  139M  1.3G  10% /
udev           devtmpfs   1.5G   12K  1.5G   1% /dev
tmpfs          tmpfs      294M  1.2M  293M   1% /run
/dev/sr0       iso9660    981M  981M     0 100% /cdrom
/dev/loop0     squashfs   939M  939M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.5G  1.2M  1.5G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      1.5G   76K  1.5G   1% /run/shm
none           tmpfs      100M   48K  100M   1% /run/user
/dev/sda1      ext4       286G   99G  173G  37% /mnt/boot-sav/sda1

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0xb24aa504

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   609515519   304756736   83  Linux
/dev/sda2       609517566   625139711     7811073    5  Extended
/dev/sda5       609517568   625139711     7811072   82  Linux swap / Solaris


Partition outside the disk detected.

[COLOR=#666666]===================[/COLOR] Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda1 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s


Unhide GRUB boot menu in sda1/etc/default/grub

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [COLOR=#666666][[/COLOR]0300[COLOR=#666666]][/COLOR]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [COLOR=#666666][[/COLOR]8086:2a42[COLOR=#666666]][/COLOR] [COLOR=#666666]([/COLOR]rev 07[COLOR=#666666])[/COLOR]
Subsystem: Hewlett-Packard Company Device [COLOR=#666666][[/COLOR]103c:3072[COLOR=#666666]][/COLOR]
Kernel driver in use: i915
00:02.1 Display controller [COLOR=#666666][[/COLOR]0380[COLOR=#666666]][/COLOR]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [COLOR=#666666][[/COLOR]8086:2a43[COLOR=#666666]][/COLOR] [COLOR=#666666]([/COLOR]rev 07[COLOR=#666666])[/COLOR]
*******

grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking [COLOR=#AA22FF]**for**[/COLOR] /sys/firmware/efi ...
grub-install: info: ... not found. Looking [COLOR=#AA22FF]**for**[/COLOR] /proc/device-tree ...
grub-install: info: ... not found.
Installing [COLOR=#AA22FF]**for **[/COLOR]i386-pc platform.
grub-install: error: install device isn't specified.
,.

Reinstall the GRUB of sda1 into the MBR of sda
Installing [COLOR=#AA22FF]**for **[/COLOR]i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: [COLOR=#AA22FF]exit [/COLOR]code of grub-install /dev/sda:0

chroot /mnt/boot-sav/sda1 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

Boot successfully repaired.
 [COLOR=#000000]You can now reboot your computer.[/COLOR]
```

Can someone help ?

---

### Post by Bashing-om on 2014-08-26
gor4l; Hi !

There is a declaration for a 'swap' partition in /etc/fstab, however, I do not see that the partition exists per the output of 'fdisk'.

As it is listed in /etc/fstab as:
> 
/dev/mapper/cryptswap1 none swap sw 0 0

Maybe comment out that entry ( from the liveDVD ) and see then if the system will boot up ?
If indeed a encrypted 'swap' does exist - that 'fdisk' can not see - will require additional measures.
Else if a 'swap' partition is to be enabled, will take additional measures.

[INDENT][INDENT]one step at a time
[INDENT][INDENT][INDENT][INDENT]gets to the end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gor4l on 2014-08-26
Hi Bashing-om.
Here is my as you suggested fstab file
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d558b77e-cff1-4a1c-881c-c99bfe9a735b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=1ccf2bb7-388f-4956-9710-0a091cdfa085 none            swap    #sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
```

Be right back.

---

### Post by gor4l on 2014-08-26
Nope this not work.
even if I wait some time in GRUB and then hit enter

when I type exit, initramfs says:
```
[COLOR=#000000][FONT=Ubuntu Mono]Gave up wating for root device. Common problems:[/FONT][/COLOR]-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/X-X-X-X does not exist.
Dropping to a shell! 

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shel (ash)
Enter `help` for a list of built-in commands.
(initramfs)_
```

why he can`t see sda1 ? and liveDVD can ?
and what means these line 
boots args cat /proc/cmdline
and
missing modules cat /proc/modules; ls /dev ?
and could someone explain me where I am, because I don`t know where I stand right now ...

---

### Post by Bashing-om on 2014-08-26
gor4l; Well.

Yes, the edit to /etc/fstab is done as I think correctly.
Now it appears to me that the boot code is corrupt, as you have done a file system check on the '/' partition, and no fault found.

OK, did you encrypt the /home directory ? As doing so will also encrypt the swap partition. Be aware I know nothing of encryption or what would be entailed in the boot process.

IF encryption is not a part of this picture, how about (RE-)installing grub to also take care of the boot code ? 


[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by gor4l on 2014-08-26
I think /home was encrypted ... (yes I think as far I can remember I encrypt /home when installing ubuntu 14.04)

---

### Post by Bashing-om on 2014-08-26
gor4l; shucks !

In the case of encryption, I have no idea what we can do.
Others will have to chime in here - that do have some experience with encryption.

[INDENT][INDENT]sorry
[INDENT][INDENT][INDENT][INDENT]exit stage left
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gor4l on 2014-08-26
How to check if partition is encrypted ?

---

### Post by Anakinholland on 2014-08-26
Don't know how to solve your issue right off the bat, but you can use various command for that.

lsblk does a list of block-devices (HDD and USB drives/sticks), the ones marked TYPE crypt are encrypted. Using my just installed machine as reference:

```
 root@schuldiner:~# lsblk
NAME                    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                       8:0    0 167,7G  0 disk  
&#9500;&#9472;sda1                    8:1    0   476M  0 part  /boot/efi
&#9500;&#9472;sda2                    8:2    0   238M  0 part  /boot
&#9500;&#9472;sda3                    8:3    0     1K  0 part  
&#9500;&#9472;sda5                    8:5    0  18,6G  0 part  
&#9474; &#9492;&#9472;sda5_crypt (dm-0)   252:0    0  18,6G  0 crypt /
&#9500;&#9472;sda6                    8:6    0    14G  0 part  
&#9474; &#9492;&#9472;sda6_crypt (dm-2)   252:2    0    14G  0 crypt /home
&#9500;&#9472;sda7                    8:7    0 125,7G  0 part  
&#9474; &#9492;&#9472;sda7_crypt (dm-3)   252:3    0 125,7G  0 crypt /virtual
&#9492;&#9472;sda8                    8:8    0   7,5G  0 part  
  &#9492;&#9472;sda8_crypt (dm-1)   252:1    0   7,5G  0 crypt [SWAP]

```

The fstab:

```
 root@schuldiner:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/sda5_crypt /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=7bd6113e-c8ad-4999-9e08-84ae5a43378a /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=CBDC-9CA6  /boot/efi       vfat    defaults        0       1
/dev/mapper/sda6_crypt /home           ext4    defaults        0       2
/dev/mapper/sda7_crypt /virtual        ext4    defaults        0       2
/dev/mapper/sda8_crypt none            swap    sw              0       0
```

However, the by-UUID is related to /etc/crypttab:

```
 root@schuldiner:~# cat /etc/crypttab 
sda5_crypt UUID=e218387f-380b-4e7a-9a45-740f8cf966a1 none luks,discard
sda6_crypt UUID=b436d2f7-efc4-4ed4-a26e-1c91dd26266e none luks,discard
sda7_crypt UUID=b9fca374-5b95-4e71-8f83-2082a9c5bd58 none luks,discard
sda8_crypt UUID=09786f1f-db39-476b-8a7f-6ee1027a67a6 none luks,swap,discard

```
Is that file still present?

Cheers!

---

### Post by gor4l on 2014-08-26
A friend of mine from ubuntu pl forum [http://ubuntu.pl/forum/viewtopic.php?f=133&t=175292&p=993631#p993631](http://ubuntu.pl/forum/viewtopic.php?f=133&t=175292&p=993631#p993631)
help me solve this problem
Solution was to do these commands from liveDVD,
it allows me to do things on my sda1 from that liveDVD(as far I understand)
```
sudo mount /dev/sda1 /mntsudo 
mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-initramfs -u
update-grub
reboot
```

He find out that there could be error in initramfs, where after kernel update initframs should be updated, and If this from some reason not happend or while doing update was error, so these things could happend.

---

### Post by Bashing-om on 2014-08-26
gor4l; Great !

Thanks for the sharing of the solution.

As this matter is now at an end:
Please mark this thread solved; 
aides others seeking the solution,
 helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and I wish
[INDENT][INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gor4l on 2014-08-26
I have done this.
Thanks for your time.
Hope we won`t meet up again soon :P

and about encrytion, here is my oudput
```
gor4l@gor4l:~$ sudo su
[sudo] password for gor4l: 
root@gor4l:# lsblk
NAME                  MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                     8:0    0 298,1G  0 disk  
&#9500;&#9472;sda1                  8:1    0 290,7G  0 part  /
&#9500;&#9472;sda2                  8:2    0     1K  0 part  
&#9492;&#9472;sda5                  8:5    0   7,5G  0 part  
  &#9492;&#9472;cryptswap1 (dm-0) 252:0    0   7,5G  0 crypt 
sr0                    11:0    1  1024M  0 rom
```
so looks like only swap is encrypted

```
root@gor4l:# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d558b77e-cff1-4a1c-881c-c99bfe9a735b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=1ccf2bb7-388f-4956-9710-0a091cdfa085 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
```
 
I comment out that line ```
#/dev/mapper/cryptswap1 none swap sw 0 0
```
while tryg to solve problem.

```
root@gor4l:# cat /etc/crypttab
cryptswap1 /dev/sda5 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
```

---

