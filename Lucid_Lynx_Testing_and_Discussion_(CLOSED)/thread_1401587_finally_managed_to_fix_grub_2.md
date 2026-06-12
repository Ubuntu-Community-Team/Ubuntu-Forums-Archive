---
title: "finally managed to fix grub 2"
date: 2010-02-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-08
with this command alone 
sudo aptitude install grub-pc

from here:
[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

how can i add windows 7 now?

---

### Post by phenest on 2010-02-08
sudo update-grub

Why did you open a new thread?

---

### Post by phenest on 2010-02-08
> **phenest said:**
> Why did you open a new thread?

And not very Lucid specific.

---

### Post by aviramof on 2010-02-08
sudo update-grub doesn't add windows 7 to the menu 

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-12-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

i also have another problem i want to finishe this guide and change to uuid but the last command don't work for me.

---

### Post by VMC on 2010-02-08
> **phenest said:**
> And not very Lucid specific.

Exactly. Two topics and non related specifically to Lucid.

Read [this]("https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD") for recover Grub2.

---

### Post by aviramof on 2010-02-08
they are lucid spesific because it is lucid but never mind.

and i don't need to recover grub 2 stop giving me the same links all the time and just tell me what are

the commands i need.

and i'm not on live cd any more.

---

### Post by phenest on 2010-02-08
> **aviramof said:**
> they are lucid spesific because it is lucid but never mind.

and i don't need to recover grub 2 stop giving me the same links all the time and just tell me what is 

the command i need.

and i'm not on live cd any more.

This could happen on Karmic, Debian, etc, not just Lucid.

We are repeating ourselves because we know how to fix your system and you should listen.

But, if you're going to start demanding answers, then I suggest you go back through everything you have been told as the answers have been given.

Grub 1 will not do anything that grub 2 cannot do. Grub 2 is your best solution.

---

### Post by aviramof on 2010-02-08
have you read this thread at all like the title?

"finally managed to fix grub 2"

i used this to install grub 2
[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04) 

and then i moved on to do this:
[http://images.howtoforge.com/images/grub2_ubuntu_9.04/8.png](http://images.howtoforge.com/images/grub2_ubuntu_9.04/8.png)

and i got this:
[http://images.howtoforge.com/images/grub2_ubuntu_9.04/9.png](http://images.howtoforge.com/images/grub2_ubuntu_9.04/9.png)
or something similer

but this doesn't work:
sudo upgrade-from-grub-legacy

get this:
sudo upgrade-from-grub-legacy
sudo: upgrade-from-grub-legacy: command not found

that is problem one.

problem two:
how to add windows 7 to grub 2.

that is all.

---

### Post by phillw on 2010-02-08
A couple of points.

If you followed the instructions for 9.04 (from that how to) - You'll be running Grub Legacy, not Grub2.

 >  Testing for an existing GRUB menu.lst file ... found:  /boot/grub/menu.lst

Kinda gives the game away, as Grub2 doesn't use menu.lst.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)  Has information on installing Grub2 onto a Grub Legacy system.

Regards,

Phill.

---

### Post by VMC on 2010-02-08
aviramof, you have opened three topics all related to the same thing. Please slow down collect your thoughts then explain your situation on one topic only. You have  us running all over the place repeating ourselves.

I know in a previous topic you mentioned you have Windows7 installed and want to keep that. Correct? Lets start from there and please stay with one topic only.

---

### Post by aviramof on 2010-02-08
doesn't this command install grub 2?
sudo aptitude install grub-pc

---

### Post by VMC on 2010-02-08
> **aviramof said:**
> doesn't this command install grub 2?
sudo aptitude install grub-pc

Yes, but it installs the program not the mbr, your wanting to install grub to the mbr. Running the installed program will do that.

---

### Post by aviramof on 2010-02-08
what installed program.

---

### Post by VMC on 2010-02-08
> **aviramof said:**
> what installed program.

You were asking about installing grub-pc. I replied to that question. 

Type this into a terminal:

```
aptitude show grub-pc|head -4
```

You should see that grub-pc is installed and what version is installed.

---

### Post by kansasnoob on 2010-02-08
> **aviramof said:**
> sudo update-grub doesn't add windows 7 to the menu 

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-12-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

i also have another problem i want to finishe this guide and change to uuid but the last command don't work for me.

I really don't see how or why Lucid would be ending up with legacy grub but anyway having mixed legacy grub and grub2 files causes problems.

Regardless copy-n-paste these commands:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub
```

That will probably say, "not installed so not removed", that's OK.

```
sudo apt-get --purge remove grub-common
```

```
sudo apt-get install --reinstall grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/**[COLOR="Red"]sda[/COLOR]**
```

Or:

```
sudo grub-install /dev/**[COLOR="Red"]sdb[/COLOR]**
```

I can only guess where to install grub2 (which mbr) because you're all over the place with this:

[http://ubuntuforums.org/showthread.php?t=1400072](http://ubuntuforums.org/showthread.php?t=1400072)

---

### Post by aviramof on 2010-02-08
i did one thing i formated again because i had problems with languges support and all the
rest and cleaned everything with windows 7 cd fixboot fixmbr now i have this 

ubuntu@ubuntu:~$ aptitude show grub-pc|head -4
Package: grub-pc
State: installed
Automatically installed: yes
Version: 1.98~20100128-1ubuntu3

i'm using live cd right now.

now what is wrong with grub 2 not creating any menu?

and by the way does this version have an ati driver i can install?

and just for the record sda is the ubuntu it's on my second drive ide hitachi 

sdb is my western digital hd my first hd with windows 7.

---

### Post by kansasnoob on 2010-02-08
> now what is wrong with grub 2 not creating any menu?

If os-prober finds a menu.lst it doesn't look for the necessary grub2 files, ie: /etc/grub.d/30_os-prober.

---

### Post by aviramof on 2010-02-08
```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    52,436,159    52,436,097  83 Linux
/dev/sda2          52,436,160    58,733,639     6,297,480  82 Linux swap / Solaris
/dev/sda3          58,733,640   160,826,714   102,093,075   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,156,224    78,156,162   7 HPFS/NTFS
/dev/sdb2          78,157,824   162,043,903    83,886,080   7 HPFS/NTFS
/dev/sdb3         162,043,904   312,577,499   150,533,596   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ac03693b-529d-410e-9f46-25e7c94b36bb   ext4                                     
/dev/sda2        07ec86a2-0540-4289-8c40-c97097b6306e   swap                                     
/dev/sda3        22CE2E75441D4836                       ntfs                                     
/dev/sdb1        C44451F64451EC24                       ntfs       Windows 7                     
/dev/sdb2        58544AAE544A8F26                       ntfs       &#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;           
/dev/sdb3        EA9635979635656B                       ntfs       &#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;           

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Windows 7         fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set ac03693b-529d-410e-9f46-25e7c94b36bb
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
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set ac03693b-529d-410e-9f46-25e7c94b36bb
set locale_dir=($root)/boot/grub/locale
set lang=he
insmod gettext
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
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ac03693b-529d-410e-9f46-25e7c94b36bb
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=ac03693b-529d-410e-9f46-25e7c94b36bb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ac03693b-529d-410e-9f46-25e7c94b36bb
    echo    Loading Linux 2.6.32-12-generic ...
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=ac03693b-529d-410e-9f46-25e7c94b36bb ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ac03693b-529d-410e-9f46-25e7c94b36bb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ac03693b-529d-410e-9f46-25e7c94b36bb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c44451f64451ec24
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ac03693b-529d-410e-9f46-25e7c94b36bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=07ec86a2-0540-4289-8c40-c97097b6306e none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.32-12-generic
    .0GB: boot/vmlinuz-2.6.32-12-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```ubuntu@ubuntu:~$ sudo os-prober
/dev/sda1:Ubuntu lucid (development branch) (10.04):Ubuntu:linux
/dev/sdb1:Windows 7 (loader):Windows:chain

now why can't it find etc/grub.d/30_os-prober?

 etc/grub.d/30_os-prober:
```
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

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

. ${libdir}/grub/grub-mkconfig_lib

found_other_os=

adjust_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
    verbose=
      else
    verbose=" --verbose"
      fi

      if [ "x${GRUB_HIDDEN_TIMEOUT}" = "x0" ] ; then
    cat <<EOF
if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
    cat << EOF
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

osx_entry() {
        cat << EOF
menuentry "${LONGNAME} (${2}-bit) (on ${DEVICE})" {
EOF
    save_default_entry | sed -e "s/^/\t/"
    prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
    cat << EOF
        insmod ${GRUB_VIDEO_BACKEND}
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ \$do_resume == 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
}

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2
  found_other_os=1

  case ${BOOT} in
    chain)

      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
    Windows\ Vista*|Windows\ 7*)
    ;;
    *)
      cat << EOF
    drivemap -s (hd0) \${root}
EOF
    ;;
      esac

      cat <<EOF
    chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

    if [ "${LROOT}" != "${LBOOT}" ]; then
      LKERNEL="${LKERNEL#/boot}"
      LINITRD="${LINITRD#/boot}"
    fi

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" {
EOF
    save_default_entry | sed -e "s/^/\t/"
    if [ -z "${prepare_boot_cache}" ]; then
      prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
    fi
    printf '%s\n' "${prepare_boot_cache}"
    cat <<  EOF
    linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
    initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
      mach_device="`echo "${grub_device}" | tr -d '()' | tr , s`"
      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
      case "${grub_fs}" in
    *fs)    hurd_fs="${grub_fs}" ;;
    *)    hurd_fs="${grub_fs}fs" ;;
      esac
      cat << EOF
    multiboot /boot/gnumach.gz root=device:${mach_device}
    module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
            --multiboot-command-line='\${kernel-command-line}' \\
            --host-priv-port='\${host-port}' \\
            --device-master-port='\${device-port}' \\
            --exec-server-task='\${exec-task}' -T typed '\${root}' \\
            '\$(task-create)' '\$(task-resume)'
    module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
}
EOF
    ;;
    *)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout
```SET command:

```
    return 0
}
_tcpdump () 
{ 
    local cur prev;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        -@(r|w|F))
            _filedir;
            return 0
        ;;
        -i)
            _available_interfaces -a;
            return 0
        ;;
    esac;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-a -d -e -f -l -n -N -O -p \
            -q -R -S -t -u -v -x -C -F -i -m -r -s -T -w -E' -- "$cur" ));
    fi
}
_ufw () 
{ 
    cur=${COMP_WORDS[COMP_CWORD]};
    prev=${COMP_WORDS[COMP_CWORD-1]};
    if [ $COMP_CWORD -eq 1 ]; then
        COMPREPLY=($( compgen -W "$(_ufw_commands)" $cur ));
    else
        if [ $COMP_CWORD -eq 2 ]; then
            case "$prev" in 
                app)
                    COMPREPLY=($( compgen -W "$(_ufw_app_commands)" $cur ))
                ;;
                status)
                    COMPREPLY=($( compgen -W "$(_ufw_status_commands)" $cur ))
                ;;
                delete)
                    COMPREPLY=($( compgen -W "$(_ufw_rule_commands)" $cur ))
                ;;
                logging)
                    COMPREPLY=($( compgen -W "$(_ufw_logging_commands)" $cur ))
                ;;
                show)
                    COMPREPLY=($( compgen -W "$(_ufw_show_commands)" $cur ))
                ;;
                default)
                    COMPREPLY=($( compgen -W "$(_ufw_default_commands)" $cur ))
                ;;
            esac;
        fi;
    fi
}
_ufw_app_commands () 
{ 
    ufw --help | sed -e '1,/^Application profile commands:/d' -e '/^ [^ ]/!d' -e 's/[ \t]\+app[ \t]\+\([a-z|]\+\)[ \t]\+.*/\1/g'
}
_ufw_commands () 
{ 
    commands=$(ufw --help | sed -e '1,/^Commands:/d' -e '/^Application profile commands:/Q' -e 's/^[ \t]\+\([a-z|]\+\)[ \t]\+.*/\1/g' -e 's/|/ /g' | uniq);
    echo "$commands app"
}
_ufw_default_commands () 
{ 
    echo "allow deny reject"
}
_ufw_logging_commands () 
{ 
    echo "off on low medium high full"
}
_ufw_rule_commands () 
{ 
    echo "`_ufw_default_commands` limit"
}
_ufw_show_commands () 
{ 
    echo "raw"
}
_ufw_status_commands () 
{ 
    echo "numbered verbose"
}
_uids () 
{ 
    if type getent &>/dev/null; then
        COMPREPLY=($( compgen -W '$( getent passwd | cut -d: -f3 )' -- "$cur" ));
    else
        if type perl &>/dev/null; then
            COMPREPLY=($( compgen -W '$( perl -e '"'"'while (($uid) = (getpwent)[2]) { print $uid . "\n" }'"'"' )' -- "$cur" ));
        else
            COMPREPLY=($( compgen -W '$( cut -d: -f3 /etc/passwd )' -- "$cur" ));
        fi;
    fi
}
_umount () 
{ 
    local cur IFS='
';
    COMPREPLY=();
    cur=`_get_cword`;
    COMPREPLY=($( compgen -W '$( mount | cut -d" " -f 3 )' -- "$cur" ));
    return 0
}
_update_alternatives () 
{ 
    local cur prev mode args i;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        --@(altdir|admindir))
            _filedir -d;
            return 0
        ;;
        --@(help|version))
            return 0
        ;;
    esac;
    for ((i=1; i < COMP_CWORD; i++ ))
    do
        if [[ "${COMP_WORDS[i]}" == --@(install|remove|auto|display|config|remove-all) ]]; then
            mode=${COMP_WORDS[i]};
            args=$(($COMP_CWORD - i));
            break;
        fi;
    done;
    case $mode in 
        --install)
            case $args in 
                1)
                    _filedir
                ;;
                2)
                    _installed_alternatives
                ;;
                3)
                    _filedir
                ;;
            esac
        ;;
        --remove)
            case $args in 
                1)
                    _installed_alternatives
                ;;
                2)
                    _filedir
                ;;
            esac
        ;;
        --auto)
            _installed_alternatives
        ;;
        --remove-all)
            _installed_alternatives
        ;;
        --display)
            _installed_alternatives
        ;;
        --config)
            _installed_alternatives
        ;;
        *)
            COMPREPLY=($( compgen -W '--verbose --quiet --help --version \
                   --altdir --admindir' -- "$cur" ) $( compgen -W '--install --remove --auto --display \
                   --config' -- "$cur" ))
        ;;
    esac
}
_update_rc_d () 
{ 
    local cur prev sysvdir services options valid_options;
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    [ -d /etc/rc.d/init.d ] && sysvdir=/etc/rc.d/init.d || sysvdir=/etc/init.d;
    services=($(echo $sysvdir/!(README*|*.sh|*.dpkg*|*.rpm@(orig|new|save))));
    services=(${services[@]#$sysvdir/});
    options=(-f -n);
    if [[ $COMP_CWORD -eq 1 || "$prev" == -* ]]; then
        valid_options=($(         echo "${COMP_WORDS[@]} ${options[@]}"         | tr " " "\n"         | sed -ne "/$( echo "${options[@]}" | sed "s/ /\\|/g" )/p"         | sort | uniq -u         ));
        COMPREPLY=($( compgen -W '${options[@]} ${services[@]}'         -X '$( echo ${COMP_WORDS[@]} | tr " " "|" )' -- "$cur" ));
    else
        if [[ "$prev" == ?($( echo ${services[@]} | tr " " "|" )) ]]; then
            COMPREPLY=($( compgen -W 'remove defaults start stop' -- "$cur" ));
        else
            if [[ "$prev" == defaults && "$cur" == [0-9] ]]; then
                COMPREPLY=(0 1 2 3 4 5 6 7 8 9);
            else
                if [[ "$prev" == defaults && "$cur" == [sk]?([0-9]) ]]; then
                    COMPREPLY=(0 1 2 3 4 5 6 7 8 9);
                else
                    if [[ "$prev" == defaults && -z "$cur" ]]; then
                        COMPREPLY=(0 1 2 3 4 5 6 7 8 9 s k);
                    else
                        if [[ "$prev" == ?(start|stop) ]]; then
                            if [[ "$cur" == [0-9] || -z "$cur" ]]; then
                                COMPREPLY=(0 1 2 3 4 5 6 7 8 9);
                            else
                                if [[ "$cur" == [0-9][0-9] ]]; then
                                    COMPREPLY=($cur);
                                else
                                    COMPREPLY=();
                                fi;
                            fi;
                        else
                            if [[ "$prev" == ?([0-9][0-9]|[0-6S]) ]]; then
                                if [[ -z "$cur" ]]; then
                                    if [[ $prev == [0-9][0-9] ]]; then
                                        COMPREPLY=(0 1 2 3 4 5 6 S);
                                    else
                                        COMPREPLY=(0 1 2 3 4 5 6 S .);
                                    fi;
                                else
                                    if [[ "$cur" == [0-6S.] ]]; then
                                        COMPREPLY=($cur);
                                    else
                                        COMPREPLY=();
                                    fi;
                                fi;
                            else
                                if [[ "$prev" == "." ]]; then
                                    COMPREPLY=($(compgen -W "start stop" -- "$cur"));
                                else
                                    COMPREPLY=();
                                fi;
                            fi;
                        fi;
                    fi;
                fi;
            fi;
        fi;
    fi;
    return 0
}
_usb_ids () 
{ 
    COMPREPLY=(${COMPREPLY[@]:-} $( compgen -W     "$( PATH="$PATH:/sbin" lsusb | awk '{print $6}' )" -- "$cur" ))
}
_user_at_host () 
{ 
    local cur;
    COMPREPLY=();
    cur=`_get_cword`;
    if [[ $cur == *@* ]]; then
        _known_hosts_real "$cur";
    else
        COMPREPLY=($( compgen -u -- "$cur" ));
    fi;
    return 0
}
_useradd () 
{ 
    local cur prev split=false;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    _split_longopt && split=true;
    case "$prev" in 
        -c | --comment | -h | --help | -e | --expiredate | -f | --inactive | -k | --key | -p | --password | -u | --uid | -Z | --selinux-user)
            return 0
        ;;
        -b | --base-dir | -d | --home | -k | --skel)
            _filedir -d;
            return 0
        ;;
        -g | --gid)
            _gids;
            [ -n "$bash205" ] && COMPREPLY=("${COMPREPLY[@]}" $( compgen -g ));
            COMPREPLY=($( compgen -W '${COMPREPLY[@]}' -- "$cur" ));
            return 0
        ;;
        -G | --groups)
            [ -n "$bash205" ] && COMPREPLY=($( compgen -g -- "$cur" ));
            return 0
        ;;
        -s | --shell)
            _shells;
            return 0
        ;;
    esac;
    $split && return 0;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-b --base-dir -c --comment -d --home\
            -D --defaults -e --expiredate -f --inactive -g --gid \
            -G --groups -h --help -k --skel -K --key -l -M \
            -m --create-home -N --no-user-group -o --non-unique \
            -p --password -r --system -s --shell -u --uid \
            -U --user-group -Z --selinux-user' -- "$cur" ));
        return 0;
    fi
}
_userdel () 
{ 
    local cur;
    COMPREPLY=();
    cur=`_get_cword`;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-f --force -h --help -r --remove'             -- "$cur" ));
        return 0;
    fi;
    COMPREPLY=($( compgen -u -- "$cur" ))
}
_usergroup () 
{ 
    local IFS='
';
    cur=${cur//\\\\ / };
    if [[ $cur = *@(\\:|.)* ]] && [ -n "$bash205" ]; then
        user=${cur%%*([^:.])};
        COMPREPLY=($(compgen -P ${user/\\\\} -g -- ${cur##*[.:]}));
    else
        if [[ $cur = *:* ]] && [ -n "$bash205" ]; then
            COMPREPLY=($( compgen -g -- ${cur##*[.:]} ));
        else
            COMPREPLY=($( compgen -S : -u -- "$cur" ));
        fi;
    fi
}
_usermod () 
{ 
    local cur prev split=false;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    _split_longopt && split=true;
    case "$prev" in 
        -c | --comment | -d | --home | -e | --expiredate | -f | --inactive | -h | --help | -l | --login | -p | --password | -u | --uid | -Z | --selinux-user)
            return 0
        ;;
        -g | --gid)
            _gids;
            [ -n "$bash205" ] && COMPREPLY=("${COMPREPLY[@]}" $( compgen -g ));
            COMPREPLY=($( compgen -W '${COMPREPLY[@]}' -- "$cur" ));
            return 0
        ;;
        -G | --groups)
            [ -n "$bash205" ] && COMPREPLY=($( compgen -g -- "$cur" ));
            return 0
        ;;
        -s | --shell)
            _shells;
            return 0
        ;;
    esac;
    $split && return 0;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-a --append -c --comment -d --home \
            -e --expiredate -f --inactive -g --gid -G --groups \
            -h --help -l --login -L --lock -o --non-unique \
            -p --password -s --shell -u --uid -U --unlock \
            -Z --selinux-user' -- "$cur" ));
        return 0;
    fi;
    COMPREPLY=($( compgen -u -- "$cur" ))
}
_vipw () 
{ 
    local cur prev;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        -h | --help)
            return 0
        ;;
    esac;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-g --group -h --help -p --passwd \
            -q --quiet -s --shadow' -- "$cur" ));
        return 0;
    fi
}
_xhost () 
{ 
    local cur=`_get_cword`;
    case "$cur" in 
        +*)
            _known_hosts_real -p+ "${cur:1}"
        ;;
        -*)
            _known_hosts_real -p- "${cur:1}"
        ;;
        *)
            _known_hosts_real "$cur"
        ;;
    esac;
    return 0
}
_xmllint () 
{ 
    local cur prev;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        -o | --output)
            _filedir;
            return 0
        ;;
        --path | --dtdvalidfpi | --maxmem | --encode | --pattern)
            return 0
        ;;
        --dtdvalid)
            _filedir dtd;
            return 0
        ;;
        --relaxng)
            _filedir rng;
            return 0
        ;;
        --schema)
            _filedir xsd;
            return 0
        ;;
        --schematron)
            _filedir sch;
            return 0
        ;;
    esac;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '$( xmllint --help 2>&1 | \
            sed -ne "s/^[[:space:]]*\(--[^[:space:]:]*\).*/\1/p" ) \
            -o' -- "$cur" ));
        return 0;
    fi;
    _filedir '@(*ml|htm|svg)'
}
_xrandr () 
{ 
    local cur prev output modes;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        --output)
            local outputs=$(xrandr|grep 'connected'|awk '{print $1}');
            COMPREPLY=($(compgen -W "$outputs" -- "$cur"));
            return 0
        ;;
        --mode)
            for ((i = 1; i < COMP_CWORD; i++ ))
            do
                if [[ "${COMP_WORDS[i]}" == "--output" ]]; then
                    output=${COMP_WORDS[i+1]};
                    break;
                fi;
            done;
            modes=$(xrandr|sed -e "1,/$output/ d"                 -e "/connected/,$ d"|awk '{print $1}');
            COMPREPLY=($( compgen -W "$modes" -- "$cur"));
            return 0
        ;;
    esac;
    case "$cur" in 
        *)
            COMPREPLY=($(compgen -W '-d -display -help -o \
                    --orientation -q --query -s --size\
                    -r --rate -v --version -x -y --screen \
                    --verbose --dryrun --prop --fb \
                    --fbmm --dpi --output --auto --mode \
                    --preferred --pos --reflect --rotate \
                    --left-of --right-of --above --below \
                    --same-as --set --off --crtc --newmode \
                    --rmmode --addmode --delmode' -- "$cur"));
            return 0
        ;;
    esac;
    return 0
}
command_not_found_handle () 
{ 
    if [ -x /usr/lib/command-not-found ]; then
        /usr/bin/python /usr/lib/command-not-found -- $1;
        return $?;
    else
        return 127;
    fi
}
dequote () 
{ 
    eval echo "$1" 2> /dev/null
}
quote () 
{ 
    echo \'${1//\'/\'\\\'\'}\'
}
quote_readline () 
{ 
    if [ -n "$bash4" ]; then
        echo "${1}";
        return;
    fi;
    local t="${1//\\/\\\\}";
    echo \'${t//\'/\'\\\'\'}\'
}

