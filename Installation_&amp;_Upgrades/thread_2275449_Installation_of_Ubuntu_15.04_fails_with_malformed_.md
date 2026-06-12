---
title: "Installation of Ubuntu 15.04 fails with malformed error message"
date: 2015-04-26
forum: Installation &amp; Upgrades
---

### Post by David_Jolley on 2015-04-26
I have booted into a Live-DVD environment of Ubuntu 15.04 - this is where I've posted this message from; I'm running 15.04 now - I know it basically works on my hardware.
The installer is vexing me somewhat though.

My computer has Windows 8.1 pre-installed, which I've transferred over to an SSD; this SSD (/dev/sda) contains the UEFI boot partition, along with the windows 8.1 system partition.  There is a second hard disk in the computer (/dev/sdb), which I've partitioned into 2, half is formatted as an NTFS filesystem, and the other half is empty (ie. not even with a partition allocating the space), ready to have Ubuntu 15.04 installed into it.

The computer uses an EFI pre-boot environment, windows 8 boots no problem and the ubuntu live DVD boots fine without turning off secure boot, into a 64 bit kernel:

ubuntu@ubuntu:~$ grep -i efi /var/log/syslog | head -n 2
Apr 26 12:40:38 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
Apr 26 12:40:38 ubuntu kernel: [    0.000000] efi: EFI v2.31 by INSYDE Corp.
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$ 

I start the "Install Ubuntu 15.04" application from my desktop.

At the welcome screen, I accept the "English" default and press the continue button.  On the next screen, I select "Download updates while installing" and "Install this third-party software", then press the continue button.
The syslog shows that some ubiquity is downloading and installing some software packages.  I go away and make a coffee.

After this compile has finished, the installer application looks like the attached image.

In the syslog, there is a stacktrace:

