---
title: "Found &quot;OS&quot; in the mounted devices"
date: 2019-01-24
forum: Installation &amp; Upgrades
---

### Post by yucinext2cloud on 2019-01-24
I am on Ubuntu 16.04 LTS

To remove python from PC I did

```
sudo apt-get purge python*
```

I realised the damage It is doing and aborted it in the middle, I ran the following

```
sudo apt-get install software-center
sudo apt-get install gnome-software
sudo apt-get install ubuntu-desktop
```

Now my PC is working fine but I found "OS" in mounted devices, Please see the picture below.

[ATTACH=CONFIG]282300[/ATTACH]

**How do I remove/unmount it permanently so that it doesn't show up?**

---

### Post by sisco311 on 2019-01-24
Hi, yucinext2cloud,

and welcome to the forums!

Is OS an actual partition which did not show up in the file manager before?

Please post the output of:
```
cat /etc/fstab
```
```
mount
```and
```
blkid
```

---

### Post by yucinext2cloud on 2019-01-24
Hello, Thank you!

"OS" didn't show up before and It happened only after I ran the commands I mentioned.

The output of cat /etc/fstab

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/nvme0n1p3 during installation
UUID=b68d69e4-e27b-402b-aadf-d2d72f09e713 / ext4 errors=remount-ro 0 1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=6683-6A19 /boot/efi vfat umask=0077 0 1
# swap was on /dev/nvme0n1p4 during installation
UUID=d325acc8-04a1-49c5-ab63-9c184f030530 none swap sw 0 0

