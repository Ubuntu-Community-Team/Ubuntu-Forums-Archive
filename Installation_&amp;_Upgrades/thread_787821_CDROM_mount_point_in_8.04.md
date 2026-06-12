---
title: "CDROM mount point in 8.04"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by rajkhand on 2008-05-09
After upgrading from 7.10 the cdrom mount point has changed it is now

/media/name of the cd

synaptic is not able to find my 8.40 disk though it is showing on the desktop and am able to view it in nautilus.

previously it was /media/cdrom/

my cat /etc/ftab output is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=48552043-0086-4ec1-a89a-2c906adc9b52 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=18D5-292C  /media/hdc5     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=78E8EA82E8EA3E4E /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=D2D4ED5ED4ED44F7 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdc3
UUID=bd5fccb8-7f18-4c0d-aae9-7e88eeb5a72b none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

in /apt/sources.list the line is

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

my /etc/mtab is

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
/dev/sda5 /media/hdc5 vfat rw,umask=007,gid=46 0 0
/dev/sdb1 /media/sda1 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sdb5 /media/sda5 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
[COLOR="Sienna"]/dev/scd0 /media/Ubuntu\0408.04\040i386 iso9660 ro,nosuid,nodev,uhelper=hal,uid=1000,utf8 0 0[/COLOR]

ls -l /dev/cd* shows
lrwxrwxrwx 1 root root 4 2008-05-09 10:23 /dev/cdrom2 -> scd0
lrwxrwxrwx 1 root root 4 2008-05-09 10:23 /dev/cdrom3 -> scd1
lrwxrwxrwx 1 root root 4 2008-05-09 10:23 /dev/cdrw2 -> scd0
lrwxrwxrwx 1 root root 4 2008-05-09 10:23 /dev/cdrw3 -> scd1

 ls -l /media/
total 58
lrwxrwxrwx  1 root root        6 2008-02-22 21:35 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2008-02-22 21:35 cdrom0
drwxr-xr-x  2 root root     4096 2008-02-22 21:35 cdrom1
drwxrwx--- 32 root plugdev 16384 1970-01-01 05:30 hdc5
drwxrwx---  1 root plugdev 24576 2008-04-09 12:57 sda1
drwxrwx---  1 root plugdev  8192 2008-03-18 16:38 sda5
dr-xr-xr-x 10 raj  root     2048 2008-04-22 23:00 Ubuntu 8.04 i386

You can observe in the last line above that the cd is mounted separately as the name of the disk

Please help

TIA

Raj

---

### Post by hermes0710 on 2008-05-09
It seems that in fstab it should be scd0 and not hda or hdb.

Are there "hda"/"hdb" in your /dev folder? If not, are there "scd0", "scd1"?

---

### Post by rajkhand on 2008-05-09
ls -l /dev/