[FONT=system]Apr 26 13:07:02 ubuntu ubiquity: Setting up screen-resolution-extra (0.17.1) ...
Apr 26 13:07:03 ubuntu ubiquity: Setting up intel-microcode (3.20150121.1) ...
Apr 26 13:07:03 ubuntu ubiquity: update-initramfs is disabled since running on read-only media
Apr 26 13:07:03 ubuntu ubiquity: intel-microcode: microcode will be updated at next boot
Apr 26 13:07:03 ubuntu ubiquity: Processing triggers for dbus (1.8.12-1ubuntu5) ...
Apr 26 13:07:03 ubuntu ubiquity: Setting up nvidia-settings (346.59-0ubuntu1) ...
Apr 26 13:07:03 ubuntu ubiquity: Processing triggers for libc-bin (2.21-0ubuntu4) ...
Apr 26 13:07:03 ubuntu ubiquity: Processing triggers for ureadahead (0.100.0-19) ...
Apr 26 13:07:03 ubuntu ubiquity[3164]: debconffilter_done: ubi-prepare (current: ubi-prepare)
Apr 26 13:07:03 ubuntu ubiquity[3164]: Step_before = stepPrepare
Apr 26 13:07:03 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Apr 26 13:07:03 ubuntu kernel: [ 1681.857581] raid6: sse2x1    8746 MB/s
Apr 26 13:07:03 ubuntu kernel: [ 1681.925650] raid6: sse2x2   12252 MB/s
Apr 26 13:07:03 ubuntu kernel: [ 1681.993706] raid6: sse2x4   14668 MB/s
Apr 26 13:07:04 ubuntu kernel: [ 1682.061772] raid6: avx2x1   19216 MB/s
Apr 26 13:07:04 ubuntu kernel: [ 1682.129839] raid6: avx2x2   22363 MB/s
Apr 26 13:07:04 ubuntu kernel: [ 1682.197919] raid6: avx2x4   25666 MB/s
Apr 26 13:07:04 ubuntu kernel: [ 1682.197921] raid6: using algorithm avx2x4 (25666 MB/s)
Apr 26 13:07:04 ubuntu kernel: [ 1682.197922] raid6: using avx2x2 recovery algorithm
Apr 26 13:07:04 ubuntu kernel: [ 1682.199622] xor: automatically using best checksumming function:
Apr 26 13:07:04 ubuntu kernel: [ 1682.237946]    avx       : 31135.000 MB/sec
Apr 26 13:07:04 ubuntu kernel: [ 1682.375620] Btrfs loaded
Apr 26 13:07:04 ubuntu kernel: [ 1682.393266] JFS: nTxBlock = 8192, nTxLock = 65536
Apr 26 13:07:04 ubuntu kernel: [ 1682.500984] SGI XFS with ACLs, security attributes, realtime, no debug enabled
Apr 26 13:07:04 ubuntu partman:   No matching physical volumes found
Apr 26 13:07:04 ubuntu partman:   Reading all physical volumes.  This may take a while...
Apr 26 13:07:04 ubuntu partman:   No volume groups found
Apr 26 13:07:04 ubuntu partman-lvm:   No volume groups found
Apr 26 13:07:04 ubuntu systemd[1]: Device dev-disk-by\x2dpartlabel-Basic\x5cx20data\x5cx20partition.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda1 and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda4
Apr 26 13:07:06 ubuntu ntfsresize: ntfsresize v2014.2.15AR.3 (libntfs-3g)
Apr 26 13:07:06 ubuntu ntfsresize: Device name        : /dev/sda1
Apr 26 13:07:06 ubuntu ntfsresize: NTFS volume version: 3.1
Apr 26 13:07:06 ubuntu ntfsresize: Cluster size       : 4096 bytes
Apr 26 13:07:06 ubuntu ntfsresize: Current volume size: 419426816 bytes (420 MB)
Apr 26 13:07:06 ubuntu ntfsresize: Current device size: 419430400 bytes (420 MB)
Apr 26 13:07:06 ubuntu ntfsresize: Checking filesystem consistency ...
Apr 26 13:07:06 ubuntu ntfsresize: Accounting clusters ...
Apr 26 13:07:06 ubuntu ntfsresize: Space in use       : 291 MB (69.2%)
Apr 26 13:07:06 ubuntu ntfsresize: Collecting resizing constraints ...
Apr 26 13:07:06 ubuntu ntfsresize: You might resize at 290136064 bytes or 291 MB (freeing 129 MB).
Apr 26 13:07:06 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Apr 26 13:07:08 ubuntu ntfsresize: ntfsresize v2014.2.15AR.3 (libntfs-3g)
Apr 26 13:07:08 ubuntu ntfsresize: Device name        : /dev/sda4
Apr 26 13:07:08 ubuntu ntfsresize: NTFS volume version: 3.1
Apr 26 13:07:08 ubuntu ntfsresize: Cluster size       : 4096 bytes
Apr 26 13:07:08 ubuntu ntfsresize: Current volume size: 489807671808 bytes (489808 MB)
Apr 26 13:07:08 ubuntu ntfsresize: Current device size: 489807675392 bytes (489808 MB)
Apr 26 13:07:08 ubuntu ntfsresize: Checking filesystem consistency ...
Apr 26 13:07:08 ubuntu ntfsresize: Accounting clusters ...
Apr 26 13:07:08 ubuntu ntfsresize: Space in use       : 234161 MB (47.8%)
Apr 26 13:07:08 ubuntu ntfsresize: Collecting resizing constraints ...
Apr 26 13:07:08 ubuntu ntfsresize: You might resize at 234160492544 bytes or 234161 MB (freeing 255647 MB).
Apr 26 13:07:08 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Apr 26 13:07:08 ubuntu ubiquity: Backtrace has 7 calls on stack:
Apr 26 13:07:08 ubuntu ubiquity:   7: /lib/x86_64-linux-gnu/libparted.so.2(ped_assert+0x44) [0x7fb735c1b2e4]
Apr 26 13:07:08 ubuntu ubiquity:   6: /lib/x86_64-linux-gnu/libparted.so.2(+0x10e45) [0x7fb735c20e45]
Apr 26 13:07:08 ubuntu ubiquity:   5: parted_server() [0x40dee1]
Apr 26 13:07:08 ubuntu ubiquity:   4: parted_server() [0x40efc9]
Apr 26 13:07:08 ubuntu ubiquity:   3: parted_server() [0x402bf0]
Apr 26 13:07:08 ubuntu ubiquity:   2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0) [0x7fb735866a40]
Apr 26 13:07:08 ubuntu ubiquity:   1: parted_server() [0x402c19][/FONT]

