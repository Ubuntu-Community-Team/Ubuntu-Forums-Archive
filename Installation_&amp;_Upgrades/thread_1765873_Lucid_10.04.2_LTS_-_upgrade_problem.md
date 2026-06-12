---
title: "Lucid 10.04.2 LTS - upgrade problem"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by akapotte on 2011-05-23
**The Setup:**
I have Ubuntu Lucid 10.04. LTS in a USB-stick.

The kernels which boots is: linux-image-2.6.32-26-generic

Below is the list of all kernels:
linux-generic
linux-image-2.6.32-24-generic
linux-image-2.6.32-25-generic
linux-image-2.6.32-26-generic
linux-image-2.6.32-30-generic

I have been booting the the System from the USB  int following machines: 
Dell laptop **Dell d420** and **Lenovo X201s**.

**What I want:**
I want to do the following
1 - To upgrade my system to run the latest kernel version
2 - To have a lean/light/thin system
NOTE:
Please have a look to the details below as well as the attached files. Your advice is very much appreciated.

**[COLOR="Red"]The Problem:[/COLOR]**
Some how the system does not behave right.

For example:
(1) My key combination does not work at all i.e. can neither flip the Desktop nor the Windows.

(2) When I tried to do "apt-get update, apt-get upgrade, apt-get dist-upgrade" only to find myself having a problem with two pckages i.e. **xinput** and **xkb-data**.

And when I tried to **reinstall** them I got error messages and when I tried to remove them I got errors.

**[COLOR="red"]Error Messages - Type A:[/COLOR]**
The errors below came when I was trying to **re-install** "xinput" and "xkb-data" packages.

