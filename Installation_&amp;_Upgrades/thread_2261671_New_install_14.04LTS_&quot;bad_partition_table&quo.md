---
title: "New install 14.04LTS &quot;bad partition table&quot;"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by blm14 on 2015-01-20
OK so I have a dell latitude E5440 which I just upgraded to an SSD. I have to use full disk encryption due to work regulations, so I installed using the mini.iso via a USB stick that I created with unetbootin and did LVM with full disk encryption. The install worked just fine, but when I rebooted the laptop said "invalid partition table." Hrm. So I tried to boot again from the USB stick and this time it booted normally and "/" is the encrypted internal SSD. So it looks like grub installed to the USB stick instead of the internal drive. 

So I tried "sudo install-grub /dev/sda" and that worked but when I reboot still "invalid partition table."

here is what mount looks like currently:

```

[COLOR=#3c3c3c]/dev/mapper/warezportable--vg-root on / type ext4 (rw,errors=remount-ro)[/COLOR]
[COLOR=#3c3c3c]proc on /proc type proc (rw,noexec,nosuid,nodev)[/COLOR]
[COLOR=#3c3c3c]sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)[/COLOR]
[COLOR=#3c3c3c]none on /sys/fs/cgroup type tmpfs (rw)[/COLOR]
[COLOR=#3c3c3c]none on /sys/fs/fuse/connections type fusectl (rw)[/COLOR]
[COLOR=#3c3c3c]none on /sys/kernel/debug type debugfs (rw)[/COLOR]
[COLOR=#3c3c3c]none on /sys/kernel/security type securityfs (rw)[/COLOR]
[COLOR=#3c3c3c]udev on /dev type devtmpfs (rw,mode=0755)[/COLOR]
[COLOR=#3c3c3c]devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)[/COLOR]
[COLOR=#3c3c3c]tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)[/COLOR]
[COLOR=#3c3c3c]none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)[/COLOR]
[COLOR=#3c3c3c]none on /run/shm type tmpfs (rw,nosuid,nodev)[/COLOR]
[COLOR=#3c3c3c]none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)[/COLOR]
[COLOR=#3c3c3c]none on /sys/fs/pstore type pstore (rw)[/COLOR]
[COLOR=#3c3c3c]/dev/sda1 on /boot type ext2 (rw)[/COLOR]
[COLOR=#3c3c3c]systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)[/COLOR]
[COLOR=#3c3c3c]gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ben)[/COLOR]
[COLOR=#3c3c3c]/dev/sdb1 on /media/ben/A1FD-2677 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

```

What can I do here? Booting always with this 4GB thumb drive seems impractical at best.[/COLOR]

---

