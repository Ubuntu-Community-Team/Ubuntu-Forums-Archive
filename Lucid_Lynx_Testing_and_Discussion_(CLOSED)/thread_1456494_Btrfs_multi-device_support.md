---
title: "Btrfs multi-device support"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by regomodo on 2010-04-17
I have a raid0 setup (non-OS use) and it seems it is impossible to mount automatically on bootup. 

Manually entering 
```
btrfsctl -a && mount -av
``` 
seems to be the only solution which, for me, is useless as I want my /home to be on a subvol of the raid.

Is it possible to use multi-device btrfs volumes in Lucid? Has anybody achieved said task?
I've tried in Gentoo but gave up as those forums are dead.

---

### Post by falconindy on 2010-04-17
You need a boot hook on your initramfs to be able to mount automatically. I've been running a RAID-0 btrfs device as my root partition for several months now with no fuss (on Arch). Somewhere on these forums is a thread by Ibuclaw explaining how to create said hook.

---

### Post by regomodo on 2010-04-17
> **falconindy said:**
> You need a boot hook on your initramfs to be able to mount automatically. I've been running a RAID-0 btrfs device as my root partition for several months now with no fuss (on Arch). Somewhere on these forums is a thread by Ibuclaw explaining how to create said hook.

Cheers. I think [this]("http://ubuntuforums.org/showpost.php?p=8716089&postcount=1") is what you were referring to. Just giving it a try now.

---

### Post by regomodo on 2010-04-17
Oh well, as ever I can't get this to work. Same issue again on bootup; it asks me to skip the mount or do a manual recovery.

Is there anything wrong with how I mount it in my fstab?

> UUID=15af01a8-60f7-4eb2-ba2b-bf72cc957ff8	/media/data	btrfs	subvol=datavol	0	1

Just had a check and I think the issue is in the initramfs

> root@jonno-desktop:~# mount /media/data/
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@jonno-desktop:~# btrfsctl -a
Scanning for Btrfs filesystems
failed to read /dev/sdi
failed to read /dev/sdh
failed to read /dev/sdg
failed to read /dev/sdf
failed to read /dev/sr0
root@jonno-desktop:~# mount -v /media/data/
/dev/sdb on /media/data type btrfs (rw,subvol=datavol)
root@jonno-desktop:~# 



---

### Post by falconindy on 2010-04-17
> **regomodo said:**
> Is there anything wrong with how I mount it in my fstab?

```
UUID=15af01a8-60f7-4eb2-ba2b-bf72cc957ff8	/media/data	btrfs	subvol=datavol	0	1
```

Just had a check and I think the issue is in the initramfs
This line clearly works, as mount -a doesn't complain when its run. The issue is definitely in the initramfs. You need to make sure that the install hook, the boot hook and all the modules are being added to the ramfs.

---

### Post by regomodo on 2010-04-17
> **falconindy said:**
> This line clearly works, as mount -a doesn't complain when its run. The issue is definitely in the initramfs. You need to make sure that the install hook, the boot hook and all the modules are being added to the ramfs.

I can triple check but I had noticed I hadn't done the Grub2 fix. Just did that and still the same error.

Looking in /var/log/messages I see this

> Apr 17 11:28:32 jonno-desktop kernel: [  330.505323] Btrfs loaded
Apr 17 11:28:32 jonno-desktop kernel: [  330.506616] device fsid b24ef760a801af15-f87f95cc72bf2bba devid 1 transid 17292 /dev/sda
Apr 17 11:28:32 jonno-desktop kernel: [  330.507103] btrfs: failed to read the system array on sda
Apr 17 11:28:32 jonno-desktop kernel: [  330.520101] btrfs: open_ctree failed

---

### Post by falconindy on 2010-04-17
That's a familiar error. You're missing one of the crc32 modules in the initramfs. The Grub2 fix is only if you're using BTRFS as root.

---

### Post by regomodo on 2010-04-17
> **falconindy said:**
> That's a familiar error. You're missing one of the crc32 modules in the initramfs. The Grub2 fix is only if you're using BTRFS as root.

Ok, that's one thing less to worry about.

> root@jonno-desktop:~# cat /usr/share/initramfs-tools/modules.d/btrfs
#initramfs modules for btrfs
libcrc32c
crc32c
zlib_deflate
btrfs

root@jonno-desktop:~# 
 I'm not sure where to go from here.

[EDIT] Ah balls. Stupid update-initramfs doesn't mount /boot. My initramfs is there just not in the *real* /boot directory.

---

### Post by regomodo on 2010-04-17
Fixed it! Cheers falconindy.

---

