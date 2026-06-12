---
title: "GRUB issue after upgrade from xenial to bionic"
date: 2019-11-01
forum: Installation &amp; Upgrades
---

### Post by gonzobilbao on 2019-11-01
Hi,


First of all, I am still digging around to solve this so sorry if there is something already. From what I have been searching, nothing so far addresses my problem so I am going ahead and posting a new thread. Any replies are highly appreciated.

I just upgraded from 16.04 to 18.04 via the upgrade tool that comes with ubuntu. I have a dual boot system, EFI, with W10 and Ubuntu. The upgrade went ok for the most part. I got a few grub error messages though. This is what I get when I run sudo dpkg --audit


[HTML]$ sudo dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 grub-efi-amd64-signed GRand Unified Bootloader, version 2 (EFI-AMD64 version, 
 shim-signed          Secure Boot chain-loading bootloader (Microsoft-signed bi

The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 friendly-recovery    Make recovery boot mode more user-friendly
 grub-efi-amd64       GRand Unified Bootloader, version 2 (EFI-AMD64 version)

The following packages are only half installed, due to problems during
installation. The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-image-4.15.0-66-generic Signed kernel image generic
 linux-image-4.4.0-165-generic Signed kernel image generic
 linux-image-4.4.0-166-generic Signed kernel image generic
 linux-image-4.4.0-78-generic Linux kernel image for version 4.4.0 on 64 bit x8
 linux-image-extra-4.4.0-78-generic Linux kernel extra modules for version 4.4.

The following packages have been triggered, but the trigger processing
has not yet been done.  Trigger processing can be requested using
dselect or dpkg --configure --pending (or dpkg --triggers-only):
 initramfs-tools      generic modular initramfs generator (automation)
[/HTML]

Trying dist-upgrade throws the output:

[HTML]sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED
  linux-image-4.4.0-165-generic linux-image-4.4.0-166-generic
  linux-image-4.4.0-78-generic linux-image-extra-4.4.0-78-generic
The following NEW packages will be installed
  dwz linux-modules-4.15.0-66-generic
The following packages will be upgraded:
  debhelper dh-autoreconf init init-system-helpers iproute2
5 to upgrade, 2 to newly install, 4 to remove and 0 not to upgrade.
9 not fully installed or removed.
Need to get 13.1 MB/22.9 MB of archives.
After this operation, 168 MB disk space will be freed.
Do you want to continue? [Y/n] 
Get:1 http://ca.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-modules-4.15.0-66-generic amd64 4.15.0-66.75 [13.1 MB]
Fetched 13.1 MB in 7s (1,794 kB/s)                                             
Preconfiguring packages ...
(Reading database ... 279807 files and directories currently installed.)
Removing linux-image-4.4.0-165-generic (4.4.0-165.193) ...
W: Last kernel image has been removed, so removing the default symlinks
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.4.0-165-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
error: out of memory.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 287
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-4.4.0-165-generic (--remove):
 installed linux-image-4.4.0-165-generic package post-removal script subprocess returned error exit status 1
Removing linux-image-4.4.0-166-generic (4.4.0-166.195) ...
W: Last kernel image has been removed, so removing the default symlinks
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.4.0-166-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
error: out of memory.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 287
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-4.4.0-166-generic (--remove):
 installed linux-image-4.4.0-166-generic package post-removal script subprocess returned error exit status 1
Removing linux-image-extra-4.4.0-78-generic (4.4.0-78.99) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-78-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
 * dkms: running auto installation service for kernel 4.4.0-78-generic   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-78-generic
WARNING: missing /lib/modules/4.4.0-78-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-78-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_TIDhJw/lib/modules/4.4.0-78-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_TIDhJw/lib/modules/4.4.0-78-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
error: out of memory.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 287
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-78-generic (--remove):
 installed linux-image-extra-4.4.0-78-generic package post-removal script subprocess returned error exit status 1
Removing linux-image-4.4.0-78-generic (4.4.0-78.99) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-78-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
error: out of memory.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 287
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-78-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-78-generic (--remove):
 installed linux-image-4.4.0-78-generic package post-removal script subprocess returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-4.4.0-165-generic
 linux-image-4.4.0-166-generic
 linux-image-extra-4.4.0-78-generic
 linux-image-4.4.0-78-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/HTML]

More details of my partition table:

[HTML] sudo parted /dev/sda
GNU Parted 3.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p

Model: ATA Crucial_CT750MX3 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  473MB  472MB   ntfs         Basic data partition          hidden, diag
 2      473MB   578MB  105MB   fat32        EFI system partition          boot, esp
 3      578MB   595MB  16.8MB               Microsoft reserved partition  msftres
 4      595MB   104GB  103GB   ntfs         Basic data partition          msftdata
 5      104GB   105GB  890MB   ntfs                                       hidden, diag
 6      105GB   140GB  35.3GB  ext4
 7      140GB   750GB  610GB   ext4


[/HTML]

The partition Number 4 is my windows 10 system.

As of now, my systems is not super functional, although I can log in, log out, etc, all that seems to be working fine. Usb devices are not recognized (I guess because they are handled by the kernel). 

Any pointers are very welcome. I have tried a few solutions that have seemed to work for others with similar problems. But so far no luck.

Thank you!

---

### Post by oldfred on 2019-11-01
Did you look at line 287 in this: 
/boot/grub/grub.cfg.new file attached.

When I had a typo in my 40_custom, it generated the .new file and told me what line to look at. Took me a bit as it was missing a closing } in boot stanza before error line.

