---
title: "Boot fails after upgrading edgy to gutsy"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by raoul@merki.ch on 2007-10-30
Hi

I am trying since about 3 days to get my system up again.

After a dist-upgrade the system does not boot anymore.

<------------------ snip ---------------------->
Booting 'Ubuntu 7.10, kernel 2.6.22-14-server'

root (hd0,4)
 Filesystem type is ext2fs, partition type 0x83
kernel  /vmlinuz-2.6.22-14-server root=/dev/mapper/Ubuntu-root ro quiet splash
   [Linux-bzImage, setup=0x1e00, size=0x1b2558]
initrd   /initrd.img-2.6.22-14-server
   [Linux-initrd @ 0x1f84c000, 0x7a32dd bytes]

Loading, please wait...       <--- takes a very long time (serveral minutes)
/scripts/local-top/lvm: /scipts/local-top/lvm: 46: vgchange: not found
<--- takes again some minutes --->
     Check root= bootarg cat /proc/cmdline
     or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/mapper/Ubuntu-root does not exist. Dropping to a shell!

<---- ends up in Busybox ---->
<------------------ snip ---------------------->

Have a /boot partition and / and swap in logical volumes.

Booted into rescue mode from CD. Logical volumes are there, mountable e2fsck ok.
How can I get this machine up again? I am technical, but not used to fix boot issues.

System is a FujitsuSiemens with AMD Athlon 1200MHz around 700 MB RAM.

Regards

Raoul

---

### Post by zvacet on 2007-10-30
You can not upgrade directly from Edgy to Gutsy.It goes like this Edgy>Feisty>Gutsy.It is big download,because your release have to be up-to-date before every upgrade.It is better to download Gutsy Cd and do fresh install.But,that´s just me.You can go with first solution if you feel like it.

---

### Post by tajreed on 2007-10-30
Try booting to a different kernel. Hit esc right after the bios finishes to find the various boot options.

---

### Post by raoul@merki.ch on 2007-10-31
Ok. It is new to me that I have to do all releases within a year. Thought 6.10 to 7.10 would be ok.

Booting another kernel did not help as well.

So is there a chance to get it back again without a complete reinstall?

Regards

Raoul

---

