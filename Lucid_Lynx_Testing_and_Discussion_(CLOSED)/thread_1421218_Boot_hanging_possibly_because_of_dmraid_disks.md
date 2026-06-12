---
title: "Boot hanging possibly because of dmraid disks"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by psusi on 2010-03-03
9.10 worked perfectly on my system so I gave Lucid Alpha 3 a try tonight.  The first big problem is that it hangs during boot.  After waiting for 3 minutes it finally indicated it had a udevadm settle timeout after 180 seconds for some reason, then failed to mount the sqashfs and dropped to the busybox shell.  After I mounted the sqashfs /dev/loop0 was already bound to and exiting, the boot continued, hung again for a 180 second udevadm timeout, then continued.  After eventually getting to an X desktop, X crashed after about 30 seconds then seemed ok, though the network interface was fouled up to the point that I had to cold power off and to get it working again... rebooting to 9.10 on the hd did not get it back online.  I repeated the process with the debug boot option to capture the initramfs.debug log which I will paste here.

My system is an Athlon 64 3200+ Black edition on an Asus K8V Deluxe motherboard using dual WD Raptor 36 gig 10krpm drives in a fake raid 0.

Any suggestions on how to further zero in on the problem are appreciated.  And it looks like the init script tried mounting my NTFS windows partition on the fakeraid looking for casper there.  What's up with that?

