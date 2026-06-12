---
title: "I compile own kernel with lvm,but it can't boot"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by bibletang on 2006-08-13
In vmware, i download kernel source from [www.kernel.org](www.kernel.org)
and i compile it with
[PHP][*] Multiple devices driver support (RAID and LVM)
  &#9474;[ ]   RAID support                                           
  &#9474;[*]   Device mapper support  [/PHP]  the lvm support

and ext3 support
[PHP]&#9474;[*] Ext3 journalling file system support                             &#9474; &#9474;
  &#9474; &#9474;[*]   Ext3 extended attributes                                       &#9474; &#9474;
  &#9474; &#9474;[*]     Ext3 POSIX Access Control Lists                              &#9474; &#9474;
  &#9474; &#9474;[ ]     Ext3 Security Labels[/PHP]

this is my /boot/grub/menu.lst
[PHP]default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title linux(2.6.17.8)
        root (hd0,0)
        kernel /linux-2.6.17.8 root=/dev/VolGroup00/LogVol00

title Offical kernel (2.6.15)
        root (hd0,0)
        kernel /vmlinuz-2.6.15 ro root=/dev/VolGroup00/LogVol00
        initrd /initrd-2.6.15.img[/PHP] 2.6.17.8 is my new kernel,2.6.15 is offical kernel
this is my /etc/fstab
[PHP]/dev/VolGroup00/LogVol00 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
/dev/VolGroup00/LogVol01 swap                    swap    defaults        0 0[/PHP]

i think it's okay, but i don't know why when i reboot use my new kernel (2.6.17.8), it failed!
[PHP]VFS: cannot open root device "VolGroup00/LogVol00" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0)[/PHP]
i don't understand why offical kernel can work, but my compile kernel can't work, may where are something differents between their's .config.

---

