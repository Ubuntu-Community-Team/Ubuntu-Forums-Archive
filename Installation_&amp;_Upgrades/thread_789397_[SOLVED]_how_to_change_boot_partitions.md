---
title: "[SOLVED] how to change boot partitions?"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by jsimerly on 2008-05-10
During upgrade from 7.10 to 8.04, new 2.6.24 kernels and menu entries were added to the /boot directory on the LVM-controlled / file system.  However, I originally set my system up in 6.06 to boot from a non-LVM-controlled partition /dev/sda1.  This /boot directory never gets updated on a running system because the LVM-controlled / root directory which contains its own /boot overmounts the /dev/sda1 /boot directory.  Subsequently, I have a Hardy installation that can run only the 2.6.22 and earlier kernels.  How do I fix this?  Do I simply boot using Live CD and copy contents of LVM /boot over the contents of /dev/sda1-controlled /boot?  I have a bad feeling that I would end up with an unbootable system if I did this.

Any fixes or suggestions are welcome.

---

### Post by lemming465 on 2008-05-10
If you post the output of ```
cat /etc/fstab; sudo blkid; sudo fdisk -l
``` we can be more specific.

There is no problem I'm aware of having /boot be a separate mount point, though in Ubuntu you'd have to use manual partitioning to get that.  (Whereas Redhat tends to do that by default).  From your description, it sounds like the hardy upgrade didn't mount the old /dev/sda1 partition on /boot, which is probably an upgrade bug.  If there is no entry for mount /dev/sda1 on /boot in /etc/fstab, that would tend to confirm the theory.  If so, you can fix that after the fact with something along the lines of
```
sudo -i
mkdir /newboot
mount /dev/sda1 /newboot
cp -a /boot/. /newboot  # warning: replaces former menu.lst
mv /boot /oldboot
mkdir /boot
umount /newboot
cp /etc/fstab /etc/fstab.bak
echo "/dev/sda1  /boot ext3 defaults 0 1" >>/etc/fstab  # >> not >, very important
mount /boot
grub-install hd0
```

---

### Post by jsimerly on 2008-05-10
root@harmony12:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/rootvg-root_lv /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1 -- converted during upgrade to edgy
UUID=89fde834-d7dd-4b97-9ebb-88f4f503ab11 /boot ext3 defaults 0 2
/dev/mapper/home_data_vg-home_lv /home           ext3    defaults        0       2
/dev/mapper/home_data_vg-opt_lv /opt            ext3    defaults        0       2
/dev/mapper/home_data_vg-src_lv /source         ext3    defaults        0       2
/dev/mapper/home_data_vg-srv_lv /srv            ext3    defaults        0       2
/dev/mapper/home_data_vg-tmp_lv /tmp            ext3    defaults        0       2
/dev/mapper/rootvg-usr_lv /usr            ext3    defaults        0       2
/dev/mapper/home_data_vg-usr_local_lv /usr/local      ext3    defaults        0       2
/dev/mapper/home_data_vg-var_lv /var            ext3    defaults        0       2
/dev/mapper/home_data_vg-var_log_lv /var/log        ext3    defaults        0       2
/dev/mapper/home_data_vg-backup /backup        ext3    defaults         0       2
/dev/mapper/rootvg-swap_lv none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

