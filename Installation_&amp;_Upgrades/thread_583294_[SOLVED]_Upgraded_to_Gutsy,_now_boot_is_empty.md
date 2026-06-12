---
title: "[SOLVED] Upgraded to Gutsy, now /boot is empty"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by neptune on 2007-10-20
Hi,

As far as I can tell, the upgrade from Edgy to Gutsy went fine and completely without errors. The reboot after upgrade also worked fine.

However, after booting into the new Gutsy, I notice that /boot has nothing in it - its completely empty! I tried **ls** as root and there are no files listed. The GRUB folder is gone too. All GRUB files seem to have disappeared as well. I can't make any change to menu.lst because I don't know where it is.

Now I'm terrified to reboot.

Any help is appreciated.

Thanks!

---

### Post by gstool on 2007-10-20
I did a fresh install from the Live CD.  I had checked md5sum and checked the media after burning.  I have done three attempts, with installation seemingly completing, but Grub was not installed on any of the attempts; the first two times I tried to get it to install to the boot record of its / partition, and the last time I let it take over the MBR.  There are some files in /boot, but no grub directory, and the initrd.img file is named initrd.img.bak.

Luckily, my boot is controlled by another Linux system using grub.  I was actually able to make the first attempt boot from the other system's boot menu by removing the ".bak" and setting up a boot section for the system in the other systems menu.lst, using another boot section as an example.

I abandoned that and tried to get a real install to work, unsuccessfully.

Gerry

---

### Post by neptune on 2007-10-20
So anyone have ideas or suggestions on how to fix this? 

Please?

<EDIT>

I decided to restart the system and see what happens.

It seems to be finding GRUB from somewhere and booting.

However, during boot process, it stops and wants the root password to start a maintenance shell and says something about file system checks (not sure, missed some of it).
So I go to the root prompt and type **fsck** but get warning about running it on mounted file system so I don't run it.
I simply exit this shell and system continues to boot.

Any thoughts on this?

Thanks!

</EDIT>

---

### Post by mlind on 2007-10-20
Do you have a separate /boot partition? What's the output of "sudo fdisk -l" (and cat /etc/mtab | grep boot)

---

### Post by neptune on 2007-10-20
Yes, I have a separate /boot partition.

During boot I noticed another anomaly; it said something to the effect "Device already mounted /dev/sda1 or /boot busy" and same for /dev/sda6 (/backup).
I wonder if this is why my /boot is empty? It hasn't actually mounted!

I went into maintenance mode and did **umount /boot** and ran fsck but it couldn't do the check on those two partitions still (/dev/sda1 and /dev/sda6).

Here's some relevant info:

sudo fdisk -l
```
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000774cd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9118    73240303+   5  Extended
/dev/hda5               1        1216     9767457   8e  Linux LVM
/dev/hda6            1217        9118    63472783+  8e  Linux LVM

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02b0d52d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13         620     4883760   83  Linux
/dev/sda3             621        6851    50050507+   5  Extended
/dev/sda5             621         711      730926   82  Linux swap / Solaris
/dev/sda6             712        3143    19535008+  83  Linux
/dev/sda7            3144        6851    29784478+  8e  Linux LVM

```

cat /etc/mtab
```
/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-386/volatile tmpfs rw 0 0

```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1edcebe9-fd5a-4f72-8e16-d5cfa338384c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=04aa73a7-17ee-4499-b9b6-f7ae85b9ee66 /backup         ext3    defaults        0       2
# /dev/sda1
UUID=a43716c7-fcd1-4ab1-a18c-d65f2d049179 /boot           ext3    defaults        0       2
/dev/mapper/vg_linux_01-home /home           ext3    defaults        0       2
/dev/mapper/vg_linux_01-opt /opt            ext3    defaults        0       2
/dev/mapper/vg_storage_01-srv /srv            xfs     defaults        0       2
/dev/mapper/vg_linux_01-tmp /tmp            ext3    defaults        0       2
/dev/mapper/vg_linux_01-usr /usr            ext3    defaults        0       2
/dev/mapper/vg_linux_02-var /var            ext3    defaults        0       2
# /dev/sda5
UUID=ed195ddc-61a9-4d92-8298-bacdd436de4f none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0neptune@i
```

ls -l /dev/disk/by-uuid/
```
total 0
lrwxrwxrwx 1 root root 10 2007-10-20 12:47 04aa73a7-17ee-4499-b9b6-f7ae85b9ee66 -> ../../sda6
lrwxrwxrwx 1 root root 33 2007-10-20 16:47 188ac236-109f-4ad0-989e-05eb22e68258 -> ../../mapper/lvm2|vg_linux_01|tmp
lrwxrwxrwx 1 root root 10 2007-10-20 12:47 1edcebe9-fd5a-4f72-8e16-d5cfa338384c -> ../../sda2
lrwxrwxrwx 1 root root 33 2007-10-20 16:47 5738434c-d0ff-438f-b465-7068e512e55e -> ../../mapper/lvm2|vg_linux_02|var
lrwxrwxrwx 1 root root 35 2007-10-20 16:47 5ed5e1bd-1365-4561-bddf-b1935ce5a625 -> ../../mapper/lvm2|vg_storage_01|srv
lrwxrwxrwx 1 root root 34 2007-10-20 16:47 74b21830-30c0-494b-bf5e-59ae3bdcc3ac -> ../../mapper/lvm2|vg_linux_01|home
lrwxrwxrwx 1 root root 33 2007-10-20 16:47 86d5e1ec-352a-4f98-87db-3a198d752e96 -> ../../mapper/lvm2|vg_linux_01|opt
lrwxrwxrwx 1 root root 33 2007-10-20 16:47 911a6634-3ad5-4cd3-be69-a467ab653e68 -> ../../mapper/lvm2|vg_linux_01|usr
lrwxrwxrwx 1 root root 10 2007-10-20 12:47 a43716c7-fcd1-4ab1-a18c-d65f2d049179 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-10-20 12:47 ed195ddc-61a9-4d92-8298-bacdd436de4f -> ../../sda5

