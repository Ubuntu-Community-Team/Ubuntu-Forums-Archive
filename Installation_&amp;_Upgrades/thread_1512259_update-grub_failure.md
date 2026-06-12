---
title: "update-grub failure"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2010-06-17
Every time I try to install or change software I get this error ```
linux-image-2.6.32-22-generic: subprocess installed post-installation script returned error exit 127
```

I found a thread here on this same problem and the solution was to change some speech marks around a command in /etc/defualt/grub which I did and then ran sudo update-grub and the following error came up. I can't find any info on the net. any one know what this means?

```
/etc/grub.d/10_linux: 121: done uname: not found
```

---

### Post by oldfred on 2010-06-17
Show us your
gksudo gedit /etc/default/grub

Some one should be able to see what you quoted (") and if it is not correct.

---

### Post by tropdoug on 2010-06-18
/etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by arrange on 2010-06-18
I don't see any problems in that file. Could you post somewhere the contents of the **/etc/grub.d/10_linux** file?

---

### Post by tropdoug on 2010-06-18
this si /etc/grub.d/10_linux file

```
#! /bin/sh -e

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
export TEXTDOMAINDIR=@LOCALEDIR@

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
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

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
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
	  cat << EOF
	set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
	initrd	${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

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
	   "initrd-${version}" "initrd.img-${alt_version}" \
	   "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
	"single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done
```

I have seen a bug report that points at the fault being in this file, but I don't know what I am looking at, and the bug fix has not yet been posted.

Thanks for helping

---

### Post by dino99 on 2010-06-18
i think that you have a corrupted index: clean the cache

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

goto synaptic repo: check that you only use genuine ubuntu repo ( no third party, no ppa, no mixed releases) then update

sudo apt-get install -f
sudo dpkg --configure -a

sudo grub-mkconfig
sudo update-grub

you can clean the system with gconf-cleaner (yes to all) and bleachbit

---

### Post by arrange on 2010-06-18
Again, dead end. Could you post```
sudo sh -x /etc/grub.d/10_linux
```(you can use [Ubuntu pastebin]("http://paste.ubuntu.com/") if it's too long)

---

### Post by tropdoug on 2010-06-21
Very grateful for the assistance. Sorry about the delays, but I only get on after work and as I am in Aus the top half of the world is asleep. anyway I still am getting the bug so it's really frustrating. apreciate all the assistance I can get. ):P

Output for ```
sudo sh -x /etc/grub.d/10_linux
```

I also put it into Ubuntu Paste Bin, under my nickname Tropdoug -- I have never seen that before, is it linked to this site only? or what's it's primary use? 

```

+ prefix=/usr
+ exec_prefix=/usr
+ bindir=/usr/bin
+ libdir=/usr/lib
+ . /usr/lib/grub/grub-mkconfig_lib
+ transform=s,x,x,
+ prefix=/usr
+ exec_prefix=/usr
+ datarootdir=/usr/share
+ datadir=/usr/share
+ bindir=/usr/bin
+ sbindir=/usr/sbin
+ sed s,x,x,
+ echo grub
+ pkgdatadir=/usr/share/grub
+ test x = x
+ sed s,x,x,
+ echo grub-probe
+ grub_probe=/usr/sbin/grub-probe
+ test x = x
+ echo grub-mkrelpath
+ sed s,x,x,
+ grub_mkrelpath=/usr/bin/grub-mkrelpath
+ export TEXTDOMAIN=grub
+ export TEXTDOMAINDIR=@LOCALEDIR@
+ CLASS=--class gnu-linux --class gnu --class os
+ [ x = x ]
+ OS=GNU/Linux
+ [ x = x ]
+ LINUX_ROOT_DEVICE=
+ [ -x /usr/bin/makedumpfile ]
+ grub_file_is_not_garbage 
+ test -f 
+ return 1
+ kernelvers=
+ kernelvers=
+ list=
+ doneuname -rfor i in /boot/vmlinuz-2.6.32-22-generic /boot/vmlinuz-2.6.35-020635rc1-generic
/etc/grub.d/10_linux: 1: doneuname: not found
+ prepare_boot_cache=
+ [ x != x ]

```

---

### Post by tropdoug on 2010-06-21
It's solved - thank you to all who helped. The solution came courtesy of martintremblay @ [HTML]http://ubuntuforums.org/showthread.php?t=1495093[/HTML]

this is the solution

```

Hmmm
When you boot does GRUB initialize as expected?
If yes, you potentially have a package and/or file conflict.

These commands will completely uninstall and reinstall GRUB2.
Do this while booted into Lucid:

Code:
     sudo mv /boot/grub /boot/grub_OLD
Code:
sudo mkdir /boot/grub
Code:
sudo apt-get --purge remove grub2
Code:
sudo apt-get --purge remove grub-pc
Code:
sudo apt-get --purge remove grub-common
Code:
sudo apt-get install grub-pc
Code:
sudo update-grub
Code:
sudo grub-install /dev/sda
Then reboot.
```

I have asked Martin if he knows what caused the error, if he replies I will post that here too for others who might be facing the same issues. 

Again thank you all:popcorn::popcorn:

---

### Post by wilee-nilee on 2010-06-21
n

---

### Post by ajaustin on 2011-10-16
> **tropdoug said:**
> It's solved - thank you to all who helped. The solution came courtesy of martintremblay @ [HTML]http://ubuntuforums.org/showthread.php?t=1495093[/HTML]


Thanks to those that have gone before me.  I had the same problem and this solution worked for me too.

---