root@harmony12:~# blkid
/dev/mapper/rootvg-swap_lv: TYPE="swap" 
/dev/evms/lvm2/rootvg/root_lv: UUID="496b67a8-a8cd-40fc-bd68-f6f0e57627dd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/lvm2/home_data_vg/home_lv: UUID="fa6ece5a-2824-4e76-b8b3-ed37e93b848f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/home_data_vg-opt_lv: UUID="2ac8effc-276b-45df-a320-b8d07779e026" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/lvm2/home_data_vg/opt_lv: UUID="2ac8effc-276b-45df-a320-b8d07779e026" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/home_data_vg-tmp_lv: UUID="be538823-702d-4b3c-887b-0bfe75094e12" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/lvm2/home_data_vg/tmp_lv: UUID="be538823-702d-4b3c-887b-0bfe75094e12" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/home_data_vg-home_lv: UUID="fa6ece5a-2824-4e76-b8b3-ed37e93b848f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/home_data_vg-var_log_lv: UUID="ecbf7813-5b36-4a3c-ac4d-988ad50c46a8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/rootvg-usr_lv: UUID="37b2247a-d053-4367-b0d1-ac66ab21a581" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/home_data_vg-srv_lv: UUID="69464b0e-8ab3-40e1-8703-d3a124856a84" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/home_data_vg-usr_local_lv: UUID="e20bc4b3-ebbd-4e86-808f-87885e3a87b2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/lvm2/home_data_vg/srv_lv: UUID="69464b0e-8ab3-40e1-8703-d3a124856a84" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/lvm2/rootvg/usr_lv: UUID="37b2247a-d053-4367-b0d1-ac66ab21a581" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/lvm2/home_data_vg/var_log_lv: UUID="ecbf7813-5b36-4a3c-ac4d-988ad50c46a8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/lvm2/home_data_vg/usr_local_lv: UUID="e20bc4b3-ebbd-4e86-808f-87885e3a87b2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/sda1: UUID="89fde834-d7dd-4b97-9ebb-88f4f503ab11" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/home_data_vg-var_lv: UUID="bffbd2cf-ebbb-4709-881b-c8b963440952" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/home_data_vg-src_lv: UUID="53188514-4f91-4c5d-a430-1c1dc214953c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/lvm2/home_data_vg/var_lv: UUID="bffbd2cf-ebbb-4709-881b-c8b963440952" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/lvm2/rootvg/swap_lv: TYPE="swap" 
/dev/evms/lvm2/home_data_vg/src_lv: UUID="53188514-4f91-4c5d-a430-1c1dc214953c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: UUID="89fde834-d7dd-4b97-9ebb-88f4f503ab11" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/lvm2|rootvg|root_lv: UUID="496b67a8-a8cd-40fc-bd68-f6f0e57627dd" TYPE="ext3" 
/dev/mapper/rootvg-root_lv: UUID="496b67a8-a8cd-40fc-bd68-f6f0e57627dd" TYPE="ext3" 
/dev/mapper/lvm2|home_data_vg|home_lv: UUID="fa6ece5a-2824-4e76-b8b3-ed37e93b848f" TYPE="ext3" 
/dev/mapper/lvm2|home_data_vg|opt_lv: UUID="2ac8effc-276b-45df-a320-b8d07779e026" TYPE="ext3" 
/dev/mapper/home_data_vg-backup: UUID="1a64ff51-8255-4d29-bb14-7e99f5e48b75" TYPE="ext3" 
/dev/mapper/lvm2|home_data_vg|tmp_lv: UUID="be538823-702d-4b3c-887b-0bfe75094e12" TYPE="ext3" 
/dev/mapper/lvm2|home_data_vg|backup: UUID="1a64ff51-8255-4d29-bb14-7e99f5e48b75" TYPE="ext3" 
/dev/mapper/lvm2|rootvg|usr_lv: UUID="37b2247a-d053-4367-b0d1-ac66ab21a581" TYPE="ext3" 
/dev/mapper/lvm2|home_data_vg|var_log_lv: UUID="ecbf7813-5b36-4a3c-ac4d-988ad50c46a8" TYPE="ext3" 
/dev/mapper/lvm2|rootvg|swap_lv: TYPE="swap" 
/dev/mapper/lvm2|home_data_vg|src_lv: UUID="53188514-4f91-4c5d-a430-1c1dc214953c" TYPE="ext3" 
/dev/sda5: UUID="C4k8p3-L1rl-NIcc-cI5m-xYmO-YIFW-E472FD" TYPE="lvm2pv" 
/dev/sdb5: UUID="DqmprJ-WH63-dewK-hlYw-GiyA-sTw5-ruNltn" TYPE="lvm2pv" 
/dev/mapper/sdb5: UUID="DqmprJ-WH63-dewK-hlYw-GiyA-sTw5-ruNltn" TYPE="lvm2pv" 
/dev/mapper/sda5: UUID="C4k8p3-L1rl-NIcc-cI5m-xYmO-YIFW-E472FD" TYPE="lvm2pv"

root@harmony12:~# fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000024f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          18      144553+  83  Linux
/dev/sda2              19        9039    72461182+   5  Extended
/dev/sda5              19        9039    72461151   8e  Linux LVM

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00020a8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    5  Extended
/dev/sdb5               1       36483   293049634+  8e  Linux LVM

---

### Post by lemming465 on 2008-05-11
Ok, your fstab has
> UUID=89fde834-d7dd-4b97-9ebb-88f4f503ab11 /boot ext3 defaults 0 2
which ought to be mounting sda1 as /boot.  Does it?

---

### Post by jsimerly on 2008-05-11
I don't know what successfully mounts.  Once the kernel-loading grub screen disappears, the system displays an error message saying that the mount of /dev/sda1 has failed because /boot is already mounted.

On a hard-drive-booted system, I get the same error:

root@harmony12:~# mount /dev/sda1 /boot
mount: /dev/sda1 already mounted or /boot busy


The only way I can access the files on /dev/sda1 is to boot into the Live CD.

---

### Post by lemming465 on 2008-05-13
> I don't know what successfully mounts.
If you get any kind of command prompt, even from initramfs, try *cat /proc/mounts* to find out.

I notice that [Evms is deprecated]("https://wiki.ubuntu.com/Evms"); the symptoms they describe match your situation.