Where the start of this log is the completion of the kernel modules compile and install, prior to this error box popping up on the user interface.  It is obviously the partition editor crashing on my setup.
A list of my disks from fdisk:

[FONT=system]ubuntu@ubuntu:~$ sudo fdisk -l /dev/sd[ab]

Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: AA202F53-006C-4C2D-9F68-0CA7F2B85E86

Device         Start        End   Sectors   Size Type
/dev/sda1       2048     821247    819200   400M Windows recovery environment
/dev/sda2     821248    1353727    532480   260M EFI System
/dev/sda3    1353728    1615871    262144   128M Microsoft reserved
/dev/sda4    1615872  958271487 956655616 456.2G Microsoft basic data
/dev/sda5  958271488 1000215215  41943728    20G Microsoft basic data

Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 35FB486A-FA2A-4E47-913D-D6216DED9291

Device         Start        End   Sectors   Size Type
/dev/sdb1  976762880 1953523711 976760832 465.8G Microsoft basic data[/FONT]


For the moment, I'm assuming that the stack backtrace and the error "message" in the popup box are somehow related, but I don't think I've got the know-how to join the two up. Anyone got any ideas how I can sidestep this crash and get to install Ubuntu on my computer?

---

### Post by David_Jolley on 2015-04-26
I have just used gparted to add an ext4 partition to /dev/sdb and retried the install.
It crashes now slighty differently, I get the same dialog box, but the stack trace in the syslog looks like:

[FONT=system]Apr 26 14:15:25 ubuntu ubiquity: Backtrace has 7 calls on stack:
Apr 26 14:15:25 ubuntu ubiquity:   7: /lib/x86_64-linux-gnu/libparted.so.2(ped_assert+0x44) [0x7f71bb9bf2e4]
Apr 26 14:15:25 ubuntu ubiquity:   6: /lib/x86_64-linux-gnu/libparted.so.2(+0x10e45) [0x7f71bb9c4e45]
Apr 26 14:15:25 ubuntu ubiquity:   5: parted_server() [0x40dee1]
Apr 26 14:15:25 ubuntu ubiquity:   4: parted_server() [0x40efc9]
Apr 26 14:15:25 ubuntu ubiquity:   3: parted_server() [0x402bf0]
Apr 26 14:15:25 ubuntu ubiquity:   2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0) [0x7f71bb60aa40]
Apr 26 14:15:25 ubuntu ubiquity:   1: parted_server() [0x402c19]
[/FONT]

Where the offsets are different in the libparted.so lines (7 and 6 in the trace).  
My disks now look like:
[FONT=system]ubuntu@ubuntu:~$ sudo fdisk -l /dev/sd[ab]

Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: AA202F53-006C-4C2D-9F68-0CA7F2B85E86

Device         Start        End   Sectors   Size Type
/dev/sda1       2048     821247    819200   400M Windows recovery environment
/dev/sda2     821248    1353727    532480   260M EFI System
/dev/sda3    1353728    1615871    262144   128M Microsoft reserved
/dev/sda4    1615872  958271487 956655616 456.2G Microsoft basic data
/dev/sda5  958271488 1000215215  41943728    20G Microsoft basic data

Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 35FB486A-FA2A-4E47-913D-D6216DED9291

