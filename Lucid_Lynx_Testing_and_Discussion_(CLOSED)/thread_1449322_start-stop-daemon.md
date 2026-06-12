---
title: "start-stop-daemon"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by abal1221 on 2010-04-07
I'm running into a little problem installing some apps on a Fresh Install of Ubuntu 10.04.

The software center will return an error and say this should not happen
I've tried manually downloading the .deb packages and running "dpkg -i  ...." and I've also tried to do "apt-get install ... "

Both dpkg and apt-get return an error about can't find "start-stop-daemon"
[I]
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: warning: 'start-stop-daemon' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: warning: 'start-stop-daemon' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.[/I]

I've done a "locate start-stop-daemon" which only returns man pages
I've tried to manually run start-stop-daemon which tells me that it is not installed and I need to do a "sudo apt-get install dpkg".  Tried that and apt reports dpkg is current version

---

### Post by sisco311 on 2010-04-07
Did you remove start-stop-daemon somehow?

What's the output of: 
```
ls -al /sbin
```
and
```
ls -al /var/cache/apt/archives/dpkg*
```?

---

### Post by abal1221 on 2010-04-07
I have not removed anything (intentionally anyway).  I ran an Application Update after installing from DVD prior to trying to install other apps.

directory listings of /sbin and /var/cache/apt/archives/dpkg*