Did you run the dpkg reconfigure commands suggested?
Or perhaps a full reinstall of grub-efi-amd64, but that will overwrite any configuration changes you made to /etc/grub.d and /etc/default/grub.

---

### Post by gonzobilbao on 2019-11-01
Hi,

Thanks for the suggestions.

My /boot/grub/grub.cfg.new file looks like this (line 287 would be the very last line)

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
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
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
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

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  17460f19-59df-48e1-95bf-426ed8db0797
else
  search --no-floppy --fs-uuid --set=root 17460f19-59df-48e1-95bf-426ed8db0797
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 10 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=1
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "Windows Boot UEFI fbx64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/Boot/fbx64.efi
}

menuentry "EFI/refind/refind_x64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/refind/refind_x64.efi
}

menuentry "EFI/ubuntu/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/ubuntu/fwupx64.efi
}

menuentry "EFI/ubuntu/mmx64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/ubuntu/mmx64.efi
}

menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/ubuntu/MokManager.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/25_custom.save ###

menuentry "Windows 10 loader" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "EFI/refind/refind_x64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/refind/refind_x64.efi
}

menuentry "EFI/ubuntu/fbx64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/ubuntu/fbx64.efi
}

menuentry "EFI/ubuntu/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/ubuntu/fwupx64.efi
}

menuentry "EFI/ubuntu/mmx64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EF
### END /etc/grub.d/25_custom.save ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-76C4-274C' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  76C4-274C
    else
      search --no-floppy --fs-uuid --set=root 76C4-274C
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

### BEGIN /etc/grub.d/bkp25_custom ###

menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "EFI/refind/refind_x64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/refind/refind_x64.efi
}

menuentry "EFI/ubuntu/fbx64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/ubuntu/fbx64.efi
}

menuentry "EFI/ubuntu/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/ubuntu/fwupx64.efi
}

menuentry "EFI/ubuntu/mmx64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/ubuntu/mmx64.efi
}

menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EFI/ubuntu/MokManager.efi
}
### END /etc/grub.d/bkp25_custom ###[/HTML]


I tried reinstalling all grub-amd64-efi, grub-amd64-efi-bin and grub-amd64-efi-signed. Uninstalling was succesfull, but installing them again didn't work. Synaptic gives me an error message

[HTML]E: linux-image-4.15.0-66-generic: installed linux-image-4.15.0-66-generic package post-removal script subprocess returned error exit status 1
E: linux-image-4.4.0-165-generic: installed linux-image-4.4.0-165-generic package post-removal script subprocess returned error exit status 1
E: linux-image-4.4.0-166-generic: installed linux-image-4.4.0-166-generic package post-removal script subprocess returned error exit status 1
E: linux-image-extra-4.4.0-78-generic: installed linux-image-extra-4.4.0-78-generic package post-removal script subprocess returned error exit status 1
E: linux-image-4.4.0-78-generic: installed linux-image-4.4.0-78-generic package post-removal script subprocess returned error exit status 1



```

before opening this thread, I had tried 
dpkg --configure grub-efi-amd64-signed

but it did not solve the issue...

thanks

---

### Post by gonzobilbao on 2019-11-01
Looks like the problem is solved. Oldfred you gave a clue with your issue with 40_custom: I looked at everything inside /etc/grub.d. Turns out that I was having a similar problem with 25-custom.save. I added the bracket at the end and reinstalled grub-amd64-efi. Everything worked just fine. I am going to reboot now, fingers crossed!!

Gonzalo

---

### Post by oldfred on 2019-11-01
This does not look correct, ends with ef and  no closing  }, error is probably just at end as mismatch with open & closing parenthesis :

```
menuentry "EFI/ubuntu/mmx64.efi" {
search --fs-uuid --no-floppy --set=root 76C4-274C
chainloader (${root})/EF
### END /etc/grub.d/25_custom.save ###

```

Your 25_custom comes from Boot-Repair and in most cases is not required, not ever seen it make a incorrect entry before? 
You can either delete all of 25_custom or edit at will like you do with 40_custom.
# Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also. also can turn off execute on 25_custom if none wanted
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

Do not know if that is only issue or not.

---

