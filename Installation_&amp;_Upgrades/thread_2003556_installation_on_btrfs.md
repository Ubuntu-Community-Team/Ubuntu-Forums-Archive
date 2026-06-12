---
title: "installation on btrfs"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by HaraldWeber on 2012-06-14
Hi

I installed ubuntu on an btrfs disk. The installer created "@" and "@home" as subvolume. "@" should be / and "@home" should be /home when booted. But "@" is empty and / is directly on /dev/sda5. What went wrong?

Some more Information.
```
# btrfs subvolume list /
ID 256 top level 5 path @
ID 257 top level 5 path @home
```

in /etc/fstab the root partition is mounted in subvolume @ and home is mounted in subvolume @home
```
UUID=... /               btrfs   defaults,subvol=@ 0       1
UUID=... /home           btrfs   defaults,subvol=@home 0       2
```

when i look at my root (/) it looks like this:
```
# ls /
@     cdrom  home        initrd.img.old  media  proc  sbin     sys  var
bin   dev    @home       lib             mnt    root  selinux  tmp  vmlinuz
boot  etc    initrd.img  lib64           opt    run   srv      usr  vmlinuz.old
```

"@" and "@home" shouldn't be there!!
/@ is empty 
/@home is the users dir
/home is also the users dir

#mount says
```
/dev/sda5 on / type btrfs (rw,subvol=@)
/dev/sda5 on /home type btrfs (rw,subvol=@home)
```

Does anybody know why @ is not root and is not populated with files?

---

### Post by HaraldWeber on 2012-06-20
Finally i managed it myself.

I did the following to move the root partition to a btrfs subvolume.

I booted from a live usb-stick.

Mounted the btrfs disk and subvolume 
```
mkdir -p /mnt/btrfs-disk /mnt/btrfs-root
mount /dev/sda5 /mnt/btrfs-disk
mount -o subvol=@ /dev/sda5 /mnt/btrfs-root (my actual root subvolume)
```

Copied the root partition to the '@' subvolume (/mnt/btrfs-root)
```
rsync -raHAX --exclude '@,home, @home and so on' /mnt/btrfs-disk /mnt/btrfs-root
```

Edited grub.conf to boot from subvolume '@' instead of /dev/sda5
```
linux	/**@/**boot/vmlinuz-3.2.0-25-generic root=UUID=0899f4b5-a8d5-4499-95b8-4f075f9cf543 ro **rootflags=subvol=@**   quiet splash $vt_handoff
```

Chrooted into the '@' subvolume
```
mount -o bind /dev /mnt/btrfs-root/dev
mount -o bind /sys /mnt/btrfs-root/sys
mount -t proc /proc /mnt/btrfs-root/proc
cp /proc/mount /mnt/btrfs-root/etc/mtab
chroot /mnt/btrfs-root /bin/bash
```

Then installed and updated Grub
```
grub-install /dev/sda
update-grub

```

Then i moved all directories except '@' and '@home' (subvolumes) to /oldRoot (can be deleted)
reboot and now its working!!

---

### Post by YannBuntu on 2012-06-20
Thanks for the feedback.

Please create a bug report on Launchpad (via "ubuntu-bug linux" for example) and indicate the report URL here so that we can follow up.

---

