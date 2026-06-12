---
title: "Kernel Upgrade Broke Auto-mounts"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by lwnexgen2 on 2008-09-22
Hey Guys-

I just updated Ubuntu to the newest kernel - 2.6.18-19 I think, and the upgrade changed the way things are mounted so it hangs on "searching for root file system" when booting.

I've seen this problem in various places, and they all say to fix it I need to fix my fstab and grub menu.lst. I can't figure out for the life of me what I need to put in there, because nothing is working for me, so I was hoping someone could look at what I can get out of the OS and give me an idea of what to try. I've gotten all of this by using a live 8.04 cd.

fdisk -l:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

```

mtab (of live OS after mounting root partition of broken OS):
```

proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.24-19-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.24-19-generic/volatile tmpfs rw,mode=0755 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
/dev/sda1 /media/disk ext3 rw,nosuid,nodev,uhelper=hal 0 0

```

current fstab of the broken install:
```

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=272f2275-1f7c-4459-ac48-2464a40ff4e0 / ext3 relatime,errors=remount-ro 0 1

# Entry for /dev/sdb5 :
UUID=395d07b8-8f82-4ee2-b98f-5cc0e8cd2e1f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/Vista ntfs umask=222,utf8 0 0

```

current menu.lst
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

Thanks for any help anyone can give me, I'm kind of at my wits end with this. Sorry for the length of this, but this is everything that I thought might be useful in figuring out what went wrong.

---

