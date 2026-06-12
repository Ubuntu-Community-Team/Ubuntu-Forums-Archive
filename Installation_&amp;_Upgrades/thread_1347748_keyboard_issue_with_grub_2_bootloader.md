---
title: "keyboard issue with grub 2 bootloader"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by fgross2 on 2009-12-06
Hello,

I have installed Karmic Koala on a HP pavilion ze4400 notebook (AMD CPU).
System works fine but I have an issue with the new Grub 2 bootloader:

When I press the enter key Ubuntu boots as expected.

But when I try to select another OS (Windows XP) or anything else in the boot menu with the cursor keys grub stops after 2nd key press. I can't even enter edit mode or command line because after pressing 'c' or 'e' no further key is accepted.

With the old Grub version (Hardy) I didn't have this problem.

I have already tried to uncomment the following option in /etc/default/grub: 
#GRUB_TERMINAL=console
After sudo update-grub and reboot I observed the same effect.

Is this a configuration issue or a real bug? 
Who can help me with this issue?

regards and many thanks in advance
Frank

Here's my /etc/default/grub:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"


/etc/grub.d/00_header:

#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
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

transform="s,x,x,"

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
grub_prefix=`echo /boot/grub | sed ${transform}`

. ${libdir}/grub/grub-mkconfig_lib

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fi

cat << EOF
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="${GRUB_DEFAULT}"
if [ \${prev_saved_entry} ]; then
  saved_entry=\${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
EOF

case ${GRUB_TERMINAL_INPUT}:${GRUB_TERMINAL_OUTPUT} in
  serial:* | *:serial)
    if ! test -e ${grub_prefix}/serial.mod ; then
      echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi

    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
      grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
      GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
  ;;
esac

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_input ${GRUB_TERMINAL_INPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal ${GRUB_TERMINAL_INPUT}
fi
EOF
  ;;
esac

case x${GRUB_TERMINAL_OUTPUT} in
 xgfxterm)
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device ${GRUB_FONT_PATH}`

    cat << EOF
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
EOF
  ;;
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_output ${GRUB_TERMINAL_OUTPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal ${GRUB_TERMINAL_OUTPUT}
fi
EOF
  ;;
esac

cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi
EOF

and the resulting
/boot/grub/grub.cfg: 

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 74b1b2d8-507d-4929-ad3a-6def4cf102ab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 74b1b2d8-507d-4929-ad3a-6def4cf102ab
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=74b1b2d8-507d-4929-ad3a-6def4cf102ab ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 74b1b2d8-507d-4929-ad3a-6def4cf102ab
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=74b1b2d8-507d-4929-ad3a-6def4cf102ab ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 74b1b2d8-507d-4929-ad3a-6def4cf102ab
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=74b1b2d8-507d-4929-ad3a-6def4cf102ab ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 74b1b2d8-507d-4929-ad3a-6def4cf102ab
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=74b1b2d8-507d-4929-ad3a-6def4cf102ab ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0673f86e79f6ba24
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by phillw on 2009-12-06
Hi,

A quick way to get your Win area back is covered here ->> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Should have u up & running in no time :-)

Phill.

---

### Post by fgross2 on 2009-12-12
Dear phillw,

I have tried the instructions for Ubuntu 9.10 and I have understood that I can restore my bootloader when I have destroyed it for some reason and have to boot from CD. This is of cause very helpful.Thx for this hint.
But unfortunately this is not my problem. I can see the bootloader menu when I boot from hard disk but it seems that it doesn't work properly. 
As I described in my previous post I am able to press enter and it boots with Linux.
But if I try to select something else with the cursor keys it stops after the second key press and I can't reach e.g. the Windows entry. 
If I try to enter 'e' for edit mode or 'c' for command line I can see the prompt but my keyboard is "dead". The only thing I can do in this situation is to switch my computer off and start again.

---

### Post by fgross2 on 2009-12-25
I now have uninstalled GRUB 2 and replaced it with the old GRUB 0.97.
Everything works fine!!!
Here you can find a description how this works:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
(see chapter 12 "Uninstalling GRUB 2")
Because the Windows partition wasn't recognized automatically I had to add it manually at the end of the menu list in menu.lst.

Thank you

---

