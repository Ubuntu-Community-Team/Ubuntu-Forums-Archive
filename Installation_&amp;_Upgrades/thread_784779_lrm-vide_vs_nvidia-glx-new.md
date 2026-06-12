---
title: "lrm-vide vs nvidia-glx-new"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by myidisvoid on 2008-05-06
After trying the nvidia-glx and nvidia-glx-new, I found no video drivers work for my GeForce 8600 GT. Every times restart the system, I was put into the ugly low resolution mode.

After searching for the fix, I noticed there is a weird setting in /sbin/lrm-video where MODULE is set to "nvidia_new"

        if [ -e /lib/linux-restricted-modules/.nvidia_new_installed ]; then
               MODULE="nvidia_new"
        fi
...
      modprobe --ignore-install -Qb $@ $MODULE

but where is this nvidia_new? My slocate result returns no nvidia_new but nvidia in /lib/modules/2.6.24-16-generic/kernel/drivers/video/nvidia.ko

Kind of kidding.. :( I just migrated from Gentoo to Ubuntu 8.04 and I am thinking of going back soon... This hot cake doesn't taste good at all (especially after few time fail to apt-get remove the nvidia-glx.)

---

### Post by divague on 2008-05-06
install nvidia-settings, then in a terminal type:

sudo nvidia-settings

change your resolution, click on "apply" if it works click on "save to x configuration file" and click on "save". That worked for me.

---

