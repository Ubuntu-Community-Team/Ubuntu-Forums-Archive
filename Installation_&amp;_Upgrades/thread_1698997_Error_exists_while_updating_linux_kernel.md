---
title: "Error exists while updating linux kernel"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by joyous on 2011-03-03
Hi,

 My kernel is not updating and I'm getting errors like.........

" sujay@Rigel:$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.35-27-generic (2.6.35-27.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-27-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
Generating grub.cfg ...
/etc/grub.d/10_linux: 160: Syntax error: "then" unexpected (expecting "done")
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-27-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-27-generic; however:
  Package linux-image-2.6.35-27-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.27.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.35-27-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Please help me !
Regards
joy

---

### Post by joyous on 2011-03-14
> **joyous said:**
> Hi,

 My kernel is not updating and I'm getting errors like.........

" sujay@Rigel:$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.35-27-generic (2.6.35-27.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-27-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
Generating grub.cfg ...
/etc/grub.d/10_linux: 160: Syntax error: "then" unexpected (expecting "done")
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-27-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-27-generic; however:
  Package linux-image-2.6.35-27-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.27.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.35-27-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Please help me !
Regards
joy

Hi Friends,

   Help me to get rid of these errors !
"sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.35-27-generic (2.6.35-27.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-27-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
Generating grub.cfg ...
/etc/grub.d/10_linux: 160: Syntax error: "then" unexpected (expecting "done")
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-27-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because the error message indicates its a followup error from a previous failure.
                                    No apport report written because the error message indicates its a followup error from a previous failure.
  dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-27-generic; however:
  Package linux-image-2.6.35-27-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.27.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-27-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Thanks in advance. 
joy

---

### Post by oldos2er on 2011-03-14
"/etc/grub.d/10_linux: 160: Syntax error: "then" unexpected (expecting "done")"

Did you edit /etc/grub.d/10_linux? Looks like the error is there.

---

### Post by joyous on 2011-03-16
> **oldos2er said:**
> "/etc/grub.d/10_linux: 160: Syntax error: "then" unexpected (expecting "done")"

Did you edit /etc/grub.d/10_linux? Looks like the error is there.

HiAnn,

   I didn't edit anything in /etc/grub.d/10_linux. Could you give
me any solution regarding the errors?


Regards,
joy

---

### Post by oldos2er on 2011-03-16
Need to see the file. Can you run **cat /etc/grub.d/10_linux** and post the output?

---

### Post by joyous on 2011-03-18
> **oldos2er said:**
> Need to see the file. Can you run **cat /etc/grub.d/10_linux** and post the output?


Here is the results......

"#! /bin/sh
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

  # Use ELILO's generic "efifb" when it's known to be available.
  # FIXME: We need an interface to select vesafb in case efifb can't be used.
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

list=`for i in /boot/vmlinu[zx]-* /vmlinu[zx]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=
COUNTER=0
LINUX_KERNELS_DISPLAYED=2

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
COUNTER=`expr $COUNTER +1`
if[$COUNTER -eq $LINUX_KERNELS_DISPLAYED];then
list=""
fi
#
done"

Regards
joy

---

### Post by Dutch70 on 2011-03-18
Just a friendly tip joyous,

First of all, sorry I can't help you with your problem, but it will make the people trying to help you much happier if you edit your long posts, highlight the long list of info you provided & put code tags around it by clicking the "#" sign in the toolbar. 

Kind regards,
Dutch

---