(Reading database ... 10%dpkg: unrecoverable fatal error, aborting: failed in buffer_read(fd): files list for package `xinput': Input/output error

E: Sub-process /usr/bin/dpkg returned an error code (2)

dpkg: warning: files list file for package `xinput' missing, assuming package has no files currently installed

dpkg: warning: files list file for package `xbk-data' missing, assuming package has no files currently installed

**[COLOR="red"]Error Messages - Type B:[/COLOR]**
The error below came when I was trying to upgrade the system.
**Squashfs error:** Unable to read page, block, Unable to read fragment cache entry


**Space usage:**
See df and du outputs below

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  3.9G  3.4G  315M  92% /
none                  1.5G  364K  1.5G   1% /dev
/dev/sdb1             7.5G  4.7G  2.8G  63% /cdrom
/dev/loop0            651M  651M     0 100% /rofs
none                  1.5G  140K  1.5G   1% /dev/shm
tmpfs                 1.5G   16K  1.5G   1% /tmp
none                  1.5G  192K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda1             233G   82G  152G  36% /media/System

$ du -s * | sort -nr
19034   Downloads
3144    Documents
792     Softs
10      Profiles
10      Desktop
2       Videos
2       Templates
2       Public
2       Pictures
2       Music

**Attached files:**
Please see attached log file for more details - they came from the following sources:
$ ls -l /var/log
/var/log/syslog
/var/log/messages
/var/log/daemon.log
kernel_boot.txt

**See /var/log/Xorg.0.log output**
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

**See /var/log/kern.log output**
NOTE: I was not able to attach **/var/log/kern.log** output therefore I Copy & Paste here; I know - sorry.
Dec  6 06:08:07 ubuntu kernel: [25486.766156] nepomukservices[5734]: segfault at 2f ip 008e9ca8 sp bfadbae0 error 4 in libsoprano.so.4.3.0[8a4000+ef000]
Dec  6 06:08:14 ubuntu kernel: [25493.812188] nepomukservices[5749]: segfault at c ip 00c68ca8 sp bfaeea30 error 4 in libsoprano.so.4.3.0[c23000+ef000]
Dec  6 06:08:15 ubuntu kernel: [25494.539650] nepomukservices[5756]: segfault at 44 ip 09aa0ca8 sp bfa8b590 error 4 in libsoprano.so.4.3.0[9a5b000+ef000]
Dec  6 06:08:16 ubuntu kernel: [25495.586578] nepomukservices[5761]: segfault at 9 ip 00e7cca8 sp bf9c4220 error 4 in libsoprano.so.4.3.0[e37000+ef000]
Dec  6 06:08:17 ubuntu kernel: [25496.293041] nepomukservices[5768]: segfault at fffff3f0 ip 00b20cab sp bfa51b10 error 4 in libsoprano.so.4.3.0[adb000+ef000]
Dec  9 07:30:22 ubuntu kernel: [  470.296941] kwrited[4202]: segfault at 5 ip 00b138aa sp bfa84f6c error 4 in libc-2.11.1.so[aa8000+153000]
Dec 15 23:30:09 ubuntu kernel: [11221.918963] nepomukservices[4243]: segfault at 0 ip 049eecab sp bf9b71b0 error 4 in libsoprano.so.4.3.0[49a9000+ef000]
Dec 16 06:37:58 ubuntu kernel: [36891.098788] nepomukservices[5971]: segfault at 0 ip 00cdacab sp bf865030 error 4 in libsoprano.so.4.3.0[c95000+ef000]
Dec 16 06:38:00 ubuntu kernel: [36893.124966] nepomukservices[5980]: segfault at 38366933 ip 00b28ca8 sp bf9d2c00 error 4 in libsoprano.so.4.3.0[ae3000+ef000]
Dec 20 23:05:37 ubuntu kernel: [15274.636557] chromium-browse[7631]: segfault at 29ed40be ip 29ed40be sp 29ed40be error 4 in libflashplayer.so[38f39000+b2e000]
Dec 20 23:36:28 ubuntu kernel: [17125.063096] vlc[9281]: segfault at 4 ip 0963cdc6 sp bffd95a0 error 4 in libQtDBus.so.4.6.3[95fa000+77000]
Dec 21 00:25:24 ubuntu kernel: [20061.453620] vlc[9343]: segfault at 4 ip 08a54dc6 sp bff884e0 error 4 in libQtDBus.so.4.6.3[8a12000+77000]
Dec 25 22:51:07 ubuntu kernel: [82287.396296] nepomukservices[4717]: segfault at 9ce0822 ip 07b66cab sp bfdac480 error 4 in libsoprano.so.4.3.0[7b21000+ef000]
Dec 25 23:29:24 ubuntu kernel: [84583.497446] nepomukservices[4763]: segfault at 73650000 ip 005b4359 sp bffdd610 error 4 in libQtCore.so.4.6.3[553000+273000]
Dec 26 02:14:35 ubuntu kernel: [94495.109061] vlc[8834]: segfault at 4 ip 02af0dc6 sp bfc37a60 error 4 in libQtDBus.so.4.6.3[2aae000+77000]
Dec 26 11:55:14 ubuntu kernel: [129334.156796] vlc[9320]: segfault at 4 ip 019c0dc6 sp bf9d6e90 error 4 in libQtDBus.so.4.6.3[197e000+77000]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647497] SQUASHFS error: zlib_inflate error, data probably corrupt
Mar 23 22:06:15 ubuntu kernel: [ 4864.647509] SQUASHFS error: squashfs_read_data failed to read block 0x74ae7
Mar 23 22:06:15 ubuntu kernel: [ 4864.647514] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647519] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647529] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647533] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647542] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647546] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647555] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647559] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647568] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647572] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647581] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647585] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647593] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647598] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647606] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647610] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647618] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647623] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647631] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647635] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647648] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647652] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647660] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647664] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647673] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647677] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647686] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647690] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647698] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647702] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647711] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647715] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647723] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647728] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647736] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647740] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647749] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647753] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647761] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647766] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647774] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647778] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647787] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647791] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647800] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647804] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647812] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647817] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647829] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647833] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647841] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647846] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647854] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647858] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647866] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647871] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647879] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647884] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647892] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647896] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647905] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647909] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.647917] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.647921] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:15 ubuntu kernel: [ 4864.649709] SQUASHFS error: zlib_inflate error, data probably corrupt
Mar 23 22:06:15 ubuntu kernel: [ 4864.649715] SQUASHFS error: squashfs_read_data failed to read block 0x74ae7
Mar 23 22:06:15 ubuntu kernel: [ 4864.649720] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:15 ubuntu kernel: [ 4864.649725] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:17 ubuntu kernel: [ 4866.804970] SQUASHFS error: zlib_inflate error, data probably corrupt
Mar 23 22:06:17 ubuntu kernel: [ 4866.804980] SQUASHFS error: squashfs_read_data failed to read block 0x74ae7
Mar 23 22:06:17 ubuntu kernel: [ 4866.804986] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:17 ubuntu kernel: [ 4866.804990] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:06:17 ubuntu kernel: [ 4867.332437] SQUASHFS error: zlib_inflate error, data probably corrupt
Mar 23 22:06:17 ubuntu kernel: [ 4867.332447] SQUASHFS error: squashfs_read_data failed to read block 0x74ae7
Mar 23 22:06:17 ubuntu kernel: [ 4867.332453] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:06:17 ubuntu kernel: [ 4867.332457] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980155] SQUASHFS error: zlib_inflate error, data probably corrupt
Mar 23 22:11:13 ubuntu kernel: [ 5162.980168] SQUASHFS error: squashfs_read_data failed to read block 0x74ae7
Mar 23 22:11:13 ubuntu kernel: [ 5162.980175] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980180] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980194] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980198] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980208] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980212] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980221] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980225] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980234] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980238] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980247] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980251] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980260] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980264] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980273] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980277] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980286] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980291] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980299] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980304] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980312] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980317] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980330] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980334] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980343] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980348] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980356] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980360] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980369] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980373] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980382] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980386] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980395] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980399] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980408] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980412] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980421] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980425] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980433] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980438] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980446] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980450] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980459] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980463] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980472] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980476] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980485] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980489] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980498] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980502] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980514] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980519] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980528] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980532] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980540] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980544] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980553] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980558] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980566] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980570] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980579] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980583] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.980592] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.980596] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Mar 23 22:11:13 ubuntu kernel: [ 5162.982478] SQUASHFS error: zlib_inflate error, data probably corrupt
Mar 23 22:11:13 ubuntu kernel: [ 5162.982484] SQUASHFS error: squashfs_read_data failed to read block 0x74ae7
Mar 23 22:11:13 ubuntu kernel: [ 5162.982489] SQUASHFS error: Unable to read data cache entry [74ae7]
Mar 23 22:11:13 ubuntu kernel: [ 5162.982493] SQUASHFS error: Unable to read page, block 74ae7, size 26b2
Apr  1 02:56:40 ubuntu kernel: [  473.485659] SQUASHFS error: zlib_inflate error, data probably corrupt
Apr  1 02:56:40 ubuntu kernel: [  473.485669] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
Apr  1 02:56:40 ubuntu kernel: [  473.485674] SQUASHFS error: Unable to read fragment cache entry [190bfa]
Apr  1 02:56:40 ubuntu kernel: [  473.485679] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
Apr  1 02:56:40 ubuntu kernel: [  473.485686] SQUASHFS error: Unable to read fragment cache entry [190bfa]
Apr  1 02:56:40 ubuntu kernel: [  473.485691] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
Apr  1 02:56:40 ubuntu kernel: [  473.826247] SQUASHFS error: Unable to read fragment cache entry [190bfa]
Apr  1 02:56:40 ubuntu kernel: [  473.826256] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
Apr  1 02:56:41 ubuntu kernel: [  474.166121] SQUASHFS error: Unable to read fragment cache entry [190bfa]
Apr  1 02:56:41 ubuntu kernel: [  474.166130] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
Apr  1 02:56:41 ubuntu kernel: [  474.500404] SQUASHFS error: Unable to read fragment cache entry [190bfa]
Apr  1 02:56:41 ubuntu kernel: [  474.500414] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
Apr  1 02:56:41 ubuntu kernel: [  474.836072] SQUASHFS error: Unable to read fragment cache entry [190bfa]
Apr  1 02:56:41 ubuntu kernel: [  474.836081] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
Apr  1 02:56:42 ubuntu kernel: [  475.168097] SQUASHFS error: Unable to read fragment cache entry [190bfa]
Apr  1 02:56:42 ubuntu kernel: [  475.168106] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
Apr  1 02:56:42 ubuntu kernel: [  475.504972] SQUASHFS error: Unable to read fragment cache entry [190bfa]
Apr  1 02:56:42 ubuntu kernel: [  475.504981] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
Apr  1 02:56:42 ubuntu kernel: [  475.841034] SQUASHFS error: Unable to read fragment cache entry [190bfa]
Apr  1 02:56:42 ubuntu kernel: [  475.841043] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 00:31:10 ubuntu kernel: [19975.570178] SQUASHFS error: zlib_inflate error, data probably corrupt
May 14 00:31:10 ubuntu kernel: [19975.570190] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 14 00:31:10 ubuntu kernel: [19975.570197] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 00:31:10 ubuntu kernel: [19975.570203] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 00:31:10 ubuntu kernel: [19975.570213] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 00:31:10 ubuntu kernel: [19975.570219] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 00:39:03 ubuntu kernel: [20447.720738] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 00:39:03 ubuntu kernel: [20447.720744] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 01:24:02 ubuntu kernel: [23147.237117] vlc[9184]: segfault at 4 ip 005e3e26 sp bffeeee0 error 4 in libQtDBus.so.4.7.0[59f000+7a000]
May 14 15:11:28 ubuntu kernel: [10518.840495] SQUASHFS error: zlib_inflate error, data probably corrupt
May 14 15:11:28 ubuntu kernel: [10518.840519] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 14 15:11:28 ubuntu kernel: [10518.840522] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 15:11:28 ubuntu kernel: [10518.840525] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 15:11:28 ubuntu kernel: [10518.840538] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 15:11:28 ubuntu kernel: [10518.840542] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 16:08:54 ubuntu kernel: [13965.091067] SQUASHFS error: zlib_inflate error, data probably corrupt
May 14 16:08:54 ubuntu kernel: [13965.091080] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 14 16:08:54 ubuntu kernel: [13965.091087] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 16:08:54 ubuntu kernel: [13965.091093] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 16:08:54 ubuntu kernel: [13965.091104] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 16:08:54 ubuntu kernel: [13965.091110] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 16:08:54 ubuntu kernel: [13965.091121] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 16:08:54 ubuntu kernel: [13965.091127] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 16:08:54 ubuntu kernel: [13965.091136] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 16:08:54 ubuntu kernel: [13965.091141] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 16:08:54 ubuntu kernel: [13965.091151] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 16:08:54 ubuntu kernel: [13965.091156] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 16:27:09 ubuntu kernel: [15059.620609] SQUASHFS error: zlib_inflate error, data probably corrupt
May 14 16:27:09 ubuntu kernel: [15059.620615] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 14 16:27:09 ubuntu kernel: [15059.620619] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 16:27:09 ubuntu kernel: [15059.620622] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 16:27:09 ubuntu kernel: [15059.620627] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 16:27:09 ubuntu kernel: [15059.620630] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 16:30:52 ubuntu kernel: [15282.746985] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 16:30:52 ubuntu kernel: [15282.746990] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 17:26:01 ubuntu kernel: [18592.131377] SQUASHFS error: zlib_inflate error, data probably corrupt
May 14 17:26:01 ubuntu kernel: [18592.131382] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 14 17:26:01 ubuntu kernel: [18592.131385] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 17:26:01 ubuntu kernel: [18592.131387] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 17:32:21 ubuntu kernel: [18972.383932] SQUASHFS error: zlib_inflate error, data probably corrupt
May 14 17:32:21 ubuntu kernel: [18972.383937] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 14 17:32:21 ubuntu kernel: [18972.383940] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 17:32:21 ubuntu kernel: [18972.383942] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 18:28:05 ubuntu kernel: [22316.259546] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 18:28:05 ubuntu kernel: [22316.259551] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 18:32:49 ubuntu kernel: [22600.419374] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 18:32:49 ubuntu kernel: [22600.419379] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 18:52:26 ubuntu kernel: [23777.282340] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 18:52:26 ubuntu kernel: [23777.282345] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 18:52:38 ubuntu kernel: [23788.981456] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 18:52:38 ubuntu kernel: [23788.981460] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 18:56:21 ubuntu kernel: [24011.883201] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 18:56:21 ubuntu kernel: [24011.883206] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 19:23:47 ubuntu kernel: [25658.296315] SQUASHFS error: zlib_inflate error, data probably corrupt
May 14 19:23:47 ubuntu kernel: [25658.296321] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 14 19:23:47 ubuntu kernel: [25658.296324] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 19:23:47 ubuntu kernel: [25658.296326] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 19:39:50 ubuntu kernel: [26621.198793] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 19:39:50 ubuntu kernel: [26621.198798] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 19:41:22 ubuntu kernel: [26713.330099] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 19:41:22 ubuntu kernel: [26713.330103] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 20:59:18 ubuntu kernel: [31389.105808] SQUASHFS error: zlib_inflate error, data probably corrupt
May 14 20:59:18 ubuntu kernel: [31389.105813] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 14 20:59:18 ubuntu kernel: [31389.105816] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 20:59:18 ubuntu kernel: [31389.105818] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 21:04:30 ubuntu kernel: [31701.323090] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 21:04:30 ubuntu kernel: [31701.323095] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 21:48:53 ubuntu kernel: [34364.116176] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 21:48:53 ubuntu kernel: [34364.116181] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 21:52:50 ubuntu kernel: [34601.085560] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 21:52:50 ubuntu kernel: [34601.085565] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 21:57:01 ubuntu kernel: [34852.344574] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 21:57:01 ubuntu kernel: [34852.344579] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 22:23:03 ubuntu kernel: [36414.419217] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 22:23:03 ubuntu kernel: [36414.419222] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 23:02:13 ubuntu kernel: [38763.563216] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 23:02:13 ubuntu kernel: [38763.563221] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 23:28:44 ubuntu kernel: [40354.634752] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 23:28:44 ubuntu kernel: [40354.634758] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 23:29:31 ubuntu kernel: [40402.023619] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 23:29:31 ubuntu kernel: [40402.023624] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 23:38:23 ubuntu kernel: [40933.687407] SQUASHFS error: zlib_inflate error, data probably corrupt
May 14 23:38:23 ubuntu kernel: [40933.687412] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 14 23:38:23 ubuntu kernel: [40933.687415] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 23:38:23 ubuntu kernel: [40933.687417] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 23:57:11 ubuntu kernel: [  229.209054] SQUASHFS error: zlib_inflate error, data probably corrupt
May 14 23:57:11 ubuntu kernel: [  229.209059] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 14 23:57:11 ubuntu kernel: [  229.209062] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 23:57:11 ubuntu kernel: [  229.209065] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 14 23:57:11 ubuntu kernel: [  229.209069] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 14 23:57:11 ubuntu kernel: [  229.209071] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 15 21:13:55 ubuntu kernel: [ 5270.475610] vlc[5040]: segfault at 4 ip 0076fe26 sp bffafe60 error 4 in libQtDBus.so.4.7.0[72b000+7a000]
May 15 21:46:28 ubuntu kernel: [ 7223.877013] vlc[5985]: segfault at 4 ip 004cce26 sp bf8c8120 error 4 in libQtDBus.so.4.7.0[488000+7a000]
May 16 02:08:23 ubuntu kernel: [22938.242103] vlc[6015]: segfault at 4 ip 00639e26 sp bf941c10 error 4 in libQtDBus.so.4.7.0[5f5000+7a000]
May 16 22:54:37 ubuntu kernel: [ 1515.600380] SQUASHFS error: zlib_inflate error, data probably corrupt
May 16 22:54:37 ubuntu kernel: [ 1515.600386] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 16 22:54:37 ubuntu kernel: [ 1515.600389] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 16 22:54:37 ubuntu kernel: [ 1515.600391] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 16 22:54:37 ubuntu kernel: [ 1515.600395] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 16 22:54:37 ubuntu kernel: [ 1515.600398] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 16 22:56:03 ubuntu kernel: [ 1602.554455] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 16 22:56:03 ubuntu kernel: [ 1602.554463] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 16 22:57:41 ubuntu kernel: [ 1700.384133] SQUASHFS error: zlib_inflate error, data probably corrupt
May 16 22:57:41 ubuntu kernel: [ 1700.384139] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 16 22:57:41 ubuntu kernel: [ 1700.384142] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 16 22:57:41 ubuntu kernel: [ 1700.384145] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 21 21:14:28 ubuntu kernel: [41450.583811] SQUASHFS error: zlib_inflate error, data probably corrupt
May 21 21:14:28 ubuntu kernel: [41450.583818] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 21 21:14:28 ubuntu kernel: [41450.583822] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 21 21:14:28 ubuntu kernel: [41450.583825] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 21 21:14:28 ubuntu kernel: [41450.583830] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 21 21:14:28 ubuntu kernel: [41450.583832] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 21 21:16:21 ubuntu kernel: [41564.131181] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 21 21:16:21 ubuntu kernel: [41564.131185] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 21 21:24:26 ubuntu kernel: [42048.981751] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 21 21:24:26 ubuntu kernel: [42048.981756] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 22 00:11:47 ubuntu kernel: [52090.002919] SQUASHFS error: zlib_inflate error, data probably corrupt
May 22 00:11:47 ubuntu kernel: [52090.002964] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 22 00:11:47 ubuntu kernel: [52090.003008] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 22 00:11:47 ubuntu kernel: [52090.003049] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 22 00:14:55 ubuntu kernel: [52277.596150] SQUASHFS error: zlib_inflate error, data probably corrupt
May 22 00:14:55 ubuntu kernel: [52277.596992] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 22 00:14:55 ubuntu kernel: [52277.597825] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 22 00:14:55 ubuntu kernel: [52277.598640] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 22 00:17:48 ubuntu kernel: [52450.303932] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 22 00:17:48 ubuntu kernel: [52450.305448] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 22 00:21:36 ubuntu kernel: [52679.116149] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 22 00:21:36 ubuntu kernel: [52679.117662] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 22 00:43:22 ubuntu kernel: [53984.737444] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 22 00:43:22 ubuntu kernel: [53984.739015] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 22 00:44:12 ubuntu kernel: [54035.132573] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 22 00:44:12 ubuntu kernel: [54035.132577] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 22 00:45:14 ubuntu kernel: [54096.243985] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 22 00:45:14 ubuntu kernel: [54096.245304] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 22 00:59:22 ubuntu kernel: [54944.795289] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 22 00:59:22 ubuntu kernel: [54944.797281] SQUASHFS error: Unable to read page, block 190bfa, size 5d92
May 22 01:48:20 ubuntu kernel: [57882.452283] SQUASHFS error: zlib_inflate error, data probably corrupt
May 22 01:48:20 ubuntu kernel: [57882.452288] SQUASHFS error: squashfs_read_data failed to read block 0x190bfa
May 22 01:48:20 ubuntu kernel: [57882.452291] SQUASHFS error: Unable to read fragment cache entry [190bfa]
May 22 01:48:20 ubuntu kernel: [57882.452293] SQUASHFS error: Unable to read page, block 190bfa, size 5d92

---