---

### Post by jsimerly on 2008-05-16
root@harmony12:~# cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/mapper/rootvg-root_lv / ext3 rw,data=ordered 0 0
/dev/mapper/rootvg-root_lv /dev/.static/dev ext3 rw,data=ordered 0 0
none /sys sysfs rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/mapper/home_data_vg-home_lv /home ext3 rw,data=ordered 0 0
/dev/mapper/home_data_vg-opt_lv /opt ext3 rw,data=ordered 0 0
/dev/mapper/home_data_vg-src_lv /source ext3 rw,data=ordered 0 0
/dev/mapper/home_data_vg-srv_lv /srv ext3 rw,data=ordered 0 0
/dev/mapper/home_data_vg-tmp_lv /tmp ext3 rw,data=ordered 0 0
/dev/mapper/rootvg-usr_lv /usr ext3 rw,data=ordered 0 0
/dev/mapper/home_data_vg-usr_local_lv /usr/local ext3 rw,data=ordered 0 0
/dev/mapper/home_data_vg-var_lv /var ext3 rw,data=ordered 0 0
/dev/mapper/home_data_vg-var_log_lv /var/log ext3 rw,data=ordered 0 0
/dev/mapper/home_data_vg-backup /backup ext3 rw,data=ordered 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0

---

### Post by lemming465 on 2008-05-17
There is no sign of either /boot or /dev/sda1 in your /proc/mounts list.  If it's complaining that it is already mounted, it must be going on the rootfs from the initial ram disk instead of the /dev/mapper/rootvg-root_lv.

What do you get from *umount /dev/sda; mkdir /newboot; mount -v /dev/sda1 /newboot*

---

### Post by jsimerly on 2008-05-17
root@harmony12:~# umount /dev/sda1
umount: /dev/sda1: not mounted

---

### Post by lemming465 on 2008-05-17
right, but what happens with *mkdir /newboot; mount -v /dev/sda1 /newboot*?

And then how does *ls -l* compare on /newboot versus /boot?

---

### Post by jsimerly on 2008-05-18
root@harmony12:~# mkdir /newboot
root@harmony12:~# mount -v /dev/sda1 /newboot
mount: you didn't specify a filesystem type for /dev/sda1
       I will try type ext3
mount: /dev/sda1 already mounted or /newboot busy
root@harmony12:~# ls -l /newboot
total 0
root@harmony12:~# ls -l /boot
total 85428
-rw-r--r-- 1 root root  414274 2008-02-12 00:19 abi-2.6.20-16-generic
-rw-r--r-- 1 root root  424317 2008-02-12 04:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root  422607 2008-04-10 11:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root  422667 2008-05-01 12:59 abi-2.6.24-17-generic
-rw-r--r-- 1 root root   83217 2008-02-11 20:45 config-2.6.20-16-generic
-rw-r--r-- 1 root root   75311 2008-02-12 04:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root   79964 2008-04-10 11:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root   80071 2008-05-01 12:59 config-2.6.24-17-generic
drwxr-xr-x 2 root root    4096 2008-05-10 16:55 grub
-rw-r--r-- 1 root root 9148905 2008-05-03 19:16 initrd.img-2.6.20-16-generic
-rw-r--r-- 1 root root 9148142 2008-05-02 21:30 initrd.img-2.6.20-16-generic.bak
-rw-r--r-- 1 root root 9141046 2008-05-03 19:17 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root 9140998 2008-05-02 21:29 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root 9468530 2008-05-03 19:24 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 9468613 2008-05-02 21:29 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root 9468644 2008-05-07 08:49 initrd.img-2.6.24-17-generic
-rw-r--r-- 1 root root 9468576 2008-05-05 08:58 initrd.img-2.6.24-17-generic.bak
-rw-r--r-- 1 root root  807071 2008-02-12 00:20 System.map-2.6.20-16-generic
-rw-r--r-- 1 root root  823535 2008-02-12 04:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root  899892 2008-04-10 11:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root  905012 2008-05-01 12:59 System.map-2.6.24-17-generic
-rw-r--r-- 1 root root 1747532 2008-02-12 00:19 vmlinuz-2.6.20-16-generic
-rw-r--r-- 1 root root 1764536 2008-02-12 04:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 11:51 vmlinuz-2.6.24-16-generic
-rw-r--r-- 1 root root 1921944 2008-05-01 12:59 vmlinuz-2.6.24-17-generic

---

### Post by jsimerly on 2008-05-18
Lemming, thanks for your help and patience.  Your reply regarding the EVM deprecation, its link, and its contents were highly valuable.  I got around the complexity of uninstalling EVM by simply reinstalling 8.04 with the Alternate CD and letting it format all system partitions.  All of my important user data and settings in /home survived the reinstallation.  The various upgrades from 6.06 to 8.04 and their installations of EVM must have really conflicted with the existing LVM setup.  As you can see, the new fstab is really straightforward:

root@harmony12:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/rootvg-root_lv
UUID=c82b809b-d8b4-49b3-87d9-efcd1e37cfd1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/mapper/home_data_vg-backup
UUID=1a64ff51-8255-4d29-bb14-7e99f5e48b75 /backup         ext3    relatime        0       2
# /dev/sda1
UUID=f5c8d62d-be3f-457d-95ff-df4bd53d9b5b /boot           ext3    relatime        0       2
# /dev/mapper/home_data_vg-home_lv
UUID=fa6ece5a-2824-4e76-b8b3-ed37e93b848f /home           ext3    relatime        0       2
# /dev/mapper/home_data_vg-opt_lv
UUID=936e568c-a6cc-41e6-9b68-296d94a055d9 /opt            ext3    relatime        0       2
# /dev/mapper/home_data_vg-src_lv
UUID=58abe82d-f5d4-44af-953f-5801b066d4f6 /src            ext3    relatime        0       2
# /dev/mapper/home_data_vg-srv_lv
UUID=69464b0e-8ab3-40e1-8703-d3a124856a84 /srv            ext3    relatime        0       2
# /dev/mapper/home_data_vg-tmp_lv
UUID=852f7a26-390d-4293-a2fc-0f8f72d5fb5e /tmp            ext3    relatime        0       2
# /dev/mapper/rootvg-usr_lv
UUID=669b98c0-e109-4d65-b8bd-56d3e5aef683 /usr            ext3    relatime        0       2
# /dev/mapper/home_data_vg-usr_local_lv
UUID=e20bc4b3-ebbd-4e86-808f-87885e3a87b2 /usr/local      ext3    relatime        0       2
# /dev/mapper/home_data_vg-var_lv
UUID=3510bf4f-e3d7-4518-81e0-d6027e3c39e4 /var            ext3    relatime        0       2
# /dev/mapper/home_data_vg-var_log_lv
UUID=360fb551-c257-4a2b-90b2-88c56458cc09 /var/log        ext3    relatime        0       2
# /dev/mapper/rootvg-swap_lv
UUID=552239da-e5ab-4164-8f8a-d5e6034ca999 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


New blkid output, compared to the bungled mess it was before.

root@harmony12:~# blkid
/dev/mapper/rootvg-swap_lv: TYPE="swap" UUID="552239da-e5ab-4164-8f8a-d5e6034ca999" 
/dev/mapper/rootvg-root_lv: UUID="c82b809b-d8b4-49b3-87d9-efcd1e37cfd1" TYPE="ext3" 
/dev/mapper/home_data_vg-opt_lv: UUID="936e568c-a6cc-41e6-9b68-296d94a055d9" TYPE="ext3" 
/dev/mapper/home_data_vg-backup: UUID="1a64ff51-8255-4d29-bb14-7e99f5e48b75" TYPE="ext3" 
/dev/mapper/home_data_vg-tmp_lv: UUID="852f7a26-390d-4293-a2fc-0f8f72d5fb5e" TYPE="ext3" 
/dev/mapper/home_data_vg-home_lv: UUID="fa6ece5a-2824-4e76-b8b3-ed37e93b848f" TYPE="ext3" 
/dev/mapper/home_data_vg-var_log_lv: UUID="360fb551-c257-4a2b-90b2-88c56458cc09" TYPE="ext3" 
/dev/mapper/rootvg-usr_lv: UUID="669b98c0-e109-4d65-b8bd-56d3e5aef683" TYPE="ext3" 
/dev/mapper/home_data_vg-srv_lv: UUID="69464b0e-8ab3-40e1-8703-d3a124856a84" TYPE="ext3" 
/dev/mapper/home_data_vg-usr_local_lv: UUID="e20bc4b3-ebbd-4e86-808f-87885e3a87b2" TYPE="ext3" 
/dev/mapper/home_data_vg-var_lv: UUID="3510bf4f-e3d7-4518-81e0-d6027e3c39e4" TYPE="ext3" 
/dev/mapper/home_data_vg-src_lv: UUID="58abe82d-f5d4-44af-953f-5801b066d4f6" TYPE="ext3" 
/dev/sda1: UUID="f5c8d62d-be3f-457d-95ff-df4bd53d9b5b" TYPE="ext3" 
/dev/sda5: UUID="C4k8p3-L1rl-NIcc-cI5m-xYmO-YIFW-E472FD" TYPE="lvm2pv" 
/dev/sdb5: UUID="DqmprJ-WH63-dewK-hlYw-GiyA-sTw5-ruNltn" TYPE="lvm2pv" 
/dev/sdc1: UUID="9801261f-1df3-4dc0-9d6b-91503bfe91cb" TYPE="ext3"

---