Device         Start        End   Sectors   Size Type
/dev/sdb1       2048  976760831 976758784 465.8G Linux filesystem
/dev/sdb2  976762880 1953523711 976760832 465.8G Microsoft basic data
[/FONT]

Note that what was /dev/sdb1 before is now sdb2 and /dev/sdb1 is the new ext4 linux filesystem, explicitly created.

---

### Post by David_Jolley on 2015-04-26
Reading the manpage for ubiquity, I notice that it mentions a debugging mode, and that logs may be required.  I've started it from a terminal, using the -d option to enable debugging.  The same error condition was encountered,
Attached are the logs /var/log/installer/debug and /var/log/partman - but gzipped due to forum size constraints.

syslog ends the installer logging with the same crash, but with different offsets:

[FONT=system]Apr 26 14:45:47 ubuntu ntfsresize: Device name        : /dev/sda1
Apr 26 14:45:47 ubuntu ntfsresize: NTFS volume version: 3.1
Apr 26 14:45:47 ubuntu ntfsresize: Cluster size       : 4096 bytes
Apr 26 14:45:47 ubuntu ntfsresize: Current volume size: 419426816 bytes (420 MB)
Apr 26 14:45:47 ubuntu ntfsresize: Current device size: 419430400 bytes (420 MB)
Apr 26 14:45:47 ubuntu ntfsresize: Checking filesystem consistency ...
Apr 26 14:45:47 ubuntu ntfsresize: Accounting clusters ...
Apr 26 14:45:47 ubuntu ntfsresize: Space in use       : 291 MB (69.2%)
Apr 26 14:45:47 ubuntu ntfsresize: Collecting resizing constraints ...
Apr 26 14:45:47 ubuntu ntfsresize: You might resize at 290136064 bytes or 291 MB (freeing 129 MB).
Apr 26 14:45:47 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Apr 26 14:45:50 ubuntu ntfsresize: ntfsresize v2014.2.15AR.3 (libntfs-3g)
Apr 26 14:45:50 ubuntu ntfsresize: Device name        : /dev/sda4
Apr 26 14:45:50 ubuntu ntfsresize: NTFS volume version: 3.1
Apr 26 14:45:50 ubuntu ntfsresize: Cluster size       : 4096 bytes
Apr 26 14:45:50 ubuntu ntfsresize: Current volume size: 489807671808 bytes (489808 MB)
Apr 26 14:45:50 ubuntu ntfsresize: Current device size: 489807675392 bytes (489808 MB)
Apr 26 14:45:50 ubuntu ntfsresize: Checking filesystem consistency ...
Apr 26 14:45:50 ubuntu ntfsresize: Accounting clusters ...
Apr 26 14:45:50 ubuntu ntfsresize: Space in use       : 234256 MB (47.8%)
Apr 26 14:45:50 ubuntu ntfsresize: Collecting resizing constraints ...
Apr 26 14:45:50 ubuntu ntfsresize: You might resize at 234255577088 bytes or 234256 MB (freeing 255552 MB).
Apr 26 14:45:50 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Apr 26 14:45:50 ubuntu ubiquity: Backtrace has 7 calls on stack:
Apr 26 14:45:50 ubuntu ubiquity:   7: /lib/x86_64-linux-gnu/libparted.so.2(ped_assert+0x44) [0x7f5b4a6b22e4]
Apr 26 14:45:50 ubuntu ubiquity:   6: /lib/x86_64-linux-gnu/libparted.so.2(+0x10e45) [0x7f5b4a6b7e45]
Apr 26 14:45:50 ubuntu ubiquity:   5: parted_server() [0x40dee1]
Apr 26 14:45:50 ubuntu ubiquity:   4: parted_server() [0x40efc9]
Apr 26 14:45:50 ubuntu ubiquity:   3: parted_server() [0x402bf0]
Apr 26 14:45:50 ubuntu ubiquity:   2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0) [0x7f5b4a2fda40]
Apr 26 14:45:50 ubuntu ubiquity:   1: parted_server() [0x402c19]

[/FONT]

---

