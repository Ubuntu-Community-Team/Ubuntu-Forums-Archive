---
title: "Upgrade 10.10 -&gt; 11.04 and GRUB got crazy"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by biuro74 on 2011-05-16
Hello,

I used to have multiboot solution on my rig and today, when upgraded my Ubuntu to 11.04 via simple screen notification, my GRUB got crazy. Now Ubuntu boots only and rest positions in bootmenu doesn't work.

I've got 2 volumes: RAID-0 HDD strip and single SSD. First boots RAID and GRUB 2 is installed there. There is bootmenu with couple positions:
* Ubuntu
* 2xMandrivas
* Mageia Alpha
* Windows menu
* MemTest.

Windows menu position gives next menu, which is installed on SSD, I've got two Windowses there.

Everything worked fine, I spent some time to "enhance" GRUB bootmenu to get everything together (as my Mandrivas worked with classic GRUB 1, so I changed bootmanager to GRUB 2, placed custom fonts, colors, backgrounds etc) until today's update. Just Ubuntu is bootable now, rest gives me a message:
```
error: no argument specified.
error: no such disk.

```Please - can anyone give me any clue, what is wrong ?

Here we are my config files:

**/etc/default/grub:**
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=4
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1080-24

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
**/etc/grub.d/10_linux:**
```

#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

export TEXTDOMAIN=grub
export TEXTDOMAINDIR=${prefix}/share/locale

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || uses_abstraction "${GRUB_DEVICE}" lvm; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

if [ "x`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2>/dev/null || true`" = xbtrfs ]; then
  rootsubvol="`make_system_path_relative_to_its_root /`"
  rootsubvol="${rootsubvol#/}"
  if [ "x${rootsubvol}" != x ]; then
    GRUB_CMDLINE_LINUX="rootflags=subvol=${rootsubvol} ${GRUB_CMDLINE_LINUX}"
  fi
fi

for word in $GRUB_CMDLINE_LINUX_DEFAULT; do
  if [ "$word" = splash ]; then
    GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=7"
  fi
done

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
    recordfail
EOF
  if ! ${recovery} ; then
      save_default_entry | sed -e "s/^/\t/"
  fi

  cat << EOF
    set gfxpayload=\$linux_gfx_mode
EOF

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    message="$(gettext_printf "Loading Linux %s ..." ${version})"
    cat << EOF
    echo    '$message'
EOF
  fi
  cat << EOF
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if test -n "${initrd}" ; then
    if [ "x$5" != "xquiet" ]; then
      message="$(gettext_printf "Loading initial ramdisk ...")"
      cat << EOF
    echo    '$message'
EOF
    fi
    cat << EOF
    initrd    ${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinuz-* /boot/vmlinux-* /vmlinuz-* /vmlinux-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

# Added to limit number of Linux kernels displayed.
COUNTER=0
LINUX_KERNELS_DISPLAYED=1
#

# Use ELILO's generic "efifb" when it's known to be available.
# FIXME: We need an interface to select vesafb in case efifb can't be used.
if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
  echo "set linux_gfx_mode=$GRUB_GFXPAYLOAD_LINUX"
else
  cat << EOF
if [ \${recordfail} != 1 ]; then
  if [ -e \${prefix}/gfxblacklist.txt ]; then
    if hwmatch \${prefix}/gfxblacklist.txt 3; then
      if [ \${match} = 0 ]; then
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
EOF
fi
cat << EOF
export linux_gfx_mode
if [ "\$linux_gfx_mode" != "text" ]; then load_video; fi
EOF

in_submenu=false
while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
       "initrd-${version}" "initramfs-${version}.img" \
       "initrd.img-${alt_version}" "initrd-${alt_version}.img" \
       "initrd-${alt_version}" "initramfs-${alt_version}.img"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done

  initramfs=
  for i in "config-${version}" "config-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initramfs=`grep CONFIG_INITRAMFS_SOURCE= "${dirname}/${i}" | cut -f2 -d= | tr -d \"`
      break
    fi
  done

  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  elif test -z "${initramfs}" ; then
    # "UUID=" magic is parsed by initrd or initramfs.  Since there's
    # no initrd or builtin initramfs, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
    "single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`