```

The output of mount
```
mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8055132k,nr_inodes=2013783,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1615416k,mode=755)
/dev/nvme0n1p3 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/var/lib/snapd/snaps/firefox_159.snap on /snap/firefox/159 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/chromium-ffmpeg_5.snap on /snap/chromium-ffmpeg/5 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/atom_210.snap on /snap/atom/210 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/firefox_152.snap on /snap/firefox/152 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/atom_209.snap on /snap/atom/209 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core_6034.snap on /snap/core/6034 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/chromium-ffmpeg_9.snap on /snap/chromium-ffmpeg/9 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/firefox_167.snap on /snap/firefox/167 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/atom_211.snap on /snap/atom/211 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/chromium-ffmpeg_8.snap on /snap/chromium-ffmpeg/8 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core_5897.snap on /snap/core/5897 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core_6130.snap on /snap/core/6130 type squashfs (ro,nodev,relatime)
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
overlay on /var/lib/docker/overlay2/e531b105bae721f9a44e08d2101bc9a7487da4ffede4fcf586b704b89792b665/merged type overlay (rw,relatime,lowerdir=/var/lib/docker/overlay2/l/VY5ENM4UCIK6YG5IRHL56ZTUNK:/var/lib/docker/overlay2/l/LBJBONO7DHTX2B2ZPYX4JZSXNQ:/var/lib/docker/overlay2/l/DMDKMX4MOEB6GLVANMZRDBU7DA:/var/lib/docker/overlay2/l/GBWPM3D3EOE4P773VCKOQT3WSG:/var/lib/docker/overlay2/l/C5AJMWHEMMH6XJYZMIX4M4U3TZ:/var/lib/docker/overlay2/l/ZTOC62765CH5XN3W7A5GYVKTPS:/var/lib/docker/overlay2/l/RS4VMLNFJFJPDRW7DN5ZFHHVIL:/var/lib/docker/overlay2/l/Y5DU7CP3LMA7OCMMUGV5U5SVUF:/var/lib/docker/overlay2/l/6Y5AZKZ6X6EPY5LWBVXOJ2PW2U:/var/lib/docker/overlay2/l/IYWRL4TVUO7PDTIXFGAWR3QB2Z,upperdir=/var/lib/docker/overlay2/e531b105bae721f9a44e08d2101bc9a7487da4ffede4fcf586b704b89792b665/diff,workdir=/var/lib/docker/overlay2/e531b105bae721f9a44e08d2101bc9a7487da4ffede4fcf586b704b89792b665/work)
overlay on /var/lib/docker/overlay2/49d3d2d3894654c7ddea8878bda162b8abc56c834127dd20f65bb8d065afff45/merged type overlay (rw,relatime,lowerdir=/var/lib/docker/overlay2/l/REABCSF3WKE2HQZFD7FR3I6YC2:/var/lib/docker/overlay2/l/HSZQV3K6LD65T7DG2YSTTYWHI7:/var/lib/docker/overlay2/l/OWJCLT2DHIP6TICWK6QG5AOOIH:/var/lib/docker/overlay2/l/WNK5T7VB64WU5IN2MOBQQ7SI77:/var/lib/docker/overlay2/l/KKG75HOI4VBCUBHIDYX3GDGE5Q:/var/lib/docker/overlay2/l/PSXJDZBNNFY4VK5TFZMYUQQL5A:/var/lib/docker/overlay2/l/IN4KNBYLYOV5OUHFATLDJRTAUK,upperdir=/var/lib/docker/overlay2/49d3d2d3894654c7ddea8878bda162b8abc56c834127dd20f65bb8d065afff45/diff,workdir=/var/lib/docker/overlay2/49d3d2d3894654c7ddea8878bda162b8abc56c834127dd20f65bb8d065afff45/work)
overlay on /var/lib/docker/overlay2/11b4bd626f2b7b9dfa8d8c7b109b4ce93493b1f33162f75509907b2da3fc6c1d/merged type overlay (rw,relatime,lowerdir=/var/lib/docker/overlay2/l/VMYOLN5KLPBJR5YYMR5ZT53JJ6:/var/lib/docker/overlay2/l/BAYT62EHFBZJ6US2UMKGPGFDH7:/var/lib/docker/overlay2/l/4VSZF45RLTPEDBSPXXJXSI3QVE:/var/lib/docker/overlay2/l/SQ6IDSK323ZNI7FXIRU6XRTOMT:/var/lib/docker/overlay2/l/R5DAJ2EZUZ7J2VBJSUZC7CSSDS:/var/lib/docker/overlay2/l/K4TWAD2DZLJBT7B5D7MKPWOLP2:/var/lib/docker/overlay2/l/TNP2MGW6YAUSPZKKMIL72LQTZD:/var/lib/docker/overlay2/l/IUJ33DUIL6OLRERMH4S66JVPQ6:/var/lib/docker/overlay2/l/KHMR53FL5C4YS3P7XDRNID4NII:/var/lib/docker/overlay2/l/IGMEDZWRWOXHOEIMDFWNADQ3WE:/var/lib/docker/overlay2/l/HJ6P3AHHYWOVT5QGSLPJYMDBKC:/var/lib/docker/overlay2/l/RTJTM7U2KN2SZ4JAMPRM42B32Q:/var/lib/docker/overlay2/l/IO3JXJNFD3FMWOMC2SNHSJ6YO4:/var/lib/docker/overlay2/l/ISPRWBJTOS7PETXG4KWR3CCTAW:/var/lib/docker/overlay2/l/FNPMCKDVZBZPYGRY5DLHAOSACI:/var/lib/docker/overlay2/l/JQFCYTHMSURX6O7YQ5DGKPGAOK:/var/lib/docker/overlay2/l/IPBCJASAGSG7HRQTGMBJYBQFE4:/var/lib/docker/overlay2/l/QAIG7OE5JDFHCZEBR24ZKTK6I4:/var/lib/docker/overlay2/l/SUFIKLB4JAOUDOUXDJ47TU4EGE:/var/lib/docker/overlay2/l/ZXNKBUXHLWGFKZWAHBUB4QISEY:/var/lib/docker/overlay2/l/DQRWCH7QQDXWTEDO5QN4HFLGX7,upperdir=/var/lib/docker/overlay2/11b4bd626f2b7b9dfa8d8c7b109b4ce93493b1f33162f75509907b2da3fc6c1d/diff,workdir=/var/lib/docker/overlay2/11b4bd626f2b7b9dfa8d8c7b109b4ce93493b1f33162f75509907b2da3fc6c1d/work)
shm on /var/lib/docker/containers/81d4b439d4a41b7bd067b84de9aa4b9a5e01e92fe90c68fe5f4d6eced5976fab/mounts/shm type tmpfs (rw,nosuid,nodev,noexec,relatime,size=65536k)
shm on /var/lib/docker/containers/0b8fa9a88d07a242c046f0d254fa16c2e586d9726ebe6d5bd7f113117393bc21/mounts/shm type tmpfs (rw,nosuid,nodev,noexec,relatime,size=65536k)
shm on /var/lib/docker/containers/2191b1460ea2422c7303d8a86a4222f056964124db74c917ed8fd88ea7caf413/mounts/shm type tmpfs (rw,nosuid,nodev,noexec,relatime,size=65536k)
nsfs on /run/docker/netns/c0d5f23c13eb type nsfs (rw)
nsfs on /run/docker/netns/7c064bcfd212 type nsfs (rw)
nsfs on /run/docker/netns/88290e96be9b type nsfs (rw)
tmpfs on /run/user/1001 type tmpfs (rw,nosuid,nodev,relatime,size=1615416k,mode=700,uid=1001,gid=1001)
gvfsd-fuse on /run/user/1001/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1001,group_id=1001)
/dev/nvme0n1p2 on /media/yucinext2cloud/OS type vfat (rw,nosuid,nodev,relatime,uid=1001,gid=1001,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)

