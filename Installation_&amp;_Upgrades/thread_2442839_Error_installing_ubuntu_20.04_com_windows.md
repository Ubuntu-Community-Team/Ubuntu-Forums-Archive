---
title: "Error installing ubuntu 20.04 com windows"
date: 2020-05-08
forum: Installation &amp; Upgrades
---

### Post by ramirezjurgen on 2020-05-08
I have tried to install ubuntu with windows, previously it had version 19.04 and it worked well, try to install version 20.04 but I have problems with grub, I try to use grub boot-repair, but when I run it, it gives me an error that I do not have an internet connection, but if I am connected , I have tried to mount the partition but it does not work, please help me. I leave the log and state of my computer and the error that appears at startup.

```


boot-repair-4ppa102                                              [20200508_0630]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location.
 => Grub2 (v1.99-2.00) is installed in the MBR of /dev/sdb and looks at sector 
    1707133040 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => No known boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbia32.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/fedora/gcdia32.efi /efi/fedora/gcdx64.efi 
                       /efi/fedora/grubia32.efi /efi/fedora/grubx64.efi 
                       /efi/fedora/mmia32.efi /efi/fedora/mmx64.efi 
                       /efi/fedora/shim.efi /efi/fedora/shimia32.efi 
                       /efi/fedora/shimia32-fedora.efi 
                       /efi/fedora/shimx64.efi /efi/fedora/shimx64-fedora.efi 
                       /efi/neon/grubx64.efi /efi/neon/mmx64.efi 
                       /efi/neon/shimx64.efi /efi/ubuntu/fwupx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/fedora/grub.cfg 
                       /efi/neon/grub.cfg /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/memtest.efi

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04 LTS
    Boot files:        /etc/fstab /etc/default/grub

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /efi/BOOT/mmx64.efi


================================ 3 OS detected =================================

OS#1:   Ubuntu 20.04 LTS on sdb4
OS#2:   Windows on sda2
OS#3:   Linux on sdb1

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04 LTS, focal, x86_64)

===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
efibootmgr -v
BootCurrent: 000A
Timeout: 0 seconds
BootOrder: 0001,0000,0003,0002,0009,000A,0008
Boot0000* Windows Boot Manager    HD(2,GPT,904fd0cf-2454-47f6-bccc-6bd4b3082ec2,0x596c4800,0x100000)/File(FI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...M................
Boot0001* ubuntu    HD(2,GPT,904fd0cf-2454-47f6-bccc-6bd4b3082ec2,0x596c4800,0x100000)/File(FIUNTU\SHIMX64.EFI)
Boot0002* neon    HD(2,GPT,904fd0cf-2454-47f6-bccc-6bd4b3082ec2,0x596c4800,0x100000)/File(FI\NEON\SHIMX64.EFI)
Boot0003* Fedora    HD(2,GPT,904fd0cf-2454-47f6-bccc-6bd4b3082ec2,0x596c4800,0x100000)/File(FI\FEDORA\SHIMX64.EFI)
Boot0008* opensuse-secureboot    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0009* Fedora    HD(2,GPT,904fd0cf-2454-47f6-bccc-6bd4b3082ec2,0x596c4800,0x100000)/File(FI\FEDORA\SHIM.EFI)..BO
Boot000A* UEFI: General USB Flash Disk 1100, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(1,GPT,3e9bd500-a613-4e80-a23e-6d18714f0a5a,0x800,0xeff7df)..BO SecureBoot disabled.

f7a57b08bc7c1c85417ae4cea582d1d4   sdb2/Boot/bootx64.efi
200ab215c2cb8722296342a9e627d38c   sdb2/Boot/fbia32.efi
bed45d1c9554cea09924d3814cb7c446   sdb2/Boot/fbx64.efi
4487628005555bfd4a4c0a47211e0700   sdb2/Boot/mmx64.efi
cb22c6afe5df6d1380bf3101d2f22a73   sdb2/fedora/gcdia32.efi
526c6c0d0772ebe2cdbd7555207d75d3   sdb2/fedora/gcdx64.efi
a560f2104e0b964eca0575bdb17fe12b   sdb2/fedora/grubia32.efi
2c577856b90956b12d622fb53554979d   sdb2/fedora/grubx64.efi
41c4276e977e53b050992112472ab40f   sdb2/fedora/mmia32.efi
81c81deecc9294607cf865657fbbb69c   sdb2/fedora/mmx64.efi
f2c580ccd60898d4aa2676249d67c171   sdb2/fedora/shim.efi
87e606dee08705c7ac75737a83a6e063   sdb2/fedora/shimia32.efi
5bb208de54be71a8741ea6f651a008f6   sdb2/fedora/shimia32-fedora.efi
f2c580ccd60898d4aa2676249d67c171   sdb2/fedora/shimx64.efi
6841eb6a2033a4d29e4ab654ea1e23f3   sdb2/fedora/shimx64-fedora.efi
a62486b1639d335d4b5813e8088bb5ac   sdb2/neon/grubx64.efi
4487628005555bfd4a4c0a47211e0700   sdb2/neon/mmx64.efi
f7a57b08bc7c1c85417ae4cea582d1d4   sdb2/neon/shimx64.efi
256fe27540b54b71cf38110338247688   sdb2/ubuntu/fwupx64.efi
98bea152fadd26c4e9136916f6cc32a8   sdb2/ubuntu/grubx64.efi
4487628005555bfd4a4c0a47211e0700   sdb2/ubuntu/mmx64.efi
f7a57b08bc7c1c85417ae4cea582d1d4   sdb2/ubuntu/shimx64.efi
cb8e4284804d56f058c0e1cf111eeedd   sdb2/Microsoft/Boot/bootmgfw.efi
3df357ffd0654bb80f2a575485e6e0cc   sdb2/Microsoft/Boot/bootmgr.efi
87e606dee08705c7ac75737a83a6e063   sdb2/Boot/BOOTIA32.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________

sda    : GPT,    BIOS_boot,    has-noESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes
sdb    : GPT,    BIOS_boot,    has---ESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda3    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdb1    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sdb2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdb4    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda2    : isnotESP,    part-has-no-fstab,    notbiosboot,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : isnotESP,    part-has-no-fstab,    notbiosboot,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sdb1    : isnotESP,    fstab-without-efi,    is-biosboot,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb2    : is---ESP,    part-has-no-fstab,    notbiosboot,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb4    : isnotESP,    fstab-has-goodEFI,    notbiosboot,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda2    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda3    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sdb1    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sdb
sdb2    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sdb
sdb4    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk sda: 119.25 GiB, 128035676160 bytes, 250069680 sectors
          Start       End   Sectors   Size Type
sda1       2048     34815     32768    16M BIOS boot
sda2      34816 248981331 248946516 118.7G Microsoft basic data
sda3  248981504 250066943   1085440   530M Windows recovery environment
Disk sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
           Start        End    Sectors   Size Type
sdb1        2048 1500267293 1500265246 715.4G BIOS boot
sdb2  1500268544 1501317119    1048576   512M EFI System
sdb3  1951524864 1953523711    1998848   976M Linux swap
sdb4  1501317120 1951524151  450207032 214.7G Linux filesystem
Partition table entries are not in disk order.
Disk sdc: 7.51 GiB, 8053063680 bytes, 15728640 sectors
      Start      End  Sectors  Size Type
sdc1   2048 15728606 15726559  7.5G Microsoft basic data

parted -lm (filtered): _________________________________________________________

sda:128GB:scsi:512:512:gpt:ATA SanDisk SD8SN8U1:;
1:1049kB:17.8MB:16.8MB::Microsoft reserved partition:bios_grub;
2:17.8MB:127GB:127GB:ntfs:Basic data partition:msftdata;
3:127GB:128GB:556MB:ntfs::hidden, diag;
sdb:1000GB:scsi:512:4096:gpt:ATA ST1000LM035-1RK1:;
1:1049kB:768GB:768GB:ntfs:Basic data partition:bios_grub;
2:768GB:769GB:537MB:fat32:EFI System Partition:boot, esp;
4:769GB:999GB:231GB:ext4::;
3:999GB:1000GB:1023MB:linux-swap(v1)::swap;
sdc:8053MB:scsi:512:512:gpt:General USB Flash Disk:;
1:1049kB:8053MB:8052MB:fat32:Main Data Partition:msftdata;

blkid (filtered): ______________________________________________________________

NAME  FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                  
sda1                                                04655de9-0a5e-4be7-81ee-28f1e62d997e             Microsoft reserved partition
sda2  ntfs     36EADDCAEADD8711                     0bea17d4-8ded-4505-ba6a-6f3c5bb19537             Basic data partition
sda3  ntfs     F2C4780DC477D279                     4c8a9d40-3bcf-4ef2-b517-2aa72c5c1230             
sdb                                                                                                  
sdb1  ntfs     7C78ADFE78ADB774                     cbe4afd3-65d9-4ad9-9cbb-c637fbbb7690 DATA        Basic data partition
sdb2  vfat     1E1C-E7C9                            904fd0cf-2454-47f6-bccc-6bd4b3082ec2             EFI System Partition
sdb3  swap     db2ddbe5-b277-445e-94dd-996b739e18c2 a11d9fc8-4fd5-4af1-88da-df5fcaa0c085             
sdb4  ext4     5733dbda-c5e4-450e-bd13-8f124a6699ab a159911e-0491-4842-9554-04aeec427cb4             
sdc                                                                                                  
sdc1  vfat     769A-E38A                            3e9bd500-a613-4e80-a23e-6d18714f0a5a UBUNTU 20_0 Main Data Partition

df (filtered): _________________________________________________________________

      Avail Use% Mounted on
sda3   88.9M  83% /mnt/boot-sav/sda3
sdc1      5G  34% /cdrom

Mount options: __________________________________________________________________

sda3   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sdc1   ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

=========================== sdb2/efi/fedora/grub.cfg ===========================

#
#
#
### BEGIN /etc/grub.d/00_header ###
set pager=1
if [ -f ${config_directory}/grubenv ]; then
  load_env -f ${config_directory}/grubenv
elif [ -s $prefix/grubenv ]; then
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="${saved_entry}"
fi
if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi
export menuentry_id_option
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi
function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}
terminal_output console
if [ x$feature_timeout_style = xy ] ; then
  set timeout_style=menu
  set timeout=5
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/01_users ###
if [ -f ${prefix}/user.cfg ]; then
  source ${prefix}/user.cfg
  if [ -n "${GRUB2_PASSWORD}" ]; then
    set superusers="root"
    export superusers
    password_pbkdf2 root ${GRUB2_PASSWORD}
  fi
fi
### END /etc/grub.d/01_users ###
### BEGIN /etc/grub.d/08_fallback_counting ###
insmod increment
if [ -n "${boot_counter}" -a "${boot_success}" = "0" ]; then
  if  [ "${boot_counter}" = "0" -o "${boot_counter}" = "-1" ]; then
    set default=1
    set boot_counter=-1
  else
    decrement boot_counter
  fi
  save_env boot_counter
fi
### END /etc/grub.d/08_fallback_counting ###
### BEGIN /etc/grub.d/10_linux ###
insmod part_gpt
insmod ext2
set root='hd1,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt4 --hint-efi=hd1,gpt4 --hint-baremetal=ahci1,gpt4  cd82e827-2f51-43c3-8c65-32ef3f446235
else
  search --no-floppy --fs-uuid --set=root cd82e827-2f51-43c3-8c65-32ef3f446235
fi
insmod part_gpt
insmod fat
set boot='hd1,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=boot --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  1E1C-E7C9
else
  search --no-floppy --fs-uuid --set=boot 1E1C-E7C9
fi
#
set default_kernelopts="root=/dev/mapper/fedora_localhost--live-root ro resume=/dev/mapper/fedora_localhost--live-swap rd.lvm.lv=fedora_localhost-live/root rd.lvm.lv=fedora_localhost-live/swap rhgb quiet"
insmod blscfg
blscfg
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/10_reset_boot_success ###
insmod increment
if [ "${boot_success}" = "1" -o "${boot_indeterminate}" = "1" ]; then
  set menu_hide_ok=1
else
  set menu_hide_ok=0 
fi
if [ "${boot_success}" = "1" ] ; then
  set boot_indeterminate=0
else
  increment boot_indeterminate
fi
set boot_success=0
save_env boot_success boot_indeterminate
### END /etc/grub.d/10_reset_boot_success ###
### BEGIN /etc/grub.d/12_menu_auto_hide ###
if [ x$feature_timeout_style = xy ] ; then
  if [ "${menu_show_once}" ]; then
    unset menu_show_once
    save_env menu_show_once
    set timeout_style=menu
    set timeout=60
  elif [ "${menu_auto_hide}" -a "${menu_hide_ok}" = "1" ]; then
    set orig_timeout_style=${timeout_style}
    set orig_timeout=${timeout}
    if [ "${fastboot}" = "1" ]; then
      set timeout_style=menu
      set timeout=0
    else
      set timeout_style=hidden
      set timeout=1
    fi
  fi
fi
### END /etc/grub.d/12_menu_auto_hide ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_ppc_terminfo ###
### END /etc/grub.d/20_ppc_terminfo ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sdb2)' --class windows --class os $menuentry_id_option 'osprober-efi-1E1C-E7C9' {
    insmod part_gpt
    insmod fat
    set root='hd1,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  1E1C-E7C9
    else
      search --no-floppy --fs-uuid --set=root 1E1C-E7C9
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
if [ "${orig_timeout_style}" -a "${menu_auto_hide}" != "2" ]; then
  set timeout_style=${orig_timeout_style}
  set timeout=${orig_timeout}
fi
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###
### BEGIN /etc/grub.d/40_custom ###
### END /etc/grub.d/40_custom ###
### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================ sdb2/efi/neon/grub.cfg ============================

search.fs_uuid b8144623-a8cf-4646-ba12-11666f5ab12f root hd1,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=========================== sdb2/efi/ubuntu/grub.cfg ===========================

search.fs_uuid 5733dbda-c5e4-450e-bd13-8f124a6699ab root hd1,gpt4 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

========================== sdb4/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb4 during installation
UUID=5733dbda-c5e4-450e-bd13-8f124a6699ab /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
UUID=1E1C-E7C9  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdb3 during installation
UUID=db2ddbe5-b277-445e-94dd-996b739e18c2 none            swap    sw              0       0

======================= sdb4/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
#GRUB_TERMINAL=console
#GRUB_GFXMODE=640x480
#GRUB_DISABLE_LINUX_UUID=true
#GRUB_DISABLE_RECOVERY="true"
#GRUB_INIT_TUNE="480 440 1"

==================== sdb4: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)

 717.532222748 = 770.444357632  boot/vmlinuz                                   2
 717.532222748 = 770.444357632  boot/vmlinuz-5.4.0-26-generic                  2
 769.082134247 = 825.795653632  boot/initrd.img                                3
 769.082134247 = 825.795653632  boot/initrd.img-5.4.0-26-generic               3
 769.082134247 = 825.795653632  boot/initrd.img.old                            3

====================== sdc1/boot/grub/grub.cfg (filtered) ======================

Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings

========================= sdc1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sdc1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================== sdc1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1


======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown MBR on /dev/sdc

00000000  41 4b 45 4f fc 31 c0 fa  8e d0 bc 00 7c fb 8e d8  |AKEO.1......|...|
00000010  bb 13 04 8b 07 83 e8 04  89 07 c1 e0 06 8e c0 b7  |................|
00000020  07 b8 7f 00 cd 10 31 db  31 c9 ba 4f 18 b8 00 06  |......1.1..O....|
00000030  cd 10 31 d2 b4 02 cd 10  b4 41 bb aa 55 cd 13 72  |..1......A..U..r|
00000040  29 81 fb 55 aa 75 23 f7  c1 01 00 74 1d 66 31 c0  |)..U.u#....t.f1.|
00000050  66 50 66 40 66 50 06 6a  00 6a 08 6a 10 89 e6 b4  |fPf@fP.j.j.j....|
00000060  42 cd 13 9f 83 c4 10 9e  eb 0d b8 08 02 b9 02 00  |B...............|
00000070  ba 80 00 31 db cd 13 bb  07 00 72 0b 31 f6 8c c0  |...1......r.1...|
00000080  8e d8 e8 3f 00 eb 06 be  19 7d e8 37 00 31 c0 8e  |...?.....}.7.1..|
00000090  d8 be 65 7d e8 2d 00 e8  1d 00 b4 01 cd 16 75 08  |..e}.-........u.|
000000a0  b4 02 cd 16 24 04 74 f2  31 c0 8e d8 b8 34 12 a3  |....$.t.1....4..|
000000b0  73 04 ea 00 00 ff ff b4  01 cd 16 74 06 b4 00 cd  |s..........t....|
000000c0  16 e2 f4 c3 ac 3c 00 74  4f 3c 0d 74 f7 3c 0a 75  |.....<.tO<.t.<.u|
000000d0  10 53 b4 03 cd 10 fe c6  b2 00 b4 02 cd 10 5b eb  |.S............[.|
000000e0  e3 3c 5c 75 1c b1 02 ac  3c 46 7f d8 2c 30 3c 09  |.<\u....<F..,0<.|
000000f0  7e 02 2c 07 c0 e3 04 24  0f 08 c3 fe c9 75 e8 eb  |~.,....$.....u..|
00000100  c3 b9 01 00 b4 09 cd 10  53 31 db b4 03 cd 10 fe  |........S1......|
00000110  c2 b4 02 cd 10 5b eb ac  c3 0d 0a 20 20 20 20 20  |.....[.....     |
00000120  20 20 20 20 20 20 20 20  5c 30 34 2a 2a 2a 20 45  |        \04*** E|
00000130  52 52 4f 52 3a 20 54 48  49 53 20 4d 45 44 49 41  |RROR: THIS MEDIA|
00000140  20 43 41 4e 4e 4f 54 20  42 4f 4f 54 20 49 4e 20  | CANNOT BOOT IN |
00000150  4c 45 47 41 43 59 20 4d  4f 44 45 20 2a 2a 2a 5c  |LEGACY MODE ***\|
00000160  30 37 0d 0a 00 0d 0a 0d  0a 20 20 20 20 20 20 20  |07.......       |
00000170  20 20 20 20 20 20 5c 37  30 50 6c 65 61 73 65 20  |      \70Please |
00000180  72 65 6d 6f 76 65 20 74  68 69 73 20 6d 65 64 69  |remove this medi|
00000190  61 20 61 6e 64 20 70 72  65 73 73 20 61 6e 79 20  |a and press any |
000001a0  6b 65 79 20 74 6f 20 72  65 62 6f 6f 74 5c 30 37  |key to reboot\07|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  02 00 ee fe ff d2 01 00  00 00 ff ff ff ff 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility will purge (in order to fix packages) and reinstall the grub-efi-amd64-signed of
sdb1,
using the following options:        sdb2/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s fix-windows-boot use-standard-efi-file    



Final advice in case of suggested repair: ______________________________________

Please do not forget to make your BIOS boot on sdb2/efi/****/shim****.efi (**** will be updated in the final message) file!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\shim****.efi (**** will be updated in the final message)

```

---

### Post by yancek on 2020-05-08
I would suggest that you read the Ubuntu documentation at the link below which explains dual-booting with windows UEFI.
You have a mix of UEFI and Legacy.  Your windows is EFI.  You can see that sdb2 is an EFI partition and that in addition to the windows EFI files, you also have EFI files for Fedora, Neon and Ubuntu.  sda1 and sdb1 are BIOS boot partitions which are not needed/used with an EFI install.  Boot repair shows sdb4 as the Ubuntu install and apparently you no longer have the other OS's (Fedora, Neon).  Disable Legacy/CSM boot in the BIOS so it boots in EFI mode. 

You indicate that you tried to mount the partition but don't indicate which partition that would be or why you want to mount it.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

