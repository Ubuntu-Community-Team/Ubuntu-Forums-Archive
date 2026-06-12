---
title: "prepare boot Image for Amazon"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by MichaelVaknine on 2011-05-04
hi,
i ma trying to debootstrap a new image and load it to amazon.
the server is not booting.

the proccess is as follows:

dd if=/dev/zero of=/root/aws/debian-ami count=2 bs=1G
mkfs.ext3 -F /root/aws/debian-ami
mount -o loop /root/aws/debian-ami /chroot
debootstrap --arch amd64 lucid /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
cp run_chroot.sh /chroot/root/

chroot /chroot

echo -e 'auto lo\niface lo inet loopback\nauto eth0\niface eth0 inet dhcp' >> /etc/network/interfaces
echo "proc            /proc           proc    nodev,noexec,nosuid 0       0
dev/sda1 / ext3 defaults 0 1" > /etc/fstab
echo "127.0.0.1       localhost" > /etc/hosts
echo ebsempty > /etc/hostname
echo 'LANG="en_US.UTF-8"' > /etc/default/locale
echo "en_US.UTF-8 UTF-8" > /etc/locale.gen
echo "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse" > /etc/apt/sources.list
locale-gen en_US.UTF-8
mount /proc
mount /dev/pts
cd /dev
MAKEDEV console
MAKEDEV std
MAKEDEV sda
apt-get update
apt-get upgrade -y
apt-get install -y linux-image-2.6.32-24-server linux-image-2.6.32-309-ec2

exit
umount -l /chroot

ec2-bundle-image 
ec2-upload-bundle

when i try to start the machine the server is not booting correctly.
this is the log from the boot proccess

Bootdata ok (command line is  root=/dev/sda1 ro 4)

Linux version 2.6.16.33-xenU (root@dom0-0-50-45-1-a4-ee.z-2.aes0.internal) (gcc version 4.1.1 20070105 (Red Hat 4.1.1-52)) #2 SMP Wed Aug 15 17:27:36 SAST 2007

BIOS-provided physical RAM map:

 Xen: 0000000000000000 - 00000001e0800000 (usable)

Built 1 zonelists

Kernel command line:  root=/dev/sda1 ro 4

Initializing CPU#0

PID hash table entries: 4096 (order: 12, 131072 bytes)

Xen reported: 2659.996 MHz processor.

Console: colour dummy device 80x25

Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)

Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)

Software IO TLB disabled

Memory: 7708664k/7872512k available (2181k kernel code, 154964k reserved, 738k data, 140k init)

Calibrating delay using timer specific routine.. 5335.44 BogoMIPS (lpj=26677204)

Security Framework v1.0.0 initialized

Mount-cache hash table entries: 256

CPU: L1 I cache: 32K, L1 D cache: 32K

CPU: L2 cache: 6144K

CPU: Physical Processor ID: 0

CPU: Processor Core ID: 1

Brought up 1 CPUs

migration_cost=0

DMI not present or invalid.

Grant table initialized

NET: Registered protocol family 16

Initializing CPU#1

migration_cost=578

Brought up 2 CPUs

xen_mem: Initialising balloon driver.

IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $

VFS: Disk quotas dquot_6.5.1

Dquot-cache hash table entries: 512 (order 0, 4096 bytes)

Initializing Cryptographic API

io scheduler noop registered (default)

i8042.c: No controller found.

RAMDISK driver initialized: 16 RAM disks of 4096K size 1024 blocksize

Xen virtual console successfully installed as tty1

Event-channel device installed.

netfront: Initialising virtual ethernet driver.

Registering block device major 8

 sdb: unknown partition table

 sdc: unknown partition table

mice: PS/2 mouse device common for all mice

md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27

md: bitmap version 4.39

device-mapper: 4.5.0-ioctl (2005-10-04) initialised: [email]dm-devel@redhat.com[/email]

MC: drivers/edac/edac_mc.c version edac_mc  Ver: 2.0.0 Aug 15 2007

NET: Registered protocol family 2

netfront: device eth0 has flipping receive path.

IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)

TCP established hash table entries: 262144 (order: 10, 4194304 bytes)

TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)

TCP: Hash tables configured (established 262144 bind 65536)

TCP reno registered

TCP bic registered

NET: Registered protocol family 1

NET: Registered protocol family 17

NET: Registered protocol family 15

md: Autodetecting RAID arrays.

md: autorun ...

md: ... autorun DONE.

EXT3-fs: INFO: recovery required on readonly filesystem.

EXT3-fs: write access will be enabled during recovery.

kjournald starting.  Commit interval 5 seconds

EXT3-fs: recovery complete.

EXT3-fs: mounted filesystem with ordered data mode.

VFS: Mounted root (ext3 filesystem) readonly.

modprobe: FATAL: Could not load /lib/modules/2.6.16.33-xenU/modules.dep: No such file or directory


init: ureadahead main process (688) terminated with status 5

libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument
mountall:mountall.c:3204: Assertion failed in main: udev_monitor = udev_monitor_new_from_netlink (udev, "udev")
init: mountall main process (693) killed by ABRT signal

modprobe: FATAL: Could not load /lib/modules/2.6.16.33-xenU/modules.dep: No such file or directory


modprobe: FATAL: Could not load /lib/modules/2.6.16.33-xenU/modules.dep: No such file or directory


modprobe: FATAL: Could not load /lib/modules/2.6.16.33-xenU/modules.dep: No such file or directory


modprobe: FATAL: Could not load /lib/modules/2.6.16.33-xenU/modules.dep: No such file or directory


modprobe: FATAL: Could not load /lib/modules/2.6.16.33-xenU/modules.dep: No such file or directory


modprobe: FATAL: Could not load /lib/modules/2.6.16.33-xenU/modules.dep: No such file or directory


init: console-setup main process (696) terminated with status 1

General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
root@ebsempty:~#



i am missing something.

any help will be appreciated.

Michael

---

