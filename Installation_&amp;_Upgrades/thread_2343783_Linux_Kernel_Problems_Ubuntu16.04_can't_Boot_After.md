---
title: "Linux Kernel Problems: Ubuntu16.04 can't Boot After Upgrade"
date: 2016-11-19
forum: Installation &amp; Upgrades
---

### Post by maxerbox on 2016-11-19
I recently upgraded from ubuntu 14.04 to 16.04. 
I'm renting a dedicated server, then I can't access to GRUB at start-up.
So I can't boot (no ping response) and I don't know why.
My host  allow me to boot with a live CD image (ubuntu 12.04) to recovery my server, then I mounted my partitions and started a chroot session.
I tried to install last linux-image (4.4.0-47)and  installation worked like a charm. I did the command update-grub.


Here is /boot/grub/menu.list


I also tried to install another kernel version as you can see(4.4.0-34).


```

root@62-210-243-90:/boot/grub# cat menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.


## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0


## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3


## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu


# Pretty colours
#color cyan/blue white/blue


## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret


#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#


#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST


### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below


## DO NOT UNCOMMENT THEM, Just edit them to your needs


## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=aa0c854e-b229-4e57-bab8-c9f9c76e0c03 ro


## default grub root device
## e.g. groot=(hd0,0)
# groot=cb3a6d4b-ad2c-48f3-8604-2bf4e511e6c4


## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true


## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false


## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash


## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false


## Xen hypervisor options to use with the default Xen boot option
# xenhopt=


## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0


## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single


## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all


## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect


## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true


## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false


## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false


## ## End Default Options ##


title           Ubuntu 16.04.1 LTS, kernel 4.4.0-47-generic
uuid            cb3a6d4b-ad2c-48f3-8604-2bf4e511e6c4
kernel          /vmlinuz-4.4.0-47-generic root=UUID=aa0c854e-b229-4e57-bab8-c9f9                                                                                                                               c76e0c03 ro quiet splash
initrd          /initrd.img-4.4.0-47-generic


title           Ubuntu 16.04.1 LTS, kernel 4.4.0-47-generic (recovery mode)
uuid            cb3a6d4b-ad2c-48f3-8604-2bf4e511e6c4
kernel          /vmlinuz-4.4.0-47-generic root=UUID=aa0c854e-b229-4e57-bab8-c9f9                                                                                                                               c76e0c03 ro  single
initrd          /initrd.img-4.4.0-47-generic


title           Ubuntu 16.04.1 LTS, kernel 4.4.0-34-generic
uuid            cb3a6d4b-ad2c-48f3-8604-2bf4e511e6c4
kernel          /vmlinuz-4.4.0-34-generic root=UUID=aa0c854e-b229-4e57-bab8-c9f9                                                                                                                               c76e0c03 ro quiet splash
initrd          /initrd.img-4.4.0-34-generic


title           Ubuntu 16.04.1 LTS, kernel 4.4.0-34-generic (recovery mode)
uuid            cb3a6d4b-ad2c-48f3-8604-2bf4e511e6c4
kernel          /vmlinuz-4.4.0-34-generic root=UUID=aa0c854e-b229-4e57-bab8-c9f9                                                                                                                               c76e0c03 ro  single
initrd          /initrd.img-4.4.0-34-generic


### END DEBIAN AUTOMAGIC KERNELS LIST

```


Here is /etc/default/grub
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="console=ttyS1,9600 BOOTIF=01-e8-9a-8f-22-d9-61"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



```


Here is /boot/grub/grub.cfg
```

root@62-210-243-90:/boot/grub# cat grub.cfg
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
insmod part_msdos
insmod ext2
set root='hd0,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  aa0c854e-b229-4e57-bab8-c9f9c76e0c03
else
  search --no-floppy --fs-uuid --set=root aa0c854e-b229-4e57-bab8-c9f9c76e0c03
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=fr_FR
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
        set gfxpayload="${1}"
        if [ "${1}" = "keep" ]; then
                set vt_handoff=vt.handoff=7
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


### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
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



```
Here is the output of "update-grub"
```

root@62-210-243-90:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-4.4.0-47-generic
Found kernel: /vmlinuz-4.4.0-34-generic
Replacing config file /run/grub/menu.lst with new version
Found kernel: /vmlinuz-4.4.0-47-generic
Found kernel: /vmlinuz-4.4.0-34-generic
Updating /boot/grub/menu.lst ... done

```

Output of "dpkg -l | grep grub"
```

root@62-210-243-90:/boot/grub# dpkg -l | grep grub
ii  grub                                  0.97-29ubuntu68                          amd64        GRand Unified Bootloader (Legacy version)
ii  grub-common                           2.02~beta2-36ubuntu3.2                   amd64        GRand Unified Bootloader (common files)
rc  grub-pc                               2.02~beta2-36ubuntu3.2                   amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)



```

[U]Another information : It's looking like there is no news logs written when I boot ubuntu16.04 (like Syslog or dmesg). I know that because I did the command "ls -t -lh" in /var/log to sort files by time. 
 My last dsmeg is before the upgrade.[/U]


Can you help me to solve this boot issue ?
Thanks for your help.
Ask me for informations

---

### Post by maxerbox on 2016-11-24
Problem not fixed

---