```
The output of blkid
```
sudo blkid
/dev/nvme0n1p1: LABEL="ESP" UUID="6683-6A19" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="b0ded393-d1b7-4e89-8d68-daf0db46131b"
/dev/nvme0n1p2: LABEL="OS" UUID="C4AA-E0FF" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="a7a644c9-c5d0-4ff7-8efb-8647662edf45"
/dev/nvme0n1p3: LABEL="UBUNTU" UUID="b68d69e4-e27b-402b-aadf-d2d72f09e713" TYPE="ext4" PARTUUID="7bd264bc-94c4-4555-acdf-1f03289c1270"
/dev/nvme0n1p4: UUID="d325acc8-04a1-49c5-ab63-9c184f030530" TYPE="swap" PARTUUID="154d0239-89f4-4e59-afa9-649ffba1ea7a"

```

---

### Post by slickymaster on 2019-01-24
_@yucinext2cloud_:
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

Also, Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output because when it's posted as plain text it loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of 'Code' tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by ajgreeny on 2019-01-24
If you right click on the OS in nautilus and choose Properties it may give you some clues about this OS entry, so copy back here any info it shows you.

---

### Post by yucinext2cloud on 2019-01-24
Thank you, Noted!

The properties of "OS" are as follows:

```
Name: OS
Type: Folder (inode/directory)
Contents: 936 items, totalling 2.2 GB

Location: /media/yucinext2cloud
Volume: OS

Total capacity: 3.2 GB
Filesystem type: msdos
```

---

### Post by oldfred on 2019-01-24
You show this in mounted partitions.
Did you have a partition with label OS? When you automount with Naulitus, it defaults to UUID or label, if you have labeled it.

```
/dev/nvme0n1p2 on /media/yucinext2cloud/[COLOR=#ff0000]OS[/COLOR] type vfat (rw,nosuid,nodev,relatime,uid=1001,gid=1001,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
```

---

### Post by sisco311 on 2019-01-24
You can change the mount options of the partition in gnome-disks (a.k.a GNOME Disk Utility or palimpsest).
```
gnome-disks --block-device /dev/disk/by-label/OS
```
Click the *gears* icon and select "Edit Mount Options...".  Enable the **User Session Defaults** option if needed and untick the *Mount at system startup* and *Show in user interface* options.

---