```i belive it's enaf information to figure it all out once and for all if not just tell me what you need.

---

### Post by kansasnoob on 2010-02-08
It looks to me like it did find it:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c44451f64451ec24
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

So is "Windows 7 (loader) (on /dev/sdb1)" not showing up in boot options?

---

### Post by aviramof on 2010-02-08
there is no boot menu there is nothing it's automatily goes to windows 7 no ubuntu at all

the only way i can create dual boot is with this command or at least that helped before:
sudo aptitude install grub-pc.

but i took this command from here:
[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

i don't use because it could cause me problem with the rest of the guide and basicly with the command sudo upgrade-from-grub-legacy that would not work because i'm not updating from grub to grub 2 i already have grub 2 installed it just not displayed when i start the computer.

so i need a similer command or that someone would tell me that it would not create the picture from the above link.

---

### Post by phenest on 2010-02-08
Perhaps one of the moderators could merge the 3 threads you have created on one subject, and move the thread to a more appropriate section.

---

### Post by aviramof on 2010-02-08
i just need to know one thing does sudo aptitude install grub-pc could do damage or not

and i don't need to join threads i gave all the information any one need a few replies ago in this thread.

my only problem with using this command that it might cause the picture in this link:
[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

which i don't want.

---

### Post by kansasnoob on 2010-02-08
> **aviramof said:**
> there is no boot menu there is nothing it's automatily goes to windows 7 no ubuntu at all

the only way i can create dual boot is with this command or at least that helped before:
sudo aptitude install grub-pc.

but i took this command from here:
[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

i don't it to cause me problem again with the rest of the guide and basicly with the command sudo upgrade-from-grub-legacy that would not work because i'm not updating from grub to grub 2 i already have grub 2 installed it just not displayed when i start the computer.

Then the BIOS is set to boot from sdb first, look:

>  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb


There really are two ways to fix that:

#1. Change the boot priority in BIOS.

#2. Install grub2 to the mbr of both drives by booting an Ubuntu Live CD and from the Live Desktop run:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
grub-install /dev/sdb
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then **if you ever decide to get rid of Ubuntu and want the Windows MBR back** just boot your Ubuntu Live CD and run:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sdb mbr
```