```
ls -al /sbin
total 7608
drwxr-xr-x  2 root root     4096 2010-04-06 21:55 .
drwxr-xr-x 22 root root     4096 2010-04-06 21:31 ..
-rwxr-xr-x  1 root root     5496 2009-12-25 03:26 acpi_available
-rwxr-xr-x  1 root root     5553 2010-01-28 19:01 alsa
-rwxr-xr-x  1 root root    84192 2010-03-25 17:04 alsactl
-rwxr-xr-x  1 root root    10557 2010-03-25 17:04 alsa-utils
-rwxr-xr-x  1 root root     5508 2009-12-25 03:26 apm_available
-rwxr-xr-x  1 root root   783108 2010-03-26 12:03 apparmor_parser
-rwxr-xr-x  1 root root    22072 2010-03-22 14:26 badblocks
-rwxr-xr-x  1 root root    22164 2010-03-22 13:51 blkid
-rwxr-xr-x  1 root root    14424 2010-03-22 13:51 blockdev
-rwxr-xr-x  1 root root    14084 2010-03-22 06:47 bootlogd
-rwxr-xr-x  1 root root   331108 2010-02-16 21:10 brltty
-rwxr-xr-x  1 root root     1416 2010-02-16 21:10 brltty-setup
-rwxr-xr-x  1 root root    56252 2010-03-22 13:51 cfdisk
-rwxr-xr-x  1 root root    13800 2010-02-23 11:01 crda
-rwxr-xr-x  1 root root     5512 2010-03-22 13:51 ctrlaltdel
-rwxr-xr-x  1 root root    78376 2010-03-22 14:26 debugfs
-rwxr-xr-x  1 root root    51016 2010-03-16 20:21 depmod
lrwxrwxrwx  1 root root        9 2010-04-06 21:18 dhclient -> dhclient3
-rwxr-xr-x  1 root root   415516 2010-02-09 05:49 dhclient3
-rwxr-xr-x  1 root root     8634 2010-02-09 05:48 dhclient-script
-rwxr-xr-x  1 root root    48100 2010-02-18 07:51 dmsetup
-rwxr-xr-x  1 root root    50732 2010-01-05 01:19 dosfsck
-rwxr-xr-x  1 root root    46636 2010-01-05 01:19 dosfslabel
-rwxr-xr-x  1 root root    17928 2010-03-22 14:26 dumpe2fs
-rwxr-xr-x  1 root root   176776 2010-03-22 14:26 e2fsck
-rwxr-xr-x  1 root root    13848 2010-03-22 14:26 e2image
-rwxr-xr-x  1 root root    34528 2010-03-22 14:26 e2label
-rwxr-xr-x  1 root root     9708 2010-03-22 14:26 e2undo
-rwxr-xr-x  1 root root    97212 2010-03-22 13:51 fdisk
-rwxr-xr-x  1 root root     5508 2010-03-22 13:51 findfs
-rwxr-xr-x  1 root root    26392 2010-03-22 13:51 fsck
-rwxr-xr-x  1 root root    13788 2010-03-22 13:51 fsck.cramfs
-rwxr-xr-x  1 root root   176776 2010-03-22 14:26 fsck.ext2
-rwxr-xr-x  1 root root   176776 2010-03-22 14:26 fsck.ext3
-rwxr-xr-x  1 root root   176776 2010-03-22 14:26 fsck.ext4
-rwxr-xr-x  1 root root   176776 2010-03-22 14:26 fsck.ext4dev
-rwxr-xr-x  1 root root    26112 2010-03-22 13:51 fsck.minix
lrwxrwxrwx  1 root root        7 2010-04-06 21:18 fsck.msdos -> dosfsck
-rwxr-xr-x  1 root root      333 2010-03-22 06:47 fsck.nfs
lrwxrwxrwx  1 root root        7 2010-04-06 21:18 fsck.vfat -> dosfsck
-rwxr-xr-x  1 root root     5540 2010-03-22 06:47 fstab-decode
-rwxr-xr-x  1 root root    18360 2010-03-22 13:51 getty
lrwxrwxrwx  1 root root        6 2010-04-06 21:18 halt -> reboot
-rwxr-xr-x  1 root root    92776 2009-11-25 06:01 hdparm
-rwxr-xr-x  1 root root    42592 2010-03-22 13:51 hwclock
-rwxr-xr-x  1 root root    65708 2010-02-11 19:38 ifconfig
-rwxr-xr-x  1 root root    38788 2010-02-20 02:02 ifdown
-rwxr-xr-x  1 root root    38788 2010-02-20 02:02 ifquery
-rwxr-xr-x  1 root root    38788 2010-02-20 02:02 ifup
-rwxr-xr-x  1 root root   108204 2010-03-17 19:38 init
-rwxr-xr-x  1 root root   104428 2010-03-17 19:38 initctl
-rwxr-xr-x  1 root root     9512 2010-03-16 20:21 insmod
-rwxr-xr-x  1 root root    55300 2009-11-05 03:57 insserv
-rwxr-xr-x  1 root root     2266 2009-12-08 08:00 installkernel
lrwxrwxrwx  1 root root        7 2010-04-06 21:18 ip -> /bin/ip
-rwxr-xr-x  1 root root    35052 2010-03-05 16:02 ip6tables
-rwxr-xr-x  1 root root    39188 2010-03-05 16:02 ip6tables-restore
-rwxr-xr-x  1 root root    35056 2010-03-05 16:02 ip6tables-save
-rwxr-xr-x  1 root root    13776 2010-02-11 19:38 ipmaddr
-rwxr-xr-x  1 root root    35068 2010-03-05 16:02 iptables
-rwxr-xr-x  1 root root    39204 2010-03-05 16:02 iptables-restore
-rwxr-xr-x  1 root root    35072 2010-03-05 16:02 iptables-save
-rwxr-xr-x  1 root root    17884 2010-02-11 19:38 iptunnel
-rwxr-xr-x  1 root root     9688 2010-03-22 13:51 isosize
-rwxr-xr-x  1 root root    22020 2010-02-23 11:26 iwconfig
-rwxr-xr-x  1 root root    13824 2010-02-23 11:26 iwevent
-rwxr-xr-x  1 root root     9640 2010-02-23 11:26 iwgetid
-rwxr-xr-x  1 root root    30252 2010-02-23 11:26 iwlist
-rwxr-xr-x  1 root root     9668 2010-02-23 11:26 iwpriv
-rwxr-xr-x  1 root root     9648 2010-02-23 11:26 iwspy
-rwxr-xr-x  1 root root     9660 2010-03-12 02:05 kbdrate
-rwxr-xr-x  1 root root    13772 2010-03-22 06:47 killall5
-rwxr-xr-x  1 root root      465 2010-03-21 22:37 ldconfig
-rwxr-xr-x  1 root root   658692 2010-03-21 22:37 ldconfig.real
-rwxr-xr-x  1 root root     9684 2010-03-22 14:26 logsave
-rwxr-xr-x  1 root root    34356 2010-03-22 13:51 losetup
lrwxrwxrwx  1 root root       10 2010-04-06 21:18 lsmod -> /bin/lsmod
lrwxrwxrwx  1 root root        9 2010-04-06 21:18 lspcmcia -> pccardctl
-rwxr-xr-x  1 root root    52466 2009-12-23 22:31 MAKEDEV
-rwxr-xr-x  1 root root    14116 2010-02-11 19:38 mii-tool
-rwxr-xr-x  1 root root    26692 2010-01-05 01:19 mkdosfs
-rwxr-xr-x  1 root root    55176 2010-03-22 14:26 mke2fs
-rwxr-xr-x  1 root root     5536 2010-03-22 13:51 mkfs
-rwxr-xr-x  1 root root    13824 2010-03-22 13:51 mkfs.bfs
-rwxr-xr-x  1 root root    22036 2010-03-22 13:51 mkfs.cramfs
-rwxr-xr-x  1 root root    55176 2010-03-22 14:26 mkfs.ext2
-rwxr-xr-x  1 root root    55176 2010-03-22 14:26 mkfs.ext3
-rwxr-xr-x  1 root root    55176 2010-03-22 14:26 mkfs.ext4
-rwxr-xr-x  1 root root    55176 2010-03-22 14:26 mkfs.ext4dev
-rwxr-xr-x  1 root root    19060 2010-03-22 13:51 mkfs.minix
lrwxrwxrwx  1 root root        7 2010-04-06 21:18 mkfs.msdos -> mkdosfs
lrwxrwxrwx  1 root root       16 2010-04-06 21:18 mkfs.ntfs -> /usr/sbin/mkntfs
lrwxrwxrwx  1 root root        7 2010-04-06 21:18 mkfs.vfat -> mkdosfs
-rwxr-xr-x  1 root root    17948 2010-02-18 07:17 mkhomedir_helper
-rwxr-xr-x  1 root root    18052 2010-03-22 13:51 mkswap
-rwxr-xr-x  1 root root    22032 2010-03-16 20:21 modinfo
-rwxr-xr-x  1 root root    38680 2010-03-16 20:21 modprobe
-rwxr-xr-x  1 root root    75256 2010-03-12 16:37 mountall
-rwxr-xr-x  1 root root     9636 2010-01-26 19:26 mount.fuse
lrwxrwxrwx  1 root root       13 2010-04-06 21:18 mount.ntfs -> mount.ntfs-3g
lrwxrwxrwx  1 root root       12 2010-04-06 21:18 mount.ntfs-3g -> /bin/ntfs-3g
lrwxrwxrwx  1 root root       18 2010-04-06 21:18 mount.ntfs-fuse -> /usr/bin/ntfsmount
-rwxr-xr-x  1 root root     9808 2010-02-11 19:38 nameif
-rwxr-xr-x  1 root root     2251 2009-12-02 03:57 on_ac_power
-rwxr-xr-x  1 root root     9664 2010-02-18 07:17 pam_tally
-rwxr-xr-x  1 root root    75828 2010-03-14 21:59 parted
-rwxr-xr-x  1 root root     9656 2010-03-14 21:59 partprobe
-rwxr-xr-x  1 root root    13800 2010-03-06 22:49 pccardctl
-rwxr-xr-x  1 root root     5488 2010-03-22 13:51 pivot_root
-rwxr-xr-x  1 root root     5544 2010-02-11 19:38 plipconfig
-rwxr-xr-x  1 root root    51136 2010-03-26 22:08 plymouthd
lrwxrwxrwx  1 root root        6 2010-04-06 21:18 poweroff -> reboot
-rwxr-xr-x  1 root root    23696 2010-02-11 19:38 rarp
-rwxr-xr-x  1 root root     9624 2010-03-22 13:51 raw
-rwxr-xr-x  1 root root     9736 2010-03-17 19:38 reboot
-rwxr-xr-x  1 root root     9636 2010-02-23 11:01 regdbdump
lrwxrwxrwx  1 root root        7 2010-04-06 21:18 reload -> initctl
-rwxr-xr-x  1 root root    34532 2010-03-22 14:26 resize2fs
lrwxrwxrwx  1 root root        7 2010-04-06 21:18 restart -> initctl
-rwxr-xr-x  1 root root     9644 2010-02-23 11:26 rfkill
-rwxr-xr-x  1 root root     9640 2010-03-16 20:21 rmmod
-rwxr-xr-x  1 root root    52268 2010-02-11 19:38 route
-rwxr-xr-x  1 root root    23156 2010-01-18 02:50 rtacct
-rwxr-xr-x  1 root root    30268 2010-01-18 02:50 rtmon
-rwxr-xr-x  1 root root     9516 2010-03-17 19:38 runlevel
-rwxr-xr-x  1 root root    55900 2010-03-22 13:51 sfdisk
-rwxr-xr-x  1 root root      879 2010-01-26 12:09 shadowconfig
-rwxr-xr-x  1 root root    46864 2010-03-17 19:38 shutdown
-rwxr-xr-x  1 root root    27732 2010-02-11 19:38 slattach
-rwxr-xr-x  1 root root    63252 2010-01-18 02:50 ss
lrwxrwxrwx  1 root root        7 2010-04-06 21:18 start -> initctl
-rwxr-xr-x  1 root root    26220 2010-03-22 06:47 startpar
lrwxrwxrwx  1 root root        7 2010-04-06 21:18 status -> initctl
lrwxrwxrwx  1 root root        7 2010-04-06 21:18 stop -> initctl
-rwxr-xr-x  1 root root    13796 2010-03-22 06:47 sulogin
lrwxrwxrwx  1 root root        6 2010-04-06 21:18 swapoff -> swapon
-rwxr-xr-x  1 root root    22340 2010-03-22 13:51 swapon
-rwxr-xr-x  1 root root     9676 2010-03-22 13:51 switch_root
-rwxr-xr-x  1 root root    13788 2009-12-16 14:34 sysctl
-rwxr-xr-x  1 root root   238648 2010-01-18 02:50 tc
-rwxr-xr-x  1 root root    38332 2010-03-17 19:38 telinit
-rwxr-xr-x  1 root root    34528 2010-03-22 14:26 tune2fs
-rwxr-xr-x  1 root root   111968 2010-03-24 14:08 udevadm
-rwxr-xr-x  1 root root   103816 2010-03-24 14:08 udevd
lrwxrwxrwx  1 root root       20 2010-04-06 21:18 umount.hal -> /usr/sbin/umount.hal
-rwxr-xr-x  1 root root     9652 2010-03-26 07:24 umount.udisks
-rwxr-sr-x  1 root shadow  30344 2010-02-18 07:17 unix_chkpwd
-rwxr-xr-x  1 root root    30328 2010-02-18 07:17 unix_update
-rwxr-xr-x  1 root root    38312 2010-03-17 19:38 upstart-udev-bridge
-rwxr-xr-x  1 root root    38416 2010-02-17 09:26 ureadahead
-rwxr-xr-x  1 root root    17944 2010-02-16 21:10 vstp
-rwxr-xr-x  1 root root    13800 2010-03-22 13:51 wipefs
-rwxr-xr-x  1 root root     1910 2010-03-07 01:24 wpa_action
-rwxr-xr-x  1 root root    39344 2010-03-07 01:24 wpa_cli
-rwxr-xr-x  1 root root   515044 2010-03-07 01:24 wpa_supplicant

```
```
ls -al /var/cache/apt/archives/dpkg*
ls: cannot access /var/cache/apt/archives/dpkg*: No such file or directory

```

---

### Post by sisco311 on 2010-04-07
Well, I don't know what happened but the file is not there!

Create a new directory in /tmp:
```
mkdir /tmp/dpkg
```
Download the dpkg deb file from [http://packages.ubuntu.com/lucid/dpkg](http://packages.ubuntu.com/lucid/dpkg) to /tmp/dpkg

extract the archive:
```
cd /tmp/dpkg
ar x dpkg*.deb
tar xfvz data.tar.gz

```
copy the file to /sbin:
```
sudo cp ./sbin/start-stop-daemon /sbin
```

and try to update & upgrade the system:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by abal1221 on 2010-04-07
That fixed it, thanks

---

### Post by sisco311 on 2010-04-07
> **abal1221 said:**
> That fixed it, thanks

You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