```

---

### Post by mlind on 2007-10-20
hmm,, I cannot see anything wrong in your fstab. Does grub use some other than your /boot partition in groot entry?

Make sure /dev/sda1 is not mounted (which it doesn't seem to), then
```

sudo fsck -f /dev/sda1

```

And then try to mount it 
```

sudo mount /boot

```

Check that groot and kopt in /boot/grub/menu.lst look right. I guess you can get the correct values by looking device.map
```

cat /boot/grub/device.map

```

---

### Post by neptune on 2007-10-20
> **mlind said:**
> hmm,, I cannot see anything wrong in your fstab. Does grub use some other than your /boot partition in groot entry?

I see that the UUID in fstab is different from that in /dev/disk/by-uuid/ for the partitions that are giving me trouble. I think thats the real problem, no? 
Any thoughts on how to fix this?

> **mlind said:**
> Make sure /dev/sda1 is not mounted (which it doesn't seem to), then
```

sudo fsck -f /dev/sda1

```
Says filesystem is mounted and not to run fsck

> **mlind said:**
> And then try to mount it 
```

sudo mount /boot

```
Shouldn't it be **sudo mount /dev/sda1 /boot**? Anyway, I did that and it said sda1 is already mount or /boot is busy

> **mlind said:**
> Check that groot and kopt in /boot/grub/menu.lst look right. I guess you can get the correct values by looking device.map
```

cat /boot/grub/device.map

```
Since /boot isn't mounted properly, I can't get a directory listing.

---

### Post by thediviner on 2007-10-20
I'm having the exact same problem, here's the thread I started: [http://ubuntuforums.org/showthread.php?t=583958](http://ubuntuforums.org/showthread.php?t=583958)

In my case, the fstab UUID's do match the ones in /dev/disk/by-uuid so that might not be the issue. Still haven't found anyone who know's what's wrong though.

---

### Post by thediviner on 2007-10-20
I was finally able to solve my issue by uninstalling all evms and libevms packages. It got rid of the recovery console issue during boot and all my /boot files are back (since it could mount again).

I hope this helps.

---

### Post by neptune on 2007-10-20
> **thediviner said:**
> I'm having the exact same problem, here's the thread I started: [http://ubuntuforums.org/showthread.php?t=583958](http://ubuntuforums.org/showthread.php?t=583958)

In my case, the fstab UUID's do match the ones in /dev/disk/by-uuid so that might not be the issue. Still haven't found anyone who know's what's wrong though.

I corrected the mis-matched UUIDs but the boot up problem is still there.

> **thediviner said:**
> I was finally able to solve my issue by uninstalling all evms and libevms packages. It got rid of the recovery console issue during boot and all my /boot files are back (since it could mount again).

I hope this helps.

I don't even have those installed according to Synaptic! LOL

---

### Post by squidgeboy on 2007-10-21
I had the same problem. It appears to be due to me using LVM. The Gutsy upgrade wiped out my fstab entry for my /boot.
 I notice you too are using LVM. You need to mount using the /dev/mapper/xxxx links.

So for your machine you probably need to change fstab to:

```
/dev/mapper/sda1    /boot           ext3    defaults   0 2
```

---

### Post by neptune on 2007-10-21
Wow! You're a genius my friend.

Your fix worked like a charm! :)

Thanks. This is a great community.

---

