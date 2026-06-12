---
title: "Installing ubuntu server on btrfs to make/restore snapshots"
date: 2022-10-04
forum: Installation &amp; Upgrades
---

### Post by sopsop on 2022-10-04
[https://www.youtube.com/watch?v=_sLSiL3oynk&t=329s](https://www.youtube.com/watch?v=_sLSiL3oynk&t=329s)
Found a video about howto setup ubuntu desktop version on btrfs and make&restore snapshots. But I am not experinced enough to make it on ubuntu server.
I tried to repeat steps from video on server version but there are no such files like btrfs70 available

also found this info 

> If you want to use Timeshift it's important to note that it requires "an Ubuntu-type subvolume layout (with @ and @home subvolumes)."

You don't need to reinstall your system. Let's assume that your BTRFS root partition is /dev/sda2. In order to create a @ subvolume and several other subvolumes the following procedure should work:


sudo mount /dev/sda2 /mnt
sudo btrfs sub create /mnt/@
sudo btrfs sub create /mnt/@home
sudo btrfs sub create /mnt/@cache
sudo btrfs sub create /mnt/@log
sudo btrfs sub create /mnt/@tmp


... whatever ..


sudo umount /mnt
Then add the following entries to your fstab:


UUID=xyz /              btrfs   subvol=@,defaults,noatime,space_cache,autodefrag,compress=zstd 0 1
UUID=xyz /home          btrfs   subvol=@home,defaults,noatime,space_cache,autodefrag,compress=zstd 0 2
UUID=xyz /var/cache     btrfs   subvol=@cache,defaults,noatime,space_cache,autodefrag,compress=zstd 0 2
UUID=xyz /var/log       btrfs   subvol=@log,defaults,noatime,space_cache,autodefrag,compress=zstd 0 2
UUID=xyz /var/tmp       btrfs   subvol=@tmp,defaults,noatime,space_cache,autodefrag,compress=zstd 0 2
Needless to say, that you should replace xyz with your real UUID for your BTRFS partition which you can find with sudo blkid

Making so, I managed to make snapshots but when I try to restore em, i get an error "Segmentation fault"

Can anyone point me, what my problem is atm
fstab
```

UUID="b7845e07-1534-4d8f-a3a4-a5d88cb518d2" /           btrfs   subvol=@,defaults,noatime,space_cache,autodefrag,compress=zstd 0 1
UUID="b7845e07-1534-4d8f-a3a4-a5d88cb518d2" /home       btrfs   subvol=@home,defaults,noatime,space_cache,autodefrag,compress=zstd 0 2

```
sudo btrfs sub list /
```

ID 256 gen 150 top level 5 path @
ID 257 gen 100 top level 5 path @home
ID 258 gen 86 top level 5 path @data
ID 264 gen 123 top level 5 path timeshift-btrfs/snapshots/2022-10-04_10-26-05/@
ID 267 gen 138 top level 5 path timeshift-btrfs/snapshots/2022-10-04_11-02-08/@
ID 268 gen 141 top level 5 path timeshift-btrfs/snapshots/2022-10-04_11-03-59/@
ID 269 gen 150 top level 5 path timeshift-btrfs/snapshots/2022-10-04_11-08-38/@

```

Thank you in advance.
ALready thinking of just to install usual ubuntu without gui. dunno what the difference between this option and server but if noone helps, that's my last resort..

---

### Post by TheFu on 2022-10-04
If you will have more than 1 disk connected and using btrfs, beware.  [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/)

The long-standing method for Linux servers to have volume management with snapshots is to use LVM2.  If you care about your data, definitely use that instead of the other 2 options, btrfs or zfs.

Zfs is great for data storage and brings lots of capabilities, but it isn't integrated with Ubuntu to make using it for your OS recommended.  Lots of ZFS zealots do use it that way, but they also run into problems that have to be manually corrected, especially during OS upgrades.

Btrfs has some issues with running CoW VM storage on BTRFS managed storage.  If you don't use virtual machines, then that is likely a non-issue. If you use lxd containers in the recommended way, on ZFS, it definitely is an issue if the ZFS is overlayed on btrfs.

Be careful with your data.  Please.

Also, please understand that snapshots are just a step in the backup process. They are not actually backups until the snapshot is used to get the quiesced data copied to other physical storage - usually a different machine with different storage and later to another machine 500 miles away.  

Far too many backup tools use the term "snapshot" incorrectly.  Snapshots are nearly instant. Backups take 10 seconds to an hour to accomplish.   Don't confuse those two very different processes.

---