```

+ [ -z  ]
+ export resume=
+ maybe_break top
+ echo 
+ egrep -q (,|^)top(,|$)
+ export BOOT
+ run_scripts /scripts/init-top
+ initdir=/scripts/init-top
+ [ ! -d /scripts/init-top ]
+ [ -f /scripts/init-top/ORDER ]
+ . /scripts/init-top/ORDER
+ /scripts/init-top/all_generic_ide
+ [ -e /conf/param.conf ]
+ /scripts/init-top/blacklist
+ [ -e /conf/param.conf ]
+ /scripts/init-top/compcache
+ [ -e /conf/param.conf ]
+ /scripts/init-top/keymap
+ [ -e /conf/param.conf ]
+ /scripts/init-top/udev
+ [ -e /conf/param.conf ]
+ /scripts/init-top/framebuffer

[b]udevadm settle - timeout of 180 seconds reached, the event queue contains:
  /sys/devices/pci0000:00/0000:00:0a.0/host1/target1:0:0/1:0:0:0/block/sdb (7272)[/b]
+ [ -e /conf/param.conf ]
+ /scripts/init-top/console_setup
+ [ -e /conf/param.conf ]
+ /scripts/init-top/brltty
+ [ -e /conf/param.conf ]
+ /scripts/init-top/plymouth
+ [ -e /conf/param.conf ]
+ maybe_break modules
+ egrep -q (,|^)modules(,|$)
+ echo 
+ log_begin_msg Loading essential drivers...
+ [ -x /sbin/usplash_write ]
+ _log_msg Begin: Loading essential drivers... ...
+ [ n = y ]
+ echo Begin: Loading essential drivers... ...
Begin: Loading essential drivers... ...
+ load_modules
+ [ -e /conf/modules ]
+ cat+ conf/modules
read m
+ [ -z dm-mod ]
+ printf %.1s dm-mod
+ com=d
+ [ d = # ]
+ modprobe dm-mod
+ read m
+ [ -z dm-mirror ]
+ printf %.1s dm-mirror
+ com=d
+ [ d = # ]
+ modprobe dm-mirror
+ read m
+ [ -z dm-raid45 ]
+ printf %.1s dm-raid45
+ com=d
+ [ d = # ]
+ modprobe dm-raid45
+ read m
+ log_end_msg
+ [ -x /sbin/usplash_write ]
+ _log_msg Done.
+ [ n = y ]
+ echo Done.
Done.
+ maybe_break premount
+ echo 
+ egrep -q (,|^)premount(,|$)
+ [ n != y ]
+ log_begin_msg Running /scripts/init-premount
+ [ -x /sbin/usplash_write ]
+ _log_msg Begin: Running /scripts/init-premount ...
+ [ n = y ]
+ echo Begin: Running /scripts/init-premount ...
Begin: Running /scripts/init-premount ...
+ run_scripts /scripts/init-premount
+ initdir=/scripts/init-premount
+ [ ! -d /scripts/init-premount ]
+ [ -f /scripts/init-premount/ORDER ]
+ [ -x /usr/bin/tsort ]
+ get_prereqs
+ set_initlist
+ unset initlist
+ [ /scripts/init-premount/brltty = /scripts/init-premount/* ]
+ [ ! -x /scripts/init-premount/brltty ]
+ [  = y ]
+ continue
+ reduce_prereqs
+ unset runlist
+ set --
+ i=0
+ [ 0 -ne 0 ]
+ call_scripts
+ [ n != y ]
+ log_end_msg
+ [ -x /sbin/usplash_write ]
+ _log_msg Done.
+ [ n = y ]
+ echo Done.
Done.
+ maybe_break mount
+ echo 
+ egrep -q (,|^)mount(,|$)
+ log_begin_msg Mounting root file system...
+ [ -x /sbin/usplash_write ]
+ _log_msg Begin: Mounting root file system... ...
+ [ n = y ]
+ echo Begin: Mounting root file system... ...
Begin: Mounting root file system... ...
+ . /scripts/casper
+ export PATH=/usr/bin:/usr/sbin:/bin:/sbin
+ mountpoint=/cdrom
+ LIVE_MEDIA_PATH=casper
+ root_persistence=casper-rw
+ home_persistence=home-rw
+ root_snapshot_label=casper-sn
+ home_snapshot_label=home-sn
+ USERNAME=casper
+ USERFULLNAME=Live session user
+ HOST=live
+ BUILD_SYSTEM=Custom
+ mkdir -p /cdrom
+ tried=/tmp/tried
+ [ -f /etc/casper.conf ]
+ . /etc/casper.conf
+ export USERNAME=ubuntu
+ export USERFULLNAME=Live session user
+ export HOST=ubuntu
+ export BUILD_SYSTEM=Ubuntu
+ export USERNAME USERFULLNAME HOST BUILD_SYSTEM
+ . /scripts/casper-helpers
+ [ Ubuntu = Debian ]
+ [ Ubuntu = Ubuntu ]
+ MP_QUIET=-q
+ [ ! -x /bin/fstype ]
+ [ ! -f /casper.vars ]
+ touch /casper.vars
+ parse_numeric
+ return
+ mountroot
+ exec
+ exec
+ exec
+ exec
+ tailpid=32765
+ parse_cmdline
+ tail -f casper.log
+ cat /proc/cmdline
+ [  =  ]
+ export UNIONFS=aufs
+ set_usplash_timeout
+ [ -x /sbin/usplash_write ]
+ start_usplash_pulse
+ [ -x /sbin/usplash_write ]
+ [ n != y ]
+ log_begin_msg Running /scripts/casper-premount
+ [ -x /sbin/usplash_write ]
+ _log_msg Begin: Running /scripts/casper-premount ...
+ [ n = y ]
+ echo Begin: Running /scripts/casper-premount ...
Begin: Running /scripts/casper-premount ...
+ run_scripts /scripts/casper-premount
+ initdir=/scripts/casper-premount
+ [ ! -d /scripts/casper-premount ]
+ [ -f /scripts/casper-premount/ORDER ]
+ . /scripts/casper-premount/ORDER
+ /scripts/casper-premount/10driver_updates
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-premount/20iso_scan
+ [ -e /conf/param.conf ]
+ /scripts/casper-premount/30custom_installation
+ [ -e /conf/param.conf ]
+ [ n != y ]
+ log_end_msg
+ [ -x /sbin/usplash_write ]
+ _log_msg Done.
+ [ n = y ]
+ echo Done.
Done.
+ set_usplash_timeout
+ [ -x /sbin/usplash_write ]
+ [ ! -z  ]
+ i=0
+ [ 0 -lt 60 ]
+ find_livefs 0
+ timeout=0
+ [ ! -z  ]
+ [ -n  ]
+ egrep -v /(loop|ram|fd)
+ echo /sys/block/dm-0 /sys/block/dm-1 /sys/block/dm-2 /sys/block/dm-3 /sys/block/loop0 /sys/block/loop1 /sys/block/loop2 /sys/block/loop3 /sys/block/loop4 /sys/block/loop5 /sys/block/loop6 /sys/block/loop7 /sys/block/ram0 /sys/block/ram1 /sys/block/ram10 /sys/block/ram11 /sys/block/ram12 /sys/block/ram13 /sys/block/ram14 /sys/block/ram15 /sys/block/ram2 /sys/block/ram3 /sys/block/ram4 /sys/block/ram5 /sys/block/ram6 /sys/block/ram7 /sys/block/ram8 /sys/block/ram9 /sys/block/sda /sys/block/sdb /sys/block/sr0
+ tr   \n
+ sys2dev /sys/block/dm-0
+ sysdev=/block/dm-0
+ /sbin/udevadm info -q name -p /block/dm-0
+ echo /dev/mapper/nvidia_ahhfbbff
+ devname=/dev/mapper/nvidia_ahhfbbff
+ [ -e /dev/mapper/nvidia_ahhfbbff ]
+ get_fstype /dev/mapper/nvidia_ahhfbbff
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=unknown FSSIZE=0
+ FSTYPE=unknown FSSIZE=0
+ [ unknown != unknown ]
+ /sbin/blkid -s TYPE -o value /dev/mapper/nvidia_ahhfbbff
+ fstype=
+ /lib/udev/cdrom_id /dev/mapper/nvidia_ahhfbbff
+ is_nice_device /sys/block/dm-0
+ sysfs_path=/block/dm-0
+ /lib/udev/path_id /block/dm-0
+ egrep -q ID_PATH=(usb|pci-[^-]*-(ide|scsi|usb)|platform-orion-ehci|platform-mmc|platform-mxsdhci)
+ echo /block/dm-0
+ grep -q ^/block/dm-
+ return 0
+ subdevices /sys/block/dm-0
+ sysblock=/sys/block/dm-0
+ r=
+ [ -e /sys/block/dm-0/dev ]
+ r= /sys/block/dm-0
+ [ -e /sys/block/dm-0/alignment_offset/dev ]
+ [ -e /sys/block/dm-0/bdi/dev ]
+ [ -e /sys/block/dm-0/capability/dev ]
+ [ -e /sys/block/dm-0/dev/dev ]
+ [ -e /sys/block/dm-0/dm/dev ]
+ [ -e /sys/block/dm-0/ext_range/dev ]
+ [ -e /sys/block/dm-0/holders/dev ]
+ [ -e /sys/block/dm-0/inflight/dev ]
+ [ -e /sys/block/dm-0/power/dev ]
+ [ -e /sys/block/dm-0/queue/dev ]
+ [ -e /sys/block/dm-0/range/dev ]
+ [ -e /sys/block/dm-0/removable/dev ]
+ [ -e /sys/block/dm-0/ro/dev ]
+ [ -e /sys/block/dm-0/size/dev ]
+ [ -e /sys/block/dm-0/slaves/dev ]
+ [ -e /sys/block/dm-0/stat/dev ]
+ [ -e /sys/block/dm-0/subsystem/dev ]
+ [ -e /sys/block/dm-0/trace/dev ]
+ [ -e /sys/block/dm-0/uevent/dev ]
+ echo /sys/block/dm-0
+ check_dev /sys/block/dm-0
+ sysdev=/sys/block/dm-0
+ devname=
+ skip_uuid_check=
+ [ -z  ]
+ sys2dev /sys/block/dm-0
+ sysdev=/block/dm-0
+ /sbin/udevadm info -q name -p /block/dm-0
+ echo /dev/mapper/nvidia_ahhfbbff
+ devname=/dev/mapper/nvidia_ahhfbbff
+ [ -d /dev/mapper/nvidia_ahhfbbff ]
+ [ -e /dev/mapper/nvidia_ahhfbbff ]
+ [ -n  ]
+ get_fstype /dev/mapper/nvidia_ahhfbbff
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=unknown FSSIZE=0
+ FSTYPE=unknown FSSIZE=0
+ [ unknown != unknown ]
+ /sbin/blkid -s TYPE -o value /dev/mapper/nvidia_ahhfbbff
+ fstype=
+ is_supported_fs
+ fstype=
+ return 1
+ [ -n  ]
+ return 1
+ sys2dev /sys/block/dm-1
+ sysdev=/block/dm-1
+ /sbin/udevadm info -q name -p /block/dm-1
+ echo /dev/mapper/nvidia_ahhfbbff1
+ devname=/dev/mapper/nvidia_ahhfbbff1
+ [ -e /dev/mapper/nvidia_ahhfbbff1 ]
+ get_fstype /dev/mapper/nvidia_ahhfbbff1
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=unknown FSSIZE=0
+ FSTYPE=unknown FSSIZE=0
+ [ unknown != unknown ]
+ /sbin/blkid -s TYPE -o value /dev/mapper/nvidia_ahhfbbff1
+ fstype=ntfs
+ /lib/udev/cdrom_id /dev/mapper/nvidia_ahhfbbff1
+ is_nice_device /sys/block/dm-1
+ sysfs_path=/block/dm-1
+ /lib/udev/path_id /block/dm-1
+ egrep -q ID_PATH=(usb|pci-[^-]*-(ide|scsi|usb)|platform-orion-ehci|platform-mmc|platform-mxsdhci)
+ echo /block/dm-1
+ grep -q ^/block/dm-
+ return 0
+ subdevices /sys/block/dm-1
+ sysblock=/sys/block/dm-1
+ r=
+ [ -e /sys/block/dm-1/dev ]
+ r= /sys/block/dm-1
+ [ -e /sys/block/dm-1/alignment_offset/dev ]
+ [ -e /sys/block/dm-1/bdi/dev ]
+ [ -e /sys/block/dm-1/capability/dev ]
+ [ -e /sys/block/dm-1/dev/dev ]
+ [ -e /sys/block/dm-1/dm/dev ]
+ [ -e /sys/block/dm-1/ext_range/dev ]
+ [ -e /sys/block/dm-1/holders/dev ]
+ [ -e /sys/block/dm-1/inflight/dev ]
+ [ -e /sys/block/dm-1/power/dev ]
+ [ -e /sys/block/dm-1/queue/dev ]
+ [ -e /sys/block/dm-1/range/dev ]
+ [ -e /sys/block/dm-1/removable/dev ]
+ [ -e /sys/block/dm-1/ro/dev ]
+ [ -e /sys/block/dm-1/size/dev ]
+ [ -e /sys/block/dm-1/slaves/dev ]
+ [ -e /sys/block/dm-1/stat/dev ]
+ [ -e /sys/block/dm-1/subsystem/dev ]
+ [ -e /sys/block/dm-1/trace/dev ]
+ [ -e /sys/block/dm-1/uevent/dev ]
+ echo /sys/block/dm-1
+ check_dev /sys/block/dm-1
+ sysdev=/sys/block/dm-1
+ devname=
+ skip_uuid_check=
+ [ -z  ]
+ sys2dev /sys/block/dm-1
+ sysdev=/block/dm-1
+ /sbin/udevadm info -q name -p /block/dm-1
+ echo /dev/mapper/nvidia_ahhfbbff1
+ devname=/dev/mapper/nvidia_ahhfbbff1
+ [ -d /dev/mapper/nvidia_ahhfbbff1 ]
+ [ -e /dev/mapper/nvidia_ahhfbbff1 ]
+ [ -n  ]
+ get_fstype /dev/mapper/nvidia_ahhfbbff1
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=unknown FSSIZE=0
+ FSTYPE=unknown FSSIZE=0
+ [ unknown != unknown ]
+ /sbin/blkid -s TYPE -o value /dev/mapper/nvidia_ahhfbbff1
+ fstype=ntfs
+ is_supported_fs ntfs
+ fstype=ntfs
+ return 0
+ blkid -o value -s UUID /dev/mapper/nvidia_ahhfbbff1
+ devuid=02B0DB63B0DB5C2B
+ [ -n 02B0DB63B0DB5C2B ]
+ grep -qs \<02B0DB63B0DB5C2B\> /tmp/tried
+ mount -t ntfs -o ro,noatime /dev/mapper/nvidia_ahhfbbff1 /cdrom
+ [ -n 02B0DB63B0DB5C2B ]
+ echo 02B0DB63B0DB5C2B
+ is_casper_path /cdrom
+ path=/cdrom
+ [ -d /cdrom/casper ]
+ return 1
+ umount /cdrom
+ [ -n  ]
+ return 1
+ sys2dev /sys/block/dm-2
+ sysdev=/block/dm-2
+ /sbin/udevadm info -q name -p /block/dm-2
+ echo /dev/mapper/nvidia_ahhfbbff2
+ devname=/dev/mapper/nvidia_ahhfbbff2
+ [ -e /dev/mapper/nvidia_ahhfbbff2 ]
+ get_fstype /dev/mapper/nvidia_ahhfbbff2
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=swap FSSIZE=0
+ FSTYPE=swap FSSIZE=0
+ [ swap != unknown ]
+ echo swap
+ return 0
+ fstype=swap
+ /lib/udev/cdrom_id /dev/mapper/nvidia_ahhfbbff2
+ is_nice_device /sys/block/dm-2
+ sysfs_path=/block/dm-2
+ /lib/udev/path_id /block/dm-2
+ egrep -q ID_PATH=(usb|pci-[^-]*-(ide|scsi|usb)|platform-orion-ehci|platform-mmc|platform-mxsdhci)
+ echo /block/dm-2
+ grep -q ^/block/dm-
+ return 0
+ subdevices /sys/block/dm-2
+ sysblock=/sys/block/dm-2
+ r=
+ [ -e /sys/block/dm-2/dev ]
+ r= /sys/block/dm-2
+ [ -e /sys/block/dm-2/alignment_offset/dev ]
+ [ -e /sys/block/dm-2/bdi/dev ]
+ [ -e /sys/block/dm-2/capability/dev ]
+ [ -e /sys/block/dm-2/dev/dev ]
+ [ -e /sys/block/dm-2/dm/dev ]
+ [ -e /sys/block/dm-2/ext_range/dev ]
+ [ -e /sys/block/dm-2/holders/dev ]
+ [ -e /sys/block/dm-2/inflight/dev ]
+ [ -e /sys/block/dm-2/power/dev ]
+ [ -e /sys/block/dm-2/queue/dev ]
+ [ -e /sys/block/dm-2/range/dev ]
+ [ -e /sys/block/dm-2/removable/dev ]
+ [ -e /sys/block/dm-2/ro/dev ]
+ [ -e /sys/block/dm-2/size/dev ]
+ [ -e /sys/block/dm-2/slaves/dev ]
+ [ -e /sys/block/dm-2/stat/dev ]
+ [ -e /sys/block/dm-2/subsystem/dev ]
+ [ -e /sys/block/dm-2/trace/dev ]
+ [ -e /sys/block/dm-2/uevent/dev ]
+ echo /sys/block/dm-2
+ check_dev /sys/block/dm-2
+ sysdev=/sys/block/dm-2
+ devname=
+ skip_uuid_check=
+ [ -z  ]
+ sys2dev /sys/block/dm-2
+ sysdev=/block/dm-2
+ /sbin/udevadm info -q name -p /block/dm-2
+ echo /dev/mapper/nvidia_ahhfbbff2
+ devname=/dev/mapper/nvidia_ahhfbbff2
+ [ -d /dev/mapper/nvidia_ahhfbbff2 ]
+ [ -e /dev/mapper/nvidia_ahhfbbff2 ]
+ [ -n  ]
+ get_fstype /dev/mapper/nvidia_ahhfbbff2
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=swap FSSIZE=0
+ FSTYPE=swap FSSIZE=0
+ [ swap != unknown ]
+ echo swap
+ return 0
+ fstype=swap
+ is_supported_fs swap
+ fstype=swap
+ return 1
+ [ -n  ]
+ return 1
+ sys2dev /sys/block/dm-3
+ sysdev=/block/dm-3
+ /sbin/udevadm info -q name -p /block/dm-3
+ echo /dev/mapper/nvidia_ahhfbbff3
+ devname=/dev/mapper/nvidia_ahhfbbff3
+ [ -e /dev/mapper/nvidia_ahhfbbff3 ]
+ get_fstype /dev/mapper/nvidia_ahhfbbff3
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=ext4 FSSIZE=31839002624
+ FSTYPE=ext4 FSSIZE=31839002624
+ [ ext4 != unknown ]
+ echo ext4
+ return 0
+ fstype=ext4
+ /lib/udev/cdrom_id /dev/mapper/nvidia_ahhfbbff3
+ is_nice_device /sys/block/dm-3
+ sysfs_path=/block/dm-3
+ /lib/udev/path_id /block/dm-3
+ egrep -q ID_PATH=(usb|pci-[^-]*-(ide|scsi|usb)|platform-orion-ehci|platform-mmc|platform-mxsdhci)
+ echo /block/dm-3
+ grep -q ^/block/dm-
+ return 0
+ subdevices /sys/block/dm-3
+ sysblock=/sys/block/dm-3
+ r=
+ [ -e /sys/block/dm-3/dev ]
+ r= /sys/block/dm-3
+ [ -e /sys/block/dm-3/alignment_offset/dev ]
+ [ -e /sys/block/dm-3/bdi/dev ]
+ [ -e /sys/block/dm-3/capability/dev ]
+ [ -e /sys/block/dm-3/dev/dev ]
+ [ -e /sys/block/dm-3/dm/dev ]
+ [ -e /sys/block/dm-3/ext_range/dev ]
+ [ -e /sys/block/dm-3/holders/dev ]
+ [ -e /sys/block/dm-3/inflight/dev ]
+ [ -e /sys/block/dm-3/power/dev ]
+ [ -e /sys/block/dm-3/queue/dev ]
+ [ -e /sys/block/dm-3/range/dev ]
+ [ -e /sys/block/dm-3/removable/dev ]
+ [ -e /sys/block/dm-3/ro/dev ]
+ [ -e /sys/block/dm-3/size/dev ]
+ [ -e /sys/block/dm-3/slaves/dev ]
+ [ -e /sys/block/dm-3/stat/dev ]
+ [ -e /sys/block/dm-3/subsystem/dev ]
+ [ -e /sys/block/dm-3/trace/dev ]
+ [ -e /sys/block/dm-3/uevent/dev ]
+ echo /sys/block/dm-3
+ check_dev /sys/block/dm-3
+ sysdev=/sys/block/dm-3
+ devname=
+ skip_uuid_check=
+ [ -z  ]
+ sys2dev /sys/block/dm-3
+ sysdev=/block/dm-3
+ /sbin/udevadm info -q name -p /block/dm-3
+ echo /dev/mapper/nvidia_ahhfbbff3
+ devname=/dev/mapper/nvidia_ahhfbbff3
+ [ -d /dev/mapper/nvidia_ahhfbbff3 ]
+ [ -e /dev/mapper/nvidia_ahhfbbff3 ]
+ [ -n  ]
+ get_fstype /dev/mapper/nvidia_ahhfbbff3
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=ext4 FSSIZE=31839002624
+ FSTYPE=ext4 FSSIZE=31839002624
+ [ ext4 != unknown ]
+ echo ext4
+ return 0
+ fstype=ext4
+ is_supported_fs ext4
+ fstype=ext4
+ return 0
+ blkid -o value -s UUID /dev/mapper/nvidia_ahhfbbff3
+ devuid=825cce04-7c30-4d48-827c-ac17443dff12
+ [ -n 825cce04-7c30-4d48-827c-ac17443dff12 ]
+ grep -qs \<825cce04-7c30-4d48-827c-ac17443dff12\> /tmp/tried
+ mount -t ext4 -o ro,noatime /dev/mapper/nvidia_ahhfbbff3 /cdrom
+ [ -n 825cce04-7c30-4d48-827c-ac17443dff12 ]
+ echo 825cce04-7c30-4d48-827c-ac17443dff12
+ is_casper_path /cdrom
+ path=/cdrom
+ [ -d /cdrom/casper ]
+ return 1
+ umount /cdrom
+ [ -n  ]
+ return 1
+ sys2dev /sys/block/sda
+ sysdev=/block/sda
+ /sbin/udevadm info -q name -p /block/sda
+ echo /dev/sda
+ devname=/dev/sda
+ [ -e /dev/sda ]
+ get_fstype /dev/sda
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=unknown FSSIZE=0
+ FSTYPE=unknown FSSIZE=0
+ [ unknown != unknown ]
+ /sbin/blkid -s TYPE -o value /dev/sda
+ fstype=via_raid_member
+ /lib/udev/cdrom_id /dev/sda
+ is_nice_device /sys/block/sda
+ sysfs_path=/block/sda
+ /lib/udev/path_id /block/sda
+ egrep -q ID_PATH=(usb|pci-[^-]*-(ide|scsi|usb)|platform-orion-ehci|platform-mmc|platform-mxsdhci)
+ return 0
+ subdevices /sys/block/sda
+ sysblock=/sys/block/sda
+ r=
+ [ -e /sys/block/sda/dev ]
+ r= /sys/block/sda
+ [ -e /sys/block/sda/alignment_offset/dev ]
+ [ -e /sys/block/sda/bdi/dev ]
+ [ -e /sys/block/sda/capability/dev ]
+ [ -e /sys/block/sda/dev/dev ]
+ [ -e /sys/block/sda/device/dev ]
+ [ -e /sys/block/sda/ext_range/dev ]
+ [ -e /sys/block/sda/holders/dev ]
+ [ -e /sys/block/sda/inflight/dev ]
+ [ -e /sys/block/sda/power/dev ]
+ [ -e /sys/block/sda/queue/dev ]
+ [ -e /sys/block/sda/range/dev ]
+ [ -e /sys/block/sda/removable/dev ]
+ [ -e /sys/block/sda/ro/dev ]
+ [ -e /sys/block/sda/size/dev ]
+ [ -e /sys/block/sda/slaves/dev ]
+ [ -e /sys/block/sda/stat/dev ]
+ [ -e /sys/block/sda/subsystem/dev ]
+ [ -e /sys/block/sda/trace/dev ]
+ [ -e /sys/block/sda/uevent/dev ]
+ echo /sys/block/sda
+ check_dev /sys/block/sda
+ sysdev=/sys/block/sda
+ devname=
+ skip_uuid_check=
+ [ -z  ]
+ sys2dev /sys/block/sda
+ sysdev=/block/sda
+ /sbin/udevadm info -q name -p /block/sda
+ echo /dev/sda
+ devname=/dev/sda
+ [ -d /dev/sda ]
+ [ -e /dev/sda ]
+ [ -n  ]
+ get_fstype /dev/sda
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=unknown FSSIZE=0
+ FSTYPE=unknown FSSIZE=0
+ [ unknown != unknown ]
+ /sbin/blkid -s TYPE -o value /dev/sda
+ fstype=via_raid_member
+ is_supported_fs via_raid_member
+ fstype=via_raid_member
+ return 1
+ [ -n  ]
+ return 1
+ sys2dev /sys/block/sdb
+ sysdev=/block/sdb
+ /sbin/udevadm info -q name -p /block/sdb
+ echo /dev/sdb
+ devname=/dev/sdb
+ [ -e /dev/sdb ]
+ get_fstype /dev/sdb
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=unknown FSSIZE=0
+ FSTYPE=unknown FSSIZE=0
+ [ unknown != unknown ]
+ /sbin/blkid -s TYPE -o value /dev/sdb
+ fstype=via_raid_member
+ /lib/udev/cdrom_id /dev/sdb
+ is_nice_device /sys/block/sdb
+ sysfs_path=/block/sdb
+ /lib/udev/path_id /block/sdb
+ egrep -q ID_PATH=(usb|pci-[^-]*-(ide|scsi|usb)|platform-orion-ehci|platform-mmc|platform-mxsdhci)
+ return 0
+ subdevices /sys/block/sdb
+ sysblock=/sys/block/sdb
+ r=
+ [ -e /sys/block/sdb/dev ]
+ r= /sys/block/sdb
+ [ -e /sys/block/sdb/alignment_offset/dev ]
+ [ -e /sys/block/sdb/bdi/dev ]
+ [ -e /sys/block/sdb/capability/dev ]
+ [ -e /sys/block/sdb/dev/dev ]
+ [ -e /sys/block/sdb/device/dev ]
+ [ -e /sys/block/sdb/ext_range/dev ]
+ [ -e /sys/block/sdb/holders/dev ]
+ [ -e /sys/block/sdb/inflight/dev ]
+ [ -e /sys/block/sdb/power/dev ]
+ [ -e /sys/block/sdb/queue/dev ]
+ [ -e /sys/block/sdb/range/dev ]
+ [ -e /sys/block/sdb/removable/dev ]
+ [ -e /sys/block/sdb/ro/dev ]
+ [ -e /sys/block/sdb/size/dev ]
+ [ -e /sys/block/sdb/slaves/dev ]
+ [ -e /sys/block/sdb/stat/dev ]
+ [ -e /sys/block/sdb/subsystem/dev ]
+ [ -e /sys/block/sdb/trace/dev ]
+ [ -e /sys/block/sdb/uevent/dev ]
+ echo /sys/block/sdb
+ check_dev /sys/block/sdb
+ sysdev=/sys/block/sdb
+ devname=
+ skip_uuid_check=
+ [ -z  ]
+ sys2dev /sys/block/sdb
+ sysdev=/block/sdb
+ /sbin/udevadm info -q name -p /block/sdb
+ echo /dev/sdb
+ devname=/dev/sdb
+ [ -d /dev/sdb ]
+ [ -e /dev/sdb ]
+ [ -n  ]
+ get_fstype /dev/sdb
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=unknown FSSIZE=0
+ FSTYPE=unknown FSSIZE=0
+ [ unknown != unknown ]
+ /sbin/blkid -s TYPE -o value /dev/sdb
+ fstype=via_raid_member
+ is_supported_fs via_raid_member
+ fstype=via_raid_member
+ return 1
+ [ -n  ]
+ return 1
+ sys2dev /sys/block/sr0
+ sysdev=/block/sr0
+ /sbin/udevadm info -q name -p /block/sr0
+ echo /dev/sr0
+ devname=/dev/sr0
+ [ -e /dev/sr0 ]
+ get_fstype /dev/sr0
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=iso9660 FSSIZE=0
+ FSTYPE=iso9660 FSSIZE=0
+ [ iso9660 != unknown ]
+ echo iso9660
+ return 0
+ fstype=iso9660
+ /lib/udev/cdrom_id /dev/sr0
+ check_dev null /dev/sr0
+ sysdev=null
+ devname=/dev/sr0
+ skip_uuid_check=
+ [ -z /dev/sr0 ]
+ [ -d /dev/sr0 ]
+ [ -e /dev/sr0 ]
+ [ -n  ]
+ get_fstype /dev/sr0
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=iso9660 FSSIZE=0
+ FSTYPE=iso9660 FSSIZE=0
+ [ iso9660 != unknown ]
+ echo iso9660
+ return 0
+ fstype=iso9660
+ is_supported_fs iso9660
+ fstype=iso9660
+ return 0
+ blkid -o value -s UUID /dev/sr0
+ devuid=
+ [ -n  ]
+ mount -t iso9660 -o ro,noatime /dev/sr0 /cdrom
+ [ -n  ]
+ is_casper_path /cdrom
+ path=/cdrom
+ [ -d /cdrom/casper ]
+ echo /cdrom/casper/filesystem.squashfs
+ [ /cdrom/casper/filesystem.squashfs != /cdrom/casper/*.squashfs ]
+ return 0
+ [  ]
+ matches_uuid /cdrom
+ [  ]
+ [ ! -e /conf/uuid.conf ]
+ path=/cdrom
+ cat /conf/uuid.conf
+ uuid=7579f6ea-83b0-40d7-add6-0951aaf747f6
+ [ -e /cdrom/.disk/casper-uuid-generic ]
+ cat /cdrom/.disk/casper-uuid-generic
+ try_uuid=7579f6ea-83b0-40d7-add6-0951aaf747f6
+ [ 7579f6ea-83b0-40d7-add6-0951aaf747f6 = 7579f6ea-83b0-40d7-add6-0951aaf747f6 ]
+ return 0
+ echo /cdrom
+ return 0
+ return 0
+ livefs_root=/cdrom
+ [ /cdrom ]
+ break
+ [ -z /cdrom ]
+ [  ]
+ [  ]
+ [  ]
+ mount_images_in_directory /cdrom /root
+ directory=/cdrom
+ rootmnt=/root
+ match_files_in_dir /cdrom/casper/*.squashfs
+ local pattern=/cdrom/casper/*.squashfs
+ echo /cdrom/casper/filesystem.squashfs
+ [ /cdrom/casper/filesystem.squashfs != /cdrom/casper/*.squashfs ]
+ return 0
+ setup_unionfs /cdrom/casper /root
+ image_directory=/cdrom/casper
+ rootmnt=/root
+ modprobe -q -b aufs
+ grep -q ^aufs$
+ cut -f2 /proc/filesystems
+ croot=/
+ rofsstring=
+ rofslist=
+ [  = nfs ]
+ [ aufs = aufs ]
+ roopt=rr
+ mkdir -p /
+ basename /cdrom/casper/*.ext2
+ imagename=*.ext2
+ [ -d /cdrom/casper/*.ext2 ]
+ [ -f /cdrom/casper/*.ext2 ]
+ basename /cdrom/casper/filesystem.squashfs
+ imagename=filesystem.squashfs
+ [ -d /cdrom/casper/filesystem.squashfs ]
+ [ -f /cdrom/casper/filesystem.squashfs ]
+ get_backing_device /cdrom/casper/filesystem.squashfs
+ setup_loop /cdrom/casper/filesystem.squashfs loop /sys/block/loop*
+ local fspath=/cdrom/casper/filesystem.squashfs
+ local module=loop
+ local pattern=/sys/block/loop*
+ local offset=
+ modprobe -q -b loop
+ /sbin/udevadm settle
+ [ loop = loop ]
+ [ ! -e /dev/loop0 ]
+ losetup -f
+ dev=/dev/loop0
+ [ /dev/loop0 ]
+ [ -n  ]
+ losetup /dev/loop0 /cdrom/casper/filesystem.squashfs
+ echo /dev/loop0
+ return 0
+ echo udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:0a.0/host0/target0:0:0/0:0:0:0/block/sda (13544) /dev/loop0
+ backdev=udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:0a.0/host0/target0:0:0/0:0:0:0/block/sda (13544) /dev/loop0
+ get_fstype udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:0a.0/host0/target0:0:0/0:0:0:0/block/sda (13544) /dev/loop0
+ local FSTYPE
+ local FSSIZE
/init: line 7: can't open udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:0a.0/host0/target0:0:0/0:0:0:0/block/sda (13544) /dev/loop0: no such file
+ fstype
+ eval
+ [  != unknown ]
+ echo
+ return 0
+ fstype=
+ [  = unknown ]
+ mkdir -p //filesystem.squashfs
+ mount -t  -o ro,noatime udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:0a.0/host0/target0:0:0/0:0:0:0/block/sda (13544) /dev/loop0 //filesystem.squashfs
mount: mounting udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:0a.0/host0/target0:0:0/0:0:0:0/block/sda (13544) /dev/loop0 on //filesystem.squashfs failed: No such device
+ panic Can not mount udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:0a.0/host0/target0:0:0/0:0:0:0/block/sda (13544) /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
+ [ -x /sbin/usplash_write ]
+ chvt 1
+ [ -n  ]
+ modprobe i8042
+ modprobe atkbd
+ run_scripts /scripts/panic
+ initdir=/scripts/panic
+ [ ! -d /scripts/panic ]
+ [ -f /scripts/panic/ORDER ]
+ [ -x /usr/bin/tsort ]
+ get_prereqs
+ set_initlist
+ unset initlist
+ [ /scripts/panic/console_setup = /scripts/panic/* ]
+ [ ! -x /scripts/panic/console_setup ]
+ [  = y ]
+ continue
+ [ /scripts/panic/keymap = /scripts/panic/* ]
+ [ ! -x /scripts/panic/keymap ]
+ [  = y ]
+ continue
+ reduce_prereqs
+ unset runlist
+ set --
+ i=0
+ [ 0 -ne 0 ]
+ call_scripts
+ echo Can not mount udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:0a.0/host0/target0:0:0/0:0:0:0/block/sda (13544) /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
Can not mount udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:0a.0/host0/target0:0:0/0:0:0:0/block/sda (13544) /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
+ PS1=(initramfs)  /bin/sh -i
+ rofsstring=//filesystem.squashfs=rr:
+ rofslist=//filesystem.squashfs 
+ basename /cdrom/casper/*.dir
+ imagename=*.dir
+ [ -d /cdrom/casper/*.dir ]
+ [ -f /cdrom/casper/*.dir ]
+ rofsstring=//filesystem.squashfs=rr
+ mkdir -p /cow
+ cowdevice=tmpfs
+ cow_fstype=tmpfs
+ cow_mountopt=rw,noatime,mode=755
+ [ -n  ]
+ mount -t tmpfs -o rw,noatime,mode=755 tmpfs /cow
+ mount -t aufs -o noatime,dirs=/cow=rw://filesystem.squashfs=rr aufs /root
+ [ -n  ]
+ [ -n  ]
+ mount -t squashfs
+ cut -d  -f 3
+ mkdir -p /root/rofs
+ [ aufs = unionfs-fuse ]
+ mount -o move /filesystem.squashfs /root/rofs
+ break
+ log_end_msg
+ [ -x /sbin/usplash_write ]
+ _log_msg Done.
+ [ n = y ]
+ echo Done.
Done.
+ [ aufs = unionfs-fuse ]
+ log_begin_msg Creating debconf-communicate fifo mechanism
+ [ -x /sbin/usplash_write ]
+ _log_msg Begin: Creating debconf-communicate fifo mechanism ...
+ [ n = y ]
+ echo Begin: Creating debconf-communicate fifo mechanism ...
Begin: Creating debconf-communicate fifo mechanism ...
+ mkfifo /tmp/debconf-in.fifo
+ mkfifo /tmp/debconf-out.fifo
+ DEBCONF_COMMUNICATE_PID=26468
+ [ ! -p /tmp/debconf-in.fifo ]
+ [ ! -p /tmp/debconf-out.fifo ]
+ log_end_msg
+ [ -x /sbin/usplash_write ]
+ _log_msg Done.
+ [ n = y ]
+ echo Done.
Done.
+ exec
+ maybe_break casper-bottom
+ chroot /root debconf-communicate -fnoninteractive casper
+ egrep -q (,|^)casper-bottom(,|$)
+ echo 
+ [ n != y ]
+ log_begin_msg Running /scripts/casper-bottom
+ [ -x /sbin/usplash_write ]
+ _log_msg Begin: Running /scripts/casper-bottom ...
+ [ n = y ]
+ echo Begin: Running /scripts/casper-bottom ...
Begin: Running /scripts/casper-bottom ...
+ run_scripts /scripts/casper-bottom
+ initdir=/scripts/casper-bottom
+ [ ! -d /scripts/casper-bottom ]
+ [ -f /scripts/casper-bottom/ORDER ]
+ . /scripts/casper-bottom/ORDER
+ /scripts/casper-bottom/01integrity_check
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/05mountpoints
Begin: Moving mount points... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/05mountpoints_lupin
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/10adduser
Begin: Adding live session user... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/10custom_installation
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/10ntfs_3g
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/12fstab
Begin: Configuring fstab... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/13swap
Begin: Setting up swap... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/14locales
Begin: Setting up locales... ...
Generating locales...
  en_US.UTF-8... done
Generation complete.
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/15autologin
Begin: Setting up automatic login... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/18hostname
Begin: Setting hostname... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/19keyboard
Begin: Setting up console keyboard... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/20xconfig
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/22gnome_panel_data
Begin: Configuring gnome-panel-data... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/22screensaver
Begin: Configuring screensaver... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/22serialtty
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/22sslcert
Begin: Regenerating SSL certificate... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/23etc_modules
Begin: Preconfiguring /etc/modules... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/23networking
Begin: Preconfiguring networking... ...

udevadm settle - timeout of 180 seconds reached, the event queue contains:
  /sys/devices/pci0000:00/0000:00:0a.0/host0/target0:0:0/0:0:0:0/block/sda (22474)
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/24preseed
Begin: Loading preseed file... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/25configure_init
Begin: Setting up init... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/30accessibility
Begin: Configuring accessibility options... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/31disable_update_notifier
Begin: Disabling update-notifier... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/32disable_hibernation
Begin: Configuring power management... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/33enable_apport_crashes
Begin: Enabling detection of crashes... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/34disable_kde_services
Begin: Disabling unnecessary KDE services... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/35fix_language_selector
Begin: Fixing language selector... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/36disable_trackerd
Begin: Disabling trackerd... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/37kubuntu_netbook_installer_link
Begin: Adding installer to Kubuntu Netbook favourites... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/40install_driver_updates
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/41apt_cdrom
Using CD-ROM mount point /media/apt/
Identifying.. [b71b8b0bc4ad49efffecaf65eadd1b42-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Ubuntu 10.04 _Lucid Lynx_ - Alpha amd64 (20100224.1)'
This disc is called: 
'Ubuntu 10.04 _Lucid Lynx_ - Alpha amd64 (20100224.1)'
Copying package lists...gpgv: Signature made Wed Feb 24 19:09:51 2010 UTC using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"

Reading Package Indexes... 0%

Reading Package Indexes... 3%

Reading Package Indexes... Done

Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Alpha amd64 (20100224.1)]/ lucid main restricted
Repeat this process for the rest of the CDs in your set.
W: Skipping nonexistent file /media/apt/dists/lucid/main/binary-amd64/Packages
W: Skipping nonexistent file /media/apt/dists/lucid/restricted/binary-amd64/Packages
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/43disable_updateinitramfs
Begin: Possibly disabling update-initramfs (useless on a live CD)... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/44pk_allow_ubuntu
Begin: Grant administrative PolicyKit pivilieges to default user... ...
Done.
+ [ -e /conf/param.conf ]
+ /scripts/casper-bottom/45disable_guest_account
Begin: Disabling gdm guest session functionality... ...
+ kill 32765
+ cp casper.log /root/var/log/
+ [ -f /etc/casper.conf ]
+ cp /etc/casper.conf /root/etc/
+ log_end_msg
+ [ -x /sbin/usplash_write ]
+ _log_msg Done.
+ [ n = y ]
+ echo Done.
Done.
+ maybe_break bottom
+ echo 
+ egrep -q (,|^)bottom(,|$)
+ [ n != y ]
+ log_begin_msg Running /scripts/init-bottom
+ [ -x /sbin/usplash_write ]
+ _log_msg Begin: Running /scripts/init-bottom ...
+ [ n = y ]
+ echo Begin: Running /scripts/init-bottom ...
Begin: Running /scripts/init-bottom ...
+ run_scripts /scripts/init-bottom
+ initdir=/scripts/init-bottom
+ [ ! -d /scripts/init-bottom ]
+ [ -f /scripts/init-bottom/ORDER ]
+ . /scripts/init-bottom/ORDER
+ /scripts/init-bottom/udev
+ [ -e /conf/param.conf ]
+ /scripts/init-bottom/plymouth
+ [ -e /conf/param.conf ]
+ [ n != y ]
+ log_end_msg
+ [ -x /sbin/usplash_write ]
+ _log_msg Done.
+ [ n = y ]
+ echo Done.
Done.
+ mount -n -o move /sys /root/sys
+ mount -n -o move /proc /root/proc
+ [ -n /sbin/init ]
+ [ ! -x /root/sbin/init ]
+ [ -z /sbin/init ]
+ [ ! -x /root/sbin/init ]
+ [ -n y ]
+ unset debug
+ maybe_break init
+ egrep -q (,|^)init(,|$)
+ echo 
+ exec run-init /root /sbin/init noquiet nosplash --
```

---

### Post by dizwell on 2010-03-22
Just wanting to confirm exactly the same behaviour in the new Beta version of 10.04 (64-bit), this time with an i7 860, 8GB RAM... and all my hard disks configured as 'fake raid' devices. Ubuntu 9.10 worked for me, too, but neither the 10.04 alpha nor the new beta is able to boot without 'udevadm settle - timeout of 180 seconds reached' messages.

I hope this is fixed before D-Day at the end of April!

---

### Post by nanog on 2010-03-22
Maybe dm raid is affected by same bug as md raid:

> Installation with /boot on RAID1 fails due to a bug when installing the bootloader to disk. This bug will be addressed for 10.04 Beta 2. (527401) 

[https://bugs.launchpad.net/bugs/527401](https://bugs.launchpad.net/bugs/527401)

---

### Post by psusi on 2010-03-22
No, this is bug [#534743](https://launchpad.net/bugs/534743).

---