---

### Post by aviramof on 2010-02-08
i did the second option because i don't think that changing the bios would create a boot menu i tried this before and as for the second part **get rid of Ubuntu **could windows 7
disk command prompt bootrec.exe /fixboot bootrec.exe /fixmbr would do the same?

---

### Post by aviramof on 2010-02-08
Finally!!!!!!!!!!!!!!!!!! Finally the problem is solved now everything is working fine 
and i have grub 2 working perfectly:):):)

thanks you very much:):):)

---

### Post by kansasnoob on 2010-02-08
> **aviramof said:**
> Finally!!!!!!!!!!!!!!!!!! Finally the problem is solved now everything is working fine 
and i have grub 2 working perfectly:):):)

thanks you very much:):):)

99% of boot problems are generally simple if a person just slows down a bit :D

I find when I get frustrated it's time to just walk away for a while, that's when it's sweet to know how to restore the mbr to whatever other OS I wish and then come back to the problem when I'm calm.

---

### Post by dino99 on 2010-02-09
hi all,

just followed #15 by kansasnoob because one of my installed distro was an upgrade of grub-legacy (now using the latest of grub-ppa)

After doing all, i look at /boot/grub/locale, but this subfolder is empty.
Should not be some files in there ? How is yours ?

---

### Post by aviramof on 2010-02-09
this folder is empty for me at least.

---

### Post by phillw on 2010-02-09
Also empty (mine was a clean 10.04 install, though).

Phill.

---

### Post by dino99 on 2010-02-09
still wonder:

when running grub-mkconfig, we can see in the first lines, a subfolder is created (/grub/locale) then an other line defined which locale is used.

At time this seem to do nothing bad, i suppose it's designed for future features.

---