crw-rw-rw-  1 root   tty       2,  73 2008-05-09 15:53 ptyt9
crw-rw-rw-  1 root   tty       2,  74 2008-05-09 15:53 ptyta
crw-rw-rw-  1 root   tty       2,  75 2008-05-09 15:53 ptytb
crw-rw-rw-  1 root   tty       2,  76 2008-05-09 15:53 ptytc
crw-rw-rw-  1 root   tty       2,  77 2008-05-09 15:53 ptytd
crw-rw-rw-  1 root   tty       2,  78 2008-05-09 15:53 ptyte
crw-rw-rw-  1 root   tty       2,  79 2008-05-09 15:53 ptytf
crw-rw-rw-  1 root   tty       2,  80 2008-05-09 15:53 ptyu0
crw-rw-rw-  1 root   tty       2,  81 2008-05-09 15:53 ptyu1
crw-rw-rw-  1 root   tty       2,  82 2008-05-09 15:53 ptyu2
crw-rw-rw-  1 root   tty       2,  83 2008-05-09 15:53 ptyu3
crw-rw-rw-  1 root   tty       2,  84 2008-05-09 15:53 ptyu4
crw-rw-rw-  1 root   tty       2,  85 2008-05-09 15:53 ptyu5
crw-rw-rw-  1 root   tty       2,  86 2008-05-09 15:53 ptyu6
crw-rw-rw-  1 root   tty       2,  87 2008-05-09 15:53 ptyu7
crw-rw-rw-  1 root   tty       2,  88 2008-05-09 15:53 ptyu8
crw-rw-rw-  1 root   tty       2,  89 2008-05-09 15:53 ptyu9
crw-rw-rw-  1 root   tty       2,  90 2008-05-09 15:53 ptyua
crw-rw-rw-  1 root   tty       2,  91 2008-05-09 15:53 ptyub
crw-rw-rw-  1 root   tty       2,  92 2008-05-09 15:53 ptyuc
crw-rw-rw-  1 root   tty       2,  93 2008-05-09 15:53 ptyud
crw-rw-rw-  1 root   tty       2,  94 2008-05-09 15:53 ptyue
crw-rw-rw-  1 root   tty       2,  95 2008-05-09 15:53 ptyuf
crw-rw-rw-  1 root   tty       2,  96 2008-05-09 15:53 ptyv0
crw-rw-rw-  1 root   tty       2,  97 2008-05-09 15:53 ptyv1
crw-rw-rw-  1 root   tty       2,  98 2008-05-09 15:53 ptyv2
crw-rw-rw-  1 root   tty       2,  99 2008-05-09 15:53 ptyv3
crw-rw-rw-  1 root   tty       2, 100 2008-05-09 15:53 ptyv4
crw-rw-rw-  1 root   tty       2, 101 2008-05-09 15:53 ptyv5
crw-rw-rw-  1 root   tty       2, 102 2008-05-09 15:53 ptyv6
crw-rw-rw-  1 root   tty       2, 103 2008-05-09 15:53 ptyv7
crw-rw-rw-  1 root   tty       2, 104 2008-05-09 15:53 ptyv8
crw-rw-rw-  1 root   tty       2, 105 2008-05-09 15:53 ptyv9
crw-rw-rw-  1 root   tty       2, 106 2008-05-09 15:53 ptyva
crw-rw-rw-  1 root   tty       2, 107 2008-05-09 15:53 ptyvb
crw-rw-rw-  1 root   tty       2, 108 2008-05-09 15:53 ptyvc
crw-rw-rw-  1 root   tty       2, 109 2008-05-09 15:53 ptyvd
crw-rw-rw-  1 root   tty       2, 110 2008-05-09 15:53 ptyve
crw-rw-rw-  1 root   tty       2, 111 2008-05-09 15:53 ptyvf
crw-rw-rw-  1 root   tty       2, 112 2008-05-09 15:53 ptyw0
crw-rw-rw-  1 root   tty       2, 113 2008-05-09 15:53 ptyw1
crw-rw-rw-  1 root   tty       2, 114 2008-05-09 15:53 ptyw2
crw-rw-rw-  1 root   tty       2, 115 2008-05-09 15:53 ptyw3
crw-rw-rw-  1 root   tty       2, 116 2008-05-09 15:53 ptyw4
crw-rw-rw-  1 root   tty       2, 117 2008-05-09 15:53 ptyw5
crw-rw-rw-  1 root   tty       2, 118 2008-05-09 15:53 ptyw6
crw-rw-rw-  1 root   tty       2, 119 2008-05-09 15:53 ptyw7
crw-rw-rw-  1 root   tty       2, 120 2008-05-09 15:53 ptyw8
crw-rw-rw-  1 root   tty       2, 121 2008-05-09 15:53 ptyw9
crw-rw-rw-  1 root   tty       2, 122 2008-05-09 15:53 ptywa
crw-rw-rw-  1 root   tty       2, 123 2008-05-09 15:53 ptywb
crw-rw-rw-  1 root   tty       2, 124 2008-05-09 15:53 ptywc
crw-rw-rw-  1 root   tty       2, 125 2008-05-09 15:53 ptywd
crw-rw-rw-  1 root   tty       2, 126 2008-05-09 15:53 ptywe
crw-rw-rw-  1 root   tty       2, 127 2008-05-09 15:53 ptywf
crw-rw-rw-  1 root   tty       2, 128 2008-05-09 15:53 ptyx0
crw-rw-rw-  1 root   tty       2, 129 2008-05-09 15:53 ptyx1
crw-rw-rw-  1 root   tty       2, 130 2008-05-09 15:53 ptyx2
crw-rw-rw-  1 root   tty       2, 131 2008-05-09 15:53 ptyx3
crw-rw-rw-  1 root   tty       2, 132 2008-05-09 15:53 ptyx4
crw-rw-rw-  1 root   tty       2, 133 2008-05-09 15:53 ptyx5
crw-rw-rw-  1 root   tty       2, 134 2008-05-09 15:53 ptyx6
crw-rw-rw-  1 root   tty       2, 135 2008-05-09 15:53 ptyx7
crw-rw-rw-  1 root   tty       2, 136 2008-05-09 15:53 ptyx8
crw-rw-rw-  1 root   tty       2, 137 2008-05-09 15:53 ptyx9
crw-rw-rw-  1 root   tty       2, 138 2008-05-09 15:53 ptyxa
crw-rw-rw-  1 root   tty       2, 139 2008-05-09 15:53 ptyxb
crw-rw-rw-  1 root   tty       2, 140 2008-05-09 15:53 ptyxc
crw-rw-rw-  1 root   tty       2, 141 2008-05-09 15:53 ptyxd
crw-rw-rw-  1 root   tty       2, 142 2008-05-09 15:53 ptyxe
crw-rw-rw-  1 root   tty       2, 143 2008-05-09 15:53 ptyxf
crw-rw-rw-  1 root   tty       2, 144 2008-05-09 15:53 ptyy0
crw-rw-rw-  1 root   tty       2, 145 2008-05-09 15:53 ptyy1
crw-rw-rw-  1 root   tty       2, 146 2008-05-09 15:53 ptyy2
crw-rw-rw-  1 root   tty       2, 147 2008-05-09 15:53 ptyy3
crw-rw-rw-  1 root   tty       2, 148 2008-05-09 15:53 ptyy4
crw-rw-rw-  1 root   tty       2, 149 2008-05-09 15:53 ptyy5
crw-rw-rw-  1 root   tty       2, 150 2008-05-09 15:53 ptyy6
crw-rw-rw-  1 root   tty       2, 151 2008-05-09 15:53 ptyy7
crw-rw-rw-  1 root   tty       2, 152 2008-05-09 15:53 ptyy8
crw-rw-rw-  1 root   tty       2, 153 2008-05-09 15:53 ptyy9
crw-rw-rw-  1 root   tty       2, 154 2008-05-09 15:53 ptyya
crw-rw-rw-  1 root   tty       2, 155 2008-05-09 15:53 ptyyb
crw-rw-rw-  1 root   tty       2, 156 2008-05-09 15:53 ptyyc
crw-rw-rw-  1 root   tty       2, 157 2008-05-09 15:53 ptyyd
crw-rw-rw-  1 root   tty       2, 158 2008-05-09 15:53 ptyye
crw-rw-rw-  1 root   tty       2, 159 2008-05-09 15:53 ptyyf
crw-rw-rw-  1 root   tty       2, 160 2008-05-09 15:53 ptyz0
crw-rw-rw-  1 root   tty       2, 161 2008-05-09 15:53 ptyz1
crw-rw-rw-  1 root   tty       2, 162 2008-05-09 15:53 ptyz2
crw-rw-rw-  1 root   tty       2, 163 2008-05-09 15:53 ptyz3
crw-rw-rw-  1 root   tty       2, 164 2008-05-09 15:53 ptyz4
crw-rw-rw-  1 root   tty       2, 165 2008-05-09 15:53 ptyz5
crw-rw-rw-  1 root   tty       2, 166 2008-05-09 15:53 ptyz6
crw-rw-rw-  1 root   tty       2, 167 2008-05-09 15:53 ptyz7
crw-rw-rw-  1 root   tty       2, 168 2008-05-09 15:53 ptyz8
crw-rw-rw-  1 root   tty       2, 169 2008-05-09 15:53 ptyz9
crw-rw-rw-  1 root   tty       2, 170 2008-05-09 15:53 ptyza
crw-rw-rw-  1 root   tty       2, 171 2008-05-09 15:53 ptyzb
crw-rw-rw-  1 root   tty       2, 172 2008-05-09 15:53 ptyzc
crw-rw-rw-  1 root   tty       2, 173 2008-05-09 15:53 ptyzd
crw-rw-rw-  1 root   tty       2, 174 2008-05-09 15:53 ptyze
crw-rw-rw-  1 root   tty       2, 175 2008-05-09 15:53 ptyzf
brw-rw----  1 root   disk      1,   0 2008-05-09 15:53 ram0
brw-rw----  1 root   disk      1,   1 2008-05-09 15:53 ram1
brw-rw----  1 root   disk      1,  10 2008-05-09 15:53 ram10
brw-rw----  1 root   disk      1,  11 2008-05-09 15:53 ram11
brw-rw----  1 root   disk      1,  12 2008-05-09 15:53 ram12
brw-rw----  1 root   disk      1,  13 2008-05-09 15:53 ram13
brw-rw----  1 root   disk      1,  14 2008-05-09 15:53 ram14
brw-rw----  1 root   disk      1,  15 2008-05-09 15:53 ram15
brw-rw----  1 root   disk      1,   2 2008-05-09 15:53 ram2
brw-rw----  1 root   disk      1,   3 2008-05-09 15:53 ram3
brw-rw----  1 root   disk      1,   4 2008-05-09 15:53 ram4
brw-rw----  1 root   disk      1,   5 2008-05-09 15:53 ram5
brw-rw----  1 root   disk      1,   6 2008-05-09 15:53 ram6
brw-rw----  1 root   disk      1,   7 2008-05-09 15:53 ram7
brw-rw----  1 root   disk      1,   8 2008-05-09 15:53 ram8
brw-rw----  1 root   disk      1,   9 2008-05-09 15:53 ram9
crw-rw-rw-  1 root   root      1,   8 2008-05-09 15:53 random
crw-rw----  1 root   audio    10, 135 2008-05-09 15:53 rtc
brw-rw----+ 1 root   cdrom    11,   0 2008-05-09 15:53 scd0
brw-rw----+ 1 root   cdrom    11,   1 2008-05-09 15:53 scd1
brw-rw----  1 root   disk      8,   0 2008-05-09 15:53 sda
brw-rw----  1 root   disk      8,   1 2008-05-09 10:23 sda1
brw-rw----  1 root   disk      8,   2 2008-05-09 15:53 sda2
brw-rw----  1 root   disk      8,   3 2008-05-09 15:53 sda3
brw-rw----  1 root   disk      8,   5 2008-05-09 15:53 sda5
brw-rw----  1 root   disk      8,  16 2008-05-09 15:53 sdb
brw-rw----  1 root   disk      8,  17 2008-05-09 15:53 sdb1
brw-rw----  1 root   disk      8,  18 2008-05-09 15:53 sdb2
brw-rw----  1 root   disk      8,  21 2008-05-09 15:53 sdb5
crw-rw----+ 1 root   audio    14,   1 2008-05-09 10:23 sequencer
crw-rw----+ 1 root   audio    14,   8 2008-05-09 10:23 sequencer2
crw-rw----  1 root   cdrom    21,   0 2008-05-09 15:53 sg0
crw-rw----  1 root   cdrom    21,   1 2008-05-09 15:53 sg1
crw-rw----  1 root   disk     21,   2 2008-05-09 15:53 sg2
crw-rw----  1 root   disk     21,   3 2008-05-09 15:53 sg3
drwxrwxrwt  2 root   root          60 2008-05-09 18:15 shm
crw-rw----  1 root   root     10, 231 2008-05-09 15:53 snapshot
drwxr-xr-x  2 root   root         220 2008-05-09 10:23 snd
lrwxrwxrwx  1 root   root          24 2008-05-09 10:23 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx  1 root   root           4 2008-05-09 10:23 sr0 -> scd0
lrwxrwxrwx  1 root   root           4 2008-05-09 10:23 sr1 -> scd1
lrwxrwxrwx  1 root   root          15 2008-05-09 10:23 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root   root          15 2008-05-09 10:23 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root   root          15 2008-05-09 10:23 stdout -> /proc/self/fd/1
crw-rw-rw-  1 root   dialout   5,   0 2008-05-09 17:00 tty
crw-rw----  1 root   root      4,   0 2008-05-09 15:53 tty0
crw-------  1 root   root      4,   1 2008-05-09 10:24 tty1
crw-rw----  1 root   dialout   4,  10 2008-05-09 15:53 tty10
crw-rw----  1 root   dialout   4,  11 2008-05-09 15:53 tty11
crw-rw----  1 root   dialout   4,  12 2008-05-09 15:53 tty12
crw-rw----  1 root   dialout   4,  13 2008-05-09 15:53 tty13
crw-rw----  1 root   dialout   4,  14 2008-05-09 15:53 tty14
crw-rw----  1 root   dialout   4,  15 2008-05-09 15:53 tty15
crw-rw----  1 root   dialout   4,  16 2008-05-09 15:53 tty16
crw-rw----  1 root   dialout   4,  17 2008-05-09 15:53 tty17
crw-rw----  1 root   dialout   4,  18 2008-05-09 15:53 tty18
crw-rw----  1 root   dialout   4,  19 2008-05-09 15:53 tty19
crw-------  1 root   root      4,   2 2008-05-09 10:23 tty2
crw-rw----  1 root   dialout   4,  20 2008-05-09 15:53 tty20
crw-rw----  1 root   dialout   4,  21 2008-05-09 15:53 tty21
crw-rw----  1 root   dialout   4,  22 2008-05-09 15:53 tty22
crw-rw----  1 root   dialout   4,  23 2008-05-09 15:53 tty23
crw-rw----  1 root   dialout   4,  24 2008-05-09 15:53 tty24
crw-rw----  1 root   dialout   4,  25 2008-05-09 15:53 tty25
crw-rw----  1 root   dialout   4,  26 2008-05-09 15:53 tty26
crw-rw----  1 root   dialout   4,  27 2008-05-09 15:53 tty27
crw-rw----  1 root   dialout   4,  28 2008-05-09 15:53 tty28
crw-rw----  1 root   dialout   4,  29 2008-05-09 15:53 tty29
crw-------  1 root   root      4,   3 2008-05-09 10:23 tty3
crw-rw----  1 root   dialout   4,  30 2008-05-09 15:53 tty30
crw-rw----  1 root   dialout   4,  31 2008-05-09 15:53 tty31
crw-rw----  1 root   dialout   4,  32 2008-05-09 15:53 tty32
crw-rw----  1 root   dialout   4,  33 2008-05-09 15:53 tty33
crw-rw----  1 root   dialout   4,  34 2008-05-09 15:53 tty34
crw-rw----  1 root   dialout   4,  35 2008-05-09 15:53 tty35
crw-rw----  1 root   dialout   4,  36 2008-05-09 15:53 tty36
crw-rw----  1 root   dialout   4,  37 2008-05-09 15:53 tty37
crw-rw----  1 root   dialout   4,  38 2008-05-09 15:53 tty38
crw-rw----  1 root   dialout   4,  39 2008-05-09 15:53 tty39
crw-------  1 root   root      4,   4 2008-05-09 10:23 tty4
crw-rw----  1 root   dialout   4,  40 2008-05-09 15:53 tty40
crw-rw----  1 root   dialout   4,  41 2008-05-09 15:53 tty41
crw-rw----  1 root   dialout   4,  42 2008-05-09 15:53 tty42
crw-rw----  1 root   dialout   4,  43 2008-05-09 15:53 tty43
crw-rw----  1 root   dialout   4,  44 2008-05-09 15:53 tty44
crw-rw----  1 root   dialout   4,  45 2008-05-09 15:53 tty45
crw-rw----  1 root   dialout   4,  46 2008-05-09 15:53 tty46
crw-rw----  1 root   dialout   4,  47 2008-05-09 15:53 tty47
crw-rw----  1 root   dialout   4,  48 2008-05-09 15:53 tty48
crw-rw----  1 root   dialout   4,  49 2008-05-09 15:53 tty49
crw-------  1 root   root      4,   5 2008-05-09 10:23 tty5
crw-rw----  1 root   dialout   4,  50 2008-05-09 15:53 tty50
crw-rw----  1 root   dialout   4,  51 2008-05-09 15:53 tty51
crw-rw----  1 root   dialout   4,  52 2008-05-09 15:53 tty52
crw-rw----  1 root   dialout   4,  53 2008-05-09 15:53 tty53
crw-rw----  1 root   dialout   4,  54 2008-05-09 15:53 tty54
crw-rw----  1 root   dialout   4,  55 2008-05-09 15:53 tty55
crw-rw----  1 root   dialout   4,  56 2008-05-09 15:53 tty56
crw-rw----  1 root   dialout   4,  57 2008-05-09 15:53 tty57
crw-rw----  1 root   dialout   4,  58 2008-05-09 15:53 tty58
crw-rw----  1 root   dialout   4,  59 2008-05-09 15:53 tty59
crw-------  1 root   root      4,   6 2008-05-09 10:23 tty6
crw-rw----  1 root   dialout   4,  60 2008-05-09 15:53 tty60
crw-rw----  1 root   dialout   4,  61 2008-05-09 15:53 tty61
crw-rw----  1 root   dialout   4,  62 2008-05-09 15:53 tty62
crw-rw----  1 root   dialout   4,  63 2008-05-09 15:53 tty63
crw-rw----  1 root   root      4,   7 2008-05-09 15:53 tty7
crw-rw----  1 root   dialout   4,   8 2008-05-09 10:24 tty8
crw-rw----  1 root   dialout   4,   9 2008-05-09 15:53 tty9
crw-rw-rw-  1 root   tty       3, 176 2008-05-09 15:53 ttya0
crw-rw-rw-  1 root   tty       3, 177 2008-05-09 15:53 ttya1
crw-rw-rw-  1 root   tty       3, 178 2008-05-09 15:53 ttya2
crw-rw-rw-  1 root   tty       3, 179 2008-05-09 15:53 ttya3
crw-rw-rw-  1 root   tty       3, 180 2008-05-09 15:53 ttya4
crw-rw-rw-  1 root   tty       3, 181 2008-05-09 15:53 ttya5
crw-rw-rw-  1 root   tty       3, 182 2008-05-09 15:53 ttya6
crw-rw-rw-  1 root   tty       3, 183 2008-05-09 15:53 ttya7
crw-rw-rw-  1 root   tty       3, 184 2008-05-09 15:53 ttya8
crw-rw-rw-  1 root   tty       3, 185 2008-05-09 15:53 ttya9
crw-rw-rw-  1 root   tty       3, 186 2008-05-09 15:53 ttyaa
crw-rw-rw-  1 root   tty       3, 187 2008-05-09 15:53 ttyab
crw-rw-rw-  1 root   tty       3, 188 2008-05-09 15:53 ttyac
crw-rw-rw-  1 root   tty       3, 189 2008-05-09 15:53 ttyad
crw-rw-rw-  1 root   tty       3, 190 2008-05-09 15:53 ttyae
crw-rw-rw-  1 root   tty       3, 191 2008-05-09 15:53 ttyaf
crw-rw-rw-  1 root   tty       3, 192 2008-05-09 15:53 ttyb0
crw-rw-rw-  1 root   tty       3, 193 2008-05-09 15:53 ttyb1
crw-rw-rw-  1 root   tty       3, 194 2008-05-09 15:53 ttyb2
crw-rw-rw-  1 root   tty       3, 195 2008-05-09 15:53 ttyb3
crw-rw-rw-  1 root   tty       3, 196 2008-05-09 15:53 ttyb4
crw-rw-rw-  1 root   tty       3, 197 2008-05-09 15:53 ttyb5
crw-rw-rw-  1 root   tty       3, 198 2008-05-09 15:53 ttyb6
crw-rw-rw-  1 root   tty       3, 199 2008-05-09 15:53 ttyb7
crw-rw-rw-  1 root   tty       3, 200 2008-05-09 15:53 ttyb8
crw-rw-rw-  1 root   tty       3, 201 2008-05-09 15:53 ttyb9
crw-rw-rw-  1 root   tty       3, 202 2008-05-09 15:53 ttyba
crw-rw-rw-  1 root   tty       3, 203 2008-05-09 15:53 ttybb
crw-rw-rw-  1 root   tty       3, 204 2008-05-09 15:53 ttybc
crw-rw-rw-  1 root   tty       3, 205 2008-05-09 15:53 ttybd
crw-rw-rw-  1 root   tty       3, 206 2008-05-09 15:53 ttybe
crw-rw-rw-  1 root   tty       3, 207 2008-05-09 15:53 ttybf
crw-rw-rw-  1 root   tty       3, 208 2008-05-09 15:53 ttyc0
crw-rw-rw-  1 root   tty       3, 209 2008-05-09 15:53 ttyc1
crw-rw-rw-  1 root   tty       3, 210 2008-05-09 15:53 ttyc2
crw-rw-rw-  1 root   tty       3, 211 2008-05-09 15:53 ttyc3
crw-rw-rw-  1 root   tty       3, 212 2008-05-09 15:53 ttyc4
crw-rw-rw-  1 root   tty       3, 213 2008-05-09 15:53 ttyc5
crw-rw-rw-  1 root   tty       3, 214 2008-05-09 15:53 ttyc6
crw-rw-rw-  1 root   tty       3, 215 2008-05-09 15:53 ttyc7
crw-rw-rw-  1 root   tty       3, 216 2008-05-09 15:53 ttyc8
crw-rw-rw-  1 root   tty       3, 217 2008-05-09 15:53 ttyc9
crw-rw-rw-  1 root   tty       3, 218 2008-05-09 15:53 ttyca
crw-rw-rw-  1 root   tty       3, 219 2008-05-09 15:53 ttycb
crw-rw-rw-  1 root   tty       3, 220 2008-05-09 15:53 ttycc
crw-rw-rw-  1 root   tty       3, 221 2008-05-09 15:53 ttycd
crw-rw-rw-  1 root   tty       3, 222 2008-05-09 15:53 ttyce
crw-rw-rw-  1 root   tty       3, 223 2008-05-09 15:53 ttycf
crw-rw-rw-  1 root   tty       3, 224 2008-05-09 15:53 ttyd0
crw-rw-rw-  1 root   tty       3, 225 2008-05-09 15:53 ttyd1
crw-rw-rw-  1 root   tty       3, 226 2008-05-09 15:53 ttyd2
crw-rw-rw-  1 root   tty       3, 227 2008-05-09 15:53 ttyd3
crw-rw-rw-  1 root   tty       3, 228 2008-05-09 15:53 ttyd4
crw-rw-rw-  1 root   tty       3, 229 2008-05-09 15:53 ttyd5
crw-rw-rw-  1 root   tty       3, 230 2008-05-09 15:53 ttyd6
crw-rw-rw-  1 root   tty       3, 231 2008-05-09 15:53 ttyd7
crw-rw-rw-  1 root   tty       3, 232 2008-05-09 15:53 ttyd8
crw-rw-rw-  1 root   tty       3, 233 2008-05-09 15:53 ttyd9
crw-rw-rw-  1 root   tty       3, 234 2008-05-09 15:53 ttyda
crw-rw-rw-  1 root   tty       3, 235 2008-05-09 15:53 ttydb
crw-rw-rw-  1 root   tty       3, 236 2008-05-09 15:53 ttydc
crw-rw-rw-  1 root   tty       3, 237 2008-05-09 15:53 ttydd
crw-rw-rw-  1 root   tty       3, 238 2008-05-09 15:53 ttyde
crw-rw-rw-  1 root   tty       3, 239 2008-05-09 15:53 ttydf
crw-rw-rw-  1 root   tty       3, 240 2008-05-09 15:53 ttye0
crw-rw-rw-  1 root   tty       3, 241 2008-05-09 15:53 ttye1
crw-rw-rw-  1 root   tty       3, 242 2008-05-09 15:53 ttye2
crw-rw-rw-  1 root   tty       3, 243 2008-05-09 15:53 ttye3
crw-rw-rw-  1 root   tty       3, 244 2008-05-09 15:53 ttye4
crw-rw-rw-  1 root   tty       3, 245 2008-05-09 15:53 ttye5
crw-rw-rw-  1 root   tty       3, 246 2008-05-09 15:53 ttye6
crw-rw-rw-  1 root   tty       3, 247 2008-05-09 15:53 ttye7
crw-rw-rw-  1 root   tty       3, 248 2008-05-09 15:53 ttye8
crw-rw-rw-  1 root   tty       3, 249 2008-05-09 15:53 ttye9
crw-rw-rw-  1 root   tty       3, 250 2008-05-09 15:53 ttyea
crw-rw-rw-  1 root   tty       3, 251 2008-05-09 15:53 ttyeb
crw-rw-rw-  1 root   tty       3, 252 2008-05-09 15:53 ttyec
crw-rw-rw-  1 root   tty       3, 253 2008-05-09 15:53 ttyed
crw-rw-rw-  1 root   tty       3, 254 2008-05-09 15:53 ttyee
crw-rw-rw-  1 root   tty       3, 255 2008-05-09 15:53 ttyef
crw-rw-rw-  1 root   tty       3,   0 2008-05-09 15:53 ttyp0
crw-rw-rw-  1 root   tty       3,   1 2008-05-09 15:53 ttyp1
crw-rw-rw-  1 root   tty       3,   2 2008-05-09 15:53 ttyp2
crw-rw-rw-  1 root   tty       3,   3 2008-05-09 15:53 ttyp3
crw-rw-rw-  1 root   tty       3,   4 2008-05-09 15:53 ttyp4
crw-rw-rw-  1 root   tty       3,   5 2008-05-09 15:53 ttyp5
crw-rw-rw-  1 root   tty       3,   6 2008-05-09 15:53 ttyp6
crw-rw-rw-  1 root   tty       3,   7 2008-05-09 15:53 ttyp7
crw-rw-rw-  1 root   tty       3,   8 2008-05-09 15:53 ttyp8
crw-rw-rw-  1 root   tty       3,   9 2008-05-09 15:53 ttyp9
crw-rw-rw-  1 root   tty       3,  10 2008-05-09 15:53 ttypa
crw-rw-rw-  1 root   tty       3,  11 2008-05-09 15:53 ttypb
crw-rw-rw-  1 root   tty       3,  12 2008-05-09 15:53 ttypc
crw-rw-rw-  1 root   tty       3,  13 2008-05-09 15:53 ttypd
crw-rw-rw-  1 root   tty       3,  14 2008-05-09 15:53 ttype
crw-rw-rw-  1 root   tty       3,  15 2008-05-09 15:53 ttypf
crw-rw-rw-  1 root   tty       3,  16 2008-05-09 15:53 ttyq0
crw-rw-rw-  1 root   tty       3,  17 2008-05-09 15:53 ttyq1
crw-rw-rw-  1 root   tty       3,  18 2008-05-09 15:53 ttyq2
crw-rw-rw-  1 root   tty       3,  19 2008-05-09 15:53 ttyq3
crw-rw-rw-  1 root   tty       3,  20 2008-05-09 15:53 ttyq4
crw-rw-rw-  1 root   tty       3,  21 2008-05-09 15:53 ttyq5
crw-rw-rw-  1 root   tty       3,  22 2008-05-09 15:53 ttyq6
crw-rw-rw-  1 root   tty       3,  23 2008-05-09 15:53 ttyq7
crw-rw-rw-  1 root   tty       3,  24 2008-05-09 15:53 ttyq8
crw-rw-rw-  1 root   tty       3,  25 2008-05-09 15:53 ttyq9
crw-rw-rw-  1 root   tty       3,  26 2008-05-09 15:53 ttyqa
crw-rw-rw-  1 root   tty       3,  27 2008-05-09 15:53 ttyqb
crw-rw-rw-  1 root   tty       3,  28 2008-05-09 15:53 ttyqc
crw-rw-rw-  1 root   tty       3,  29 2008-05-09 15:53 ttyqd
crw-rw-rw-  1 root   tty       3,  30 2008-05-09 15:53 ttyqe
crw-rw-rw-  1 root   tty       3,  31 2008-05-09 15:53 ttyqf
crw-rw-rw-  1 root   tty       3,  32 2008-05-09 15:53 ttyr0
crw-rw-rw-  1 root   tty       3,  33 2008-05-09 15:53 ttyr1
crw-rw-rw-  1 root   tty       3,  34 2008-05-09 15:53 ttyr2
crw-rw-rw-  1 root   tty       3,  35 2008-05-09 15:53 ttyr3
crw-rw-rw-  1 root   tty       3,  36 2008-05-09 15:53 ttyr4
crw-rw-rw-  1 root   tty       3,  37 2008-05-09 15:53 ttyr5
crw-rw-rw-  1 root   tty       3,  38 2008-05-09 15:53 ttyr6
crw-rw-rw-  1 root   tty       3,  39 2008-05-09 15:53 ttyr7
crw-rw-rw-  1 root   tty       3,  40 2008-05-09 15:53 ttyr8
crw-rw-rw-  1 root   tty       3,  41 2008-05-09 15:53 ttyr9
crw-rw-rw-  1 root   tty       3,  42 2008-05-09 15:53 ttyra
crw-rw-rw-  1 root   tty       3,  43 2008-05-09 15:53 ttyrb
crw-rw-rw-  1 root   tty       3,  44 2008-05-09 15:53 ttyrc
crw-rw-rw-  1 root   tty       3,  45 2008-05-09 15:53 ttyrd
crw-rw-rw-  1 root   tty       3,  46 2008-05-09 15:53 ttyre
crw-rw-rw-  1 root   tty       3,  47 2008-05-09 15:53 ttyrf
crw-rw-rw-  1 root   tty       3,  48 2008-05-09 15:53 ttys0
crw-rw----  1 root   dialout   4,  64 2008-05-09 15:53 ttyS0
crw-rw-rw-  1 root   tty       3,  49 2008-05-09 15:53 ttys1
crw-rw----  1 root   dialout   4,  65 2008-05-09 15:53 ttyS1
crw-rw-rw-  1 root   tty       3,  50 2008-05-09 15:53 ttys2
crw-rw----  1 root   dialout   4,  66 2008-05-09 15:53 ttyS2
crw-rw-rw-  1 root   tty       3,  51 2008-05-09 15:53 ttys3
crw-rw----  1 root   dialout   4,  67 2008-05-09 15:53 ttyS3
crw-rw-rw-  1 root   tty       3,  52 2008-05-09 15:53 ttys4
crw-rw-rw-  1 root   tty       3,  53 2008-05-09 15:53 ttys5
crw-rw-rw-  1 root   tty       3,  54 2008-05-09 15:53 ttys6
crw-rw-rw-  1 root   tty       3,  55 2008-05-09 15:53 ttys7
crw-rw-rw-  1 root   tty       3,  56 2008-05-09 15:53 ttys8
crw-rw-rw-  1 root   tty       3,  57 2008-05-09 15:53 ttys9
crw-rw-rw-  1 root   tty       3,  58 2008-05-09 15:53 ttysa
crw-rw-rw-  1 root   tty       3,  59 2008-05-09 15:53 ttysb
crw-rw-rw-  1 root   tty       3,  60 2008-05-09 15:53 ttysc
crw-rw-rw-  1 root   tty       3,  61 2008-05-09 15:53 ttysd
crw-rw-rw-  1 root   tty       3,  62 2008-05-09 15:53 ttyse
crw-rw-rw-  1 root   tty       3,  63 2008-05-09 15:53 ttysf
crw-rw-rw-  1 root   tty       3,  64 2008-05-09 15:53 ttyt0
crw-rw-rw-  1 root   tty       3,  65 2008-05-09 15:53 ttyt1
crw-rw-rw-  1 root   tty       3,  66 2008-05-09 15:53 ttyt2
crw-rw-rw-  1 root   tty       3,  67 2008-05-09 15:53 ttyt3
crw-rw-rw-  1 root   tty       3,  68 2008-05-09 15:53 ttyt4
crw-rw-rw-  1 root   tty       3,  69 2008-05-09 15:53 ttyt5
crw-rw-rw-  1 root   tty       3,  70 2008-05-09 15:53 ttyt6
crw-rw-rw-  1 root   tty       3,  71 2008-05-09 15:53 ttyt7
crw-rw-rw-  1 root   tty       3,  72 2008-05-09 15:53 ttyt8
crw-rw-rw-  1 root   tty       3,  73 2008-05-09 15:53 ttyt9
crw-rw-rw-  1 root   tty       3,  74 2008-05-09 15:53 ttyta
crw-rw-rw-  1 root   tty       3,  75 2008-05-09 15:53 ttytb
crw-rw-rw-  1 root   tty       3,  76 2008-05-09 15:53 ttytc
crw-rw-rw-  1 root   tty       3,  77 2008-05-09 15:53 ttytd
crw-rw-rw-  1 root   tty       3,  78 2008-05-09 15:53 ttyte
crw-rw-rw-  1 root   tty       3,  79 2008-05-09 15:53 ttytf
crw-rw-rw-  1 root   tty       3,  80 2008-05-09 15:53 ttyu0
crw-rw-rw-  1 root   tty       3,  81 2008-05-09 15:53 ttyu1
crw-rw-rw-  1 root   tty       3,  82 2008-05-09 15:53 ttyu2
crw-rw-rw-  1 root   tty       3,  83 2008-05-09 15:53 ttyu3
crw-rw-rw-  1 root   tty       3,  84 2008-05-09 15:53 ttyu4
crw-rw-rw-  1 root   tty       3,  85 2008-05-09 15:53 ttyu5
crw-rw-rw-  1 root   tty       3,  86 2008-05-09 15:53 ttyu6
crw-rw-rw-  1 root   tty       3,  87 2008-05-09 15:53 ttyu7
crw-rw-rw-  1 root   tty       3,  88 2008-05-09 15:53 ttyu8
crw-rw-rw-  1 root   tty       3,  89 2008-05-09 15:53 ttyu9
crw-rw-rw-  1 root   tty       3,  90 2008-05-09 15:53 ttyua
crw-rw-rw-  1 root   tty       3,  91 2008-05-09 15:53 ttyub
crw-rw-rw-  1 root   tty       3,  92 2008-05-09 15:53 ttyuc
crw-rw-rw-  1 root   tty       3,  93 2008-05-09 15:53 ttyud
crw-rw-rw-  1 root   tty       3,  94 2008-05-09 15:53 ttyue
crw-rw-rw-  1 root   tty       3,  95 2008-05-09 15:53 ttyuf
crw-rw-rw-  1 root   tty       3,  96 2008-05-09 15:53 ttyv0
crw-rw-rw-  1 root   tty       3,  97 2008-05-09 15:53 ttyv1
crw-rw-rw-  1 root   tty       3,  98 2008-05-09 15:53 ttyv2
crw-rw-rw-  1 root   tty       3,  99 2008-05-09 15:53 ttyv3
crw-rw-rw-  1 root   tty       3, 100 2008-05-09 15:53 ttyv4
crw-rw-rw-  1 root   tty       3, 101 2008-05-09 15:53 ttyv5
crw-rw-rw-  1 root   tty       3, 102 2008-05-09 15:53 ttyv6
crw-rw-rw-  1 root   tty       3, 103 2008-05-09 15:53 ttyv7
crw-rw-rw-  1 root   tty       3, 104 2008-05-09 15:53 ttyv8
crw-rw-rw-  1 root   tty       3, 105 2008-05-09 15:53 ttyv9
crw-rw-rw-  1 root   tty       3, 106 2008-05-09 15:53 ttyva
crw-rw-rw-  1 root   tty       3, 107 2008-05-09 15:53 ttyvb
crw-rw-rw-  1 root   tty       3, 108 2008-05-09 15:53 ttyvc
crw-rw-rw-  1 root   tty       3, 109 2008-05-09 15:53 ttyvd
crw-rw-rw-  1 root   tty       3, 110 2008-05-09 15:53 ttyve
crw-rw-rw-  1 root   tty       3, 111 2008-05-09 15:53 ttyvf
crw-rw-rw-  1 root   tty       3, 112 2008-05-09 15:53 ttyw0
crw-rw-rw-  1 root   tty       3, 113 2008-05-09 15:53 ttyw1
crw-rw-rw-  1 root   tty       3, 114 2008-05-09 15:53 ttyw2
crw-rw-rw-  1 root   tty       3, 115 2008-05-09 15:53 ttyw3
crw-rw-rw-  1 root   tty       3, 116 2008-05-09 15:53 ttyw4
crw-rw-rw-  1 root   tty       3, 117 2008-05-09 15:53 ttyw5
crw-rw-rw-  1 root   tty       3, 118 2008-05-09 15:53 ttyw6
crw-rw-rw-  1 root   tty       3, 119 2008-05-09 15:53 ttyw7
crw-rw-rw-  1 root   tty       3, 120 2008-05-09 15:53 ttyw8
crw-rw-rw-  1 root   tty       3, 121 2008-05-09 15:53 ttyw9
crw-rw-rw-  1 root   tty       3, 122 2008-05-09 15:53 ttywa
crw-rw-rw-  1 root   tty       3, 123 2008-05-09 15:53 ttywb
crw-rw-rw-  1 root   tty       3, 124 2008-05-09 15:53 ttywc
crw-rw-rw-  1 root   tty       3, 125 2008-05-09 15:53 ttywd
crw-rw-rw-  1 root   tty       3, 126 2008-05-09 15:53 ttywe
crw-rw-rw-  1 root   tty       3, 127 2008-05-09 15:53 ttywf
crw-rw-rw-  1 root   tty       3, 128 2008-05-09 15:53 ttyx0
crw-rw-rw-  1 root   tty       3, 129 2008-05-09 15:53 ttyx1
crw-rw-rw-  1 root   tty       3, 130 2008-05-09 15:53 ttyx2
crw-rw-rw-  1 root   tty       3, 131 2008-05-09 15:53 ttyx3
crw-rw-rw-  1 root   tty       3, 132 2008-05-09 15:53 ttyx4
crw-rw-rw-  1 root   tty       3, 133 2008-05-09 15:53 ttyx5
crw-rw-rw-  1 root   tty       3, 134 2008-05-09 15:53 ttyx6
crw-rw-rw-  1 root   tty       3, 135 2008-05-09 15:53 ttyx7
crw-rw-rw-  1 root   tty       3, 136 2008-05-09 15:53 ttyx8
crw-rw-rw-  1 root   tty       3, 137 2008-05-09 15:53 ttyx9
crw-rw-rw-  1 root   tty       3, 138 2008-05-09 15:53 ttyxa
crw-rw-rw-  1 root   tty       3, 139 2008-05-09 15:53 ttyxb
crw-rw-rw-  1 root   tty       3, 140 2008-05-09 15:53 ttyxc
crw-rw-rw-  1 root   tty       3, 141 2008-05-09 15:53 ttyxd
crw-rw-rw-  1 root   tty       3, 142 2008-05-09 15:53 ttyxe
crw-rw-rw-  1 root   tty       3, 143 2008-05-09 15:53 ttyxf
crw-rw-rw-  1 root   tty       3, 144 2008-05-09 15:53 ttyy0
crw-rw-rw-  1 root   tty       3, 145 2008-05-09 15:53 ttyy1
crw-rw-rw-  1 root   tty       3, 146 2008-05-09 15:53 ttyy2
crw-rw-rw-  1 root   tty       3, 147 2008-05-09 15:53 ttyy3
crw-rw-rw-  1 root   tty       3, 148 2008-05-09 15:53 ttyy4
crw-rw-rw-  1 root   tty       3, 149 2008-05-09 15:53 ttyy5
crw-rw-rw-  1 root   tty       3, 150 2008-05-09 15:53 ttyy6
crw-rw-rw-  1 root   tty       3, 151 2008-05-09 15:53 ttyy7
crw-rw-rw-  1 root   tty       3, 152 2008-05-09 15:53 ttyy8
crw-rw-rw-  1 root   tty       3, 153 2008-05-09 15:53 ttyy9
crw-rw-rw-  1 root   tty       3, 154 2008-05-09 15:53 ttyya
crw-rw-rw-  1 root   tty       3, 155 2008-05-09 15:53 ttyyb
crw-rw-rw-  1 root   tty       3, 156 2008-05-09 15:53 ttyyc
crw-rw-rw-  1 root   tty       3, 157 2008-05-09 15:53 ttyyd
crw-rw-rw-  1 root   tty       3, 158 2008-05-09 15:53 ttyye
crw-rw-rw-  1 root   tty       3, 159 2008-05-09 15:53 ttyyf
crw-rw-rw-  1 root   tty       3, 160 2008-05-09 15:53 ttyz0
crw-rw-rw-  1 root   tty       3, 161 2008-05-09 15:53 ttyz1
crw-rw-rw-  1 root   tty       3, 162 2008-05-09 15:53 ttyz2
crw-rw-rw-  1 root   tty       3, 163 2008-05-09 15:53 ttyz3
crw-rw-rw-  1 root   tty       3, 164 2008-05-09 15:53 ttyz4
crw-rw-rw-  1 root   tty       3, 165 2008-05-09 15:53 ttyz5
crw-rw-rw-  1 root   tty       3, 166 2008-05-09 15:53 ttyz6
crw-rw-rw-  1 root   tty       3, 167 2008-05-09 15:53 ttyz7
crw-rw-rw-  1 root   tty       3, 168 2008-05-09 15:53 ttyz8
crw-rw-rw-  1 root   tty       3, 169 2008-05-09 15:53 ttyz9
crw-rw-rw-  1 root   tty       3, 170 2008-05-09 15:53 ttyza
crw-rw-rw-  1 root   tty       3, 171 2008-05-09 15:53 ttyzb
crw-rw-rw-  1 root   tty       3, 172 2008-05-09 15:53 ttyzc
crw-rw-rw-  1 root   tty       3, 173 2008-05-09 15:53 ttyzd
crw-rw-rw-  1 root   tty       3, 174 2008-05-09 15:53 ttyze
crw-rw-rw-  1 root   tty       3, 175 2008-05-09 15:53 ttyzf
crw-rw-rw-  1 root   root      1,   9 2008-05-09 10:23 urandom
crw-rw----  1 root   root    254,   0 2008-05-09 15:53 usbdev1.1_ep00
crw-rw----  1 root   root    254,   1 2008-05-09 15:53 usbdev1.1_ep81
crw-rw----  1 root   root    254,   2 2008-05-09 15:53 usbdev2.1_ep00
crw-rw----  1 root   root    254,   3 2008-05-09 15:53 usbdev2.1_ep81
crw-rw----  1 root   root    254,   4 2008-05-09 15:53 usbdev3.1_ep00
crw-rw----  1 root   root    254,   5 2008-05-09 15:53 usbdev3.1_ep81
crw-rw----  1 root   root      7,   0 2008-05-09 15:53 vcs
crw-rw----  1 root   root      7,   1 2008-05-09 10:24 vcs1
crw-rw----  1 root   root      7,   2 2008-05-09 10:23 vcs2
crw-rw----  1 root   root      7,   3 2008-05-09 10:23 vcs3
crw-rw----  1 root   root      7,   4 2008-05-09 10:23 vcs4
crw-rw----  1 root   root      7,   5 2008-05-09 10:23 vcs5
crw-rw----  1 root   root      7,   6 2008-05-09 10:23 vcs6
crw-rw----  1 root   root      7,   7 2008-05-09 10:24 vcs7
crw-rw----  1 root   root      7,   8 2008-05-09 15:53 vcs8
crw-rw----  1 root   root      7, 128 2008-05-09 15:53 vcsa
crw-rw----  1 root   root      7, 129 2008-05-09 10:24 vcsa1
crw-rw----  1 root   root      7, 130 2008-05-09 10:23 vcsa2
crw-rw----  1 root   root      7, 131 2008-05-09 10:23 vcsa3
crw-rw----  1 root   root      7, 132 2008-05-09 10:23 vcsa4
crw-rw----  1 root   root      7, 133 2008-05-09 10:23 vcsa5
crw-rw----  1 root   root      7, 134 2008-05-09 10:23 vcsa6
crw-rw----  1 root   root      7, 135 2008-05-09 10:24 vcsa7
crw-rw----  1 root   root      7, 136 2008-05-09 15:53 vcsa8
prw-r-----  1 syslog adm            0 2008-05-09 18:19 xconsole
crw-rw-rw-  1 root   root      1,   5 2008-05-09 15:53 zero

---

### Post by hermes0710 on 2008-05-09
> lrwxrwxrwx 1 root root 4 2008-05-09 10:23 sr0 -> scd0
lrwxrwxrwx 1 root root 4 2008-05-09 10:23 sr1 -> scd1

Ok, you must change the last two lines of fstab as below:

```

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0

```

and reboot

---

### Post by rajkhand on 2008-05-09
Thanks a million!!!

solved the problem

Raj

---

### Post by hermes0710 on 2008-05-09
Glad I helped :P

---

