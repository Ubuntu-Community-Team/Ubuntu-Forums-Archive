---
title: "Would appreciate some UDEV rule help"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by nicoloks on 2010-02-13
Hi All,

Trying to create myself some UDEV rules to control the way my external USB Hard Drive is mounted on my Mythbuntu 9.10 install. This is my first dealing with creating my own UDEV rules, and not seeming to be having much luck. I created symlink from /media/External to /media/sdb1 to be my mount point and entered the following into /etc/udev/user.rules ;

```
KERNEL=="sd?1", ATTRS{vendor}=="WD", ATTRS{model}=="My Book 1110", NAME="%k", SYMLINK+="Exernal"
ACTION=="add", KERNEL=="sd?1", ATTRS{vendor}=="WD", ATTRS{model}=="My Book 1110", RUN+="/bin/mount -t ntfs -o  uid=mythtv,umask=000,utf8,flush,auto UUID=2B424FE96E9354D7 /media/External"
ACTION=="remove", KERNEL=="sd?1", ENV{ID_VENDOR}=="WD", ENV{ID_MODEL}="1110", RUN+="/bin/umount /media/External"
```

This is the output of "udevadm info -q all -n /dev/sdb1" ;

```
P: /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2:1.0/host5/target5:0:0/5:0:0:0/block/sdb/sdb1
N: sdb1
W: 26
S: block/8:17
S: disk/by-id/usb-WD_My_Book_1110_574341563533393137353631-0:0-part1
S: disk/by-path/pci-0000:00:02.1-usb-0:2:1.0-scsi-0:0:0:0-part1
S: disk/by-uuid/2B424FE96E9354D7
S: disk/by-label/Data
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2:1.0/host5/target5:0:0/5:0:0:0/block/sdb/sdb1
E: MAJOR=8
E: MINOR=17
E: DEVNAME=/dev/sdb1
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_VENDOR=WD
E: ID_VENDOR_ENC=WD\x20\x20\x20\x20\x20\x20
E: ID_VENDOR_ID=1058
E: ID_MODEL=My_Book_1110
E: ID_MODEL_ENC=My\x20Book\x201110\x20\x20\x20\x20
E: ID_MODEL_ID=1110
E: ID_REVISION=1030
E: ID_SERIAL=WD_My_Book_1110_574341563533393137353631-0:0
E: ID_SERIAL_SHORT=574341563533393137353631
E: ID_TYPE=disk
E: ID_INSTANCE=0:0
E: ID_BUS=usb
E: ID_USB_INTERFACES=:080650:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=usb-storage
E: ID_PATH=pci-0000:00:02.1-usb-0:2:1.0-scsi-0:0:0:0
E: ID_FS_UUID=2B424FE96E9354D7
E: ID_FS_UUID_ENC=2B424FE96E9354D7
E: ID_FS_LABEL=Data
E: ID_FS_LABEL_ENC=Data
E: ID_FS_TYPE=ntfs
E: ID_FS_USAGE=filesystem
E: DKD_PARTITION=1
E: DKD_PARTITION_SCHEME=mbr
E: DKD_PARTITION_NUMBER=1
E: DKD_PARTITION_TYPE=0x07
E: DKD_PARTITION_SIZE=999494866944
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:17 /dev/disk/by-id/usb-WD_My_Book_1110_574341563533393137353631-0:0-part1 /dev/disk/by-path/pci-0000:00:02.1-usb-0:2:1.0-scsi-0:0:0:0-part1 /dev/disk/by-uuid/2B424FE96E9354D7 /dev/disk/by-label/Data
```

What I was hoping would happen by doing this is when the drive is plugged in for it to be mounted using the mount command in the above UDEV rules, and unmounted when removed. This does appear to be happening though, and I don't know why.

Any help greatly appreciated as this is now the only real issue left I have with this new HTPC.

---

