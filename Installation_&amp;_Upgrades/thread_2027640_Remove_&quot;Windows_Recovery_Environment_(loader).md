---
title: "Remove &quot;Windows Recovery Environment (loader) (on /dev/sda1)&quot;"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by Sylslay on 2012-07-16
Looking for simple script to remove from grub2 (on ubuntu 12.04)

this entry from boot menu list.

"Windows Recovery Environment (loader) (on /dev/sda1)"

PS: I edit file:

/etc/grub.d/30_os-prober 

[HTML]
for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi
# Added to remove Windows Recovery
if [ "$LONGNAME" = "Windows Recovery Environment (loader)" ] && [ "${DEVICE}" = "/dev/sda1" ] ; then
continue
fi
# End Added
[/HTML]

from this: 

> for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

and then
sudo update-grub

---

