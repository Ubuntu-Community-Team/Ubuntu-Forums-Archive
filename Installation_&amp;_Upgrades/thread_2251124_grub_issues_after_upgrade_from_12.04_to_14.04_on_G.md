---
title: "grub issues after upgrade from 12.04 to 14.04 on GPT partition"
date: 2014-11-02
forum: Installation &amp; Upgrades
---

### Post by nevercome on 2014-11-02
Hello everybody,
i couldn't complete a release upgrade from 12.04 server to 14.04 with do-release-upgrade, exiting with a grub error status:

```

Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-41-generic /boot/vmlinuz-3.2.0-41-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-41-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-41-generic /boot/vmlinuz-3.2.0-41-generic
/usr/sbin/grub-probe: error: failed to get canonical path of `none'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-41-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-41-generic (--remove):
 il sottoprocesso installato script di post-removal ha restituito lo stato di errore 1
Removing linux-image-3.2.0-56-generic (3.2.0-56.86) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-56-generic /boot/vmlinuz-3.2.0-56-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-56-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-56-generic /boot/vmlinuz-3.2.0-56-generic
/usr/sbin/grub-probe: error: failed to get canonical path of `none'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-56-generic.postrm line 328.
dpkg: error processing package linux-image-3.2.0-56-generic (--remove):
 il sottoprocesso installato script di post-removal ha restituito lo stato di errore 1

```

typing a dpkg --configure -a :

```

> dpkg --configure -a
Configurazione di samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.3)...
rmdir: failed to remove ‘/etc/dhcp3/dhclient-enter-hooks.d’: No such file or directory
dpkg: error processing package samba-common (--configure):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 1
dpkg: problemi con le dipendenze impediscono la configurazione di smbclient:
 smbclient dipende da samba-common (= 2:4.1.6+dfsg-1ubuntu2.14.04.3); comunque:
  Il pacchetto samba-common non è ancora configurato.

dpkg: error processing package smbclient (--configure):
 problemi con le dipendenze - lasciato non configurato
Configurazione di grub-pc (2.02~beta2-9ubuntu1)...
Including Xen overrides from /etc/default/grub.d/xen.cfg
WARNING: GRUB_DEFAULT changed to boot into Xen by default!
         Edit /etc/default/grub.d/xen.cfg to avoid this warning.
/usr/sbin/grub-probe: error: failed to get canonical path of `none'.
dpkg: error processing package grub-pc (--configure):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 1
dpkg: problemi con le dipendenze impediscono la configurazione di samba-common-bin:
 samba-common-bin dipende da samba-common (= 2:4.1.6+dfsg-1ubuntu2.14.04.3); comunque:
  Il pacchetto samba-common non è ancora configurato.

dpkg: error processing package samba-common-bin (--configure):
 problemi con le dipendenze - lasciato non configurato
Si sono verificati degli errori nell'elaborazione:
 samba-common
 smbclient
 grub-pc
 samba-common-bin
> 

```

or update-grub:

```

> update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `none'.

```

grub was working fine and being updated correctly before the do-release-upgrade .
```

> parted -l
Model: Adaptec 6405E RAID10 (scsi)
Disk /dev/sda: 3994GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  20,5GB  20,5GB  ext4                  msftdata
 2      20,5GB  21,0GB  512MB   linux-swap(v1)
 3      21,0GB  3994GB  3973GB                        lvm

(other device-mapper LVM partitions follow)

```

I'm not sure how to proceed, since it's a remote dedicated server i didn't try a reboot yet .
Any help would be very appreciated. Thank you all.

---