# Added to limit number of Linux kernels displayed.
COUNTER=`expr $COUNTER + 1`
if [ $COUNTER -eq $LINUX_KERNELS_DISPLAYED ]; then
list=""
fi
#

  if [ "$list" ] && ! $in_submenu; then
    echo "submenu \"Previous Linux versions\" {"
    in_submenu=:
  fi
done

if $in_submenu; then
  echo "}"
fi

```
**/etc/grub/d/40_custom:**
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

set default="Windows menu"
set timeout=4

menuentry "Linux Mandriva 2010.1" {
    insmod part_msdos
    insmod ext2
    insmod raid
    set root=(/dev/mapper/nvidia_dbjedfig8)
    search --no-floppy --fs-uuid --set c60484db-0f77-43ba-97b7-c87d6bdd0e52
    linux /boot/vmlinuz BOOT_IMAGE=linux root=/dev/mapper/nvidia_dbjedfigp8 resume=/dev/mapper/nvidia_dbjedfigp14 splash=silent vga=788
    initrd /boot/initrd.img
}

menuentry "Linux Mandriva 2010.1 x64" {
    insmod part_msdos
    insmod ext2
    insmod raid
    set root=(/dev/mapper/nvidia_dbjedfig9)
    search --no-floppy --fs-uuid --set 73353235-153a-479b-9aad-49d6ebafc10c
    linux /boot/vmlinuz BOOT_IMAGE=linux root=/dev/mapper/nvidia_dbjedfigp9 resume=/dev/mapper/nvidia_dbjedfigp14 splash=silent vga=788
    initrd /boot/initrd.img
}

menuentry "Linux Mageia Alpha1" {
    insmod part_msdos
    insmod ext2
    insmod raid
    set root=(/dev/mapper/nvidia_dbjedfig10)
    search --no-floppy --fs-uuid --set 6bf0270b-2817-4d0f-bc1c-13cfd2bb7c8b
    linux /boot/vmlinuz BOOT_IMAGE=linux root=/dev/mapper/nvidia_dbjedfigp10 resume=/dev/mapper/nvidia_dbjedfigp14 splash=silent vga=788
    initrd /boot/initrd.img
}

menuentry "Windows menu" {
    insmod part_msdos
    insmod ntfs
#   set root=(/dev/mapper/nvidia_dbjedfig1)
    set root=(/dev/sda1)
#   search --no-floppy --fs-uuid --set 4a6c915e6c91461b
    search --no-floppy --fs-uuid --set 004828F14828E75E
    chainloader +1
}

menuentry "MemTest 4.0" {
    insmod part_msdos
    insmod ext2
    insmod raid
    set root=(/dev/mapper/nvidia_dbjedfig11)
    search --no-floppy --fs-uuid --set 0a70f9a5-763c-4651-ab15-73812445cf62
    linux16 /boot/memtest86+.bin
}


```I've checked my drives assignments - all are fine (SSD is /dev/sda1, RAID-0 is /dev/mapper/nvidia_dbjedfig). UUIDs stayed the same, too.

Any help appreciated,
Thank you

---

### Post by biuro74 on 2011-05-16
Solved.

For all followers who may find it helpful: there was something wrong with partition naming like '/dev/nvidia_dbjedfigXX', so what I've done was to change all those symbols to GRUB-like 'hd3,msdosXX'.

I was strange anyway, because previously (10.04, 10.10) it was working fine.

Luckily, Windows-menu entry has NOT been changed and it automagically started to work :) So I think there's a small bug there in GRUB package, but if it works, I don't mind.

---

