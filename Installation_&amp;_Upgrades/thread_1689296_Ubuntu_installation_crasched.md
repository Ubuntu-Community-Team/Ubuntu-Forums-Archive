---
title: "Ubuntu installation crasched"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by privi87 on 2011-02-16
Hi all!
I'm tring to install different versions of Ubuntu (10.10, 10.04 and 9.04) with usb key and cd but i have the same problem: installation crashes during creation of file system ext4!

These are my computer features:

Mother Board :   ASRock G41M-S
Chipset :   Intel G41
Processor :   Intel Pentium 4 530 @ 3000MHz
Ram :   1024MB (1 x 1024 DDR2-SDRAM )
Video :   RADEON X600 Series
Hard Disk :   Maxtor 6Y160M0 (160GB) (Windows XP installed)
Hard  Disk :   Western Digital WD2500JB-00REA0 (250GB) (where i tried to install Ubuntu)
CD-Rom Drive :   _NEC DVD_RW ND-3500AG
CD-Rom Drive :   SCSIVAX DVD/CD-ROM SCSI CdRom Device

Can you help me??

Thank you very much!

---

### Post by walle1357 on 2011-02-16
Could you please post a screenshot or explain in more detail what you mean by crashed? Thanks!

Who needs windoze in a life without walls?

---

### Post by privi87 on 2011-02-16
Thank you for you reply, i'm not english but i try to explain the problem better.
I start installation and set nickname (in lowercase) and password, after that i choose the hd, set clock, language of keyboard and finally click "Install"!
Now, installation start and tries to create 
file system ext4 for / into partition n° 1 of SCSI1 (0,0,0) (sda)...

at this time installation is blocked!

Sorry for my english, i hope you understand what i wanna say :-)

---

### Post by privi87 on 2011-02-16
I found this post [http://ubuntuforums.org/showthread.php?t=1526677](http://ubuntuforums.org/showthread.php?t=1526677), my problem is the same! 
Do you know what he meant?

---

### Post by privi87 on 2011-02-16
Update ;), this is my syslog:

```
Feb 16 20:22:53 ubuntu partman: Error running 'ntfsresize --info'
Feb 16 20:22:53 ubuntu ubiquity[4690]: switched to page partman
Feb 16 20:22:57 ubuntu ubiquity[4690]: switched to page partman
Feb 16 20:22:57 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Feb 16 20:22:57 ubuntu ntfsresize: Device name        : /dev/sdb1
Feb 16 20:22:57 ubuntu ntfsresize: NTFS volume version: 3.1
Feb 16 20:22:57 ubuntu ntfsresize: Cluster size       : 4096 bytes
Feb 16 20:22:57 ubuntu ntfsresize: Current volume size: 160006337024 bytes (160007 MB)
Feb 16 20:22:57 ubuntu ntfsresize: Current device size: 160006339584 bytes (160007 MB)
Feb 16 20:22:57 ubuntu ntfsresize: ERROR: This software has detected that the disk has at least 3 bad sectors.
Feb 16 20:22:57 ubuntu ntfsresize: ****************************************************************************
Feb 16 20:22:57 ubuntu ntfsresize: * WARNING: The disk has bad sector. This means physical damage on the disk *
Feb 16 20:22:57 ubuntu ntfsresize: * surface caused by deterioration, manufacturing faults or other reason.   *
Feb 16 20:22:57 ubuntu ntfsresize: * The reliability of the disk may stay stable or degrade fast. We suggest  *
Feb 16 20:22:57 ubuntu ntfsresize: * making a full backup urgently by running 'ntfsclone --rescue ...' then   *
Feb 16 20:22:57 ubuntu ntfsresize: * run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize  *
Feb 16 20:22:57 ubuntu ntfsresize: * NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
Feb 16 20:22:57 ubuntu ntfsresize: ****************************************************************************
Feb 16 20:22:57 ubuntu partman: Error running 'ntfsresize --info'
Feb 16 20:22:58 ubuntu kernel: [  129.846801] NTFS driver 2.1.29 [Flags: R/O MODULE].
Feb 16 20:22:58 ubuntu kernel: [  129.946158] QNX4 filesystem 0.2.3 registered.
Feb 16 20:22:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Feb 16 20:22:58 ubuntu 50mounted-tests: debug: /dev/sda1 type not recognised; skipping
Feb 16 20:22:58 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb 16 20:22:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Feb 16 20:22:58 ubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Feb 16 20:22:58 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb 16 20:22:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Feb 16 20:22:58 ubuntu 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Feb 16 20:22:58 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb 16 20:22:58 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb1
Feb 16 20:22:59 ubuntu ntfs-3g[7187]: Version 2010.8.8 external FUSE 28
Feb 16 20:22:59 ubuntu ntfs-3g[7187]: Mounted /dev/sdb1 (Read-Only, label "", NTFS 3.1)
Feb 16 20:22:59 ubuntu ntfs-3g[7187]: Cmdline options: ro
Feb 16 20:22:59 ubuntu ntfs-3g[7187]: Mount options: ro,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096
Feb 16 20:22:59 ubuntu ntfs-3g[7187]: Ownership and permissions disabled, configuration type 1
Feb 16 20:22:59 ubuntu 50mounted-tests: debug: mounted as ntfs-3g filesystem
Feb 16 20:22:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Feb 16 20:22:59 ubuntu 10freedos: debug: /dev/sdb1 is not a FAT partition: exiting
Feb 16 20:22:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Feb 16 20:22:59 ubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Feb 16 20:22:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Feb 16 20:22:59 ubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Feb 16 20:22:59 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Feb 16 20:22:59 ubuntu 20microsoft: debug: /dev/sdb1 is a NTFS partition
Feb 16 20:22:59 ubuntu 20microsoft: result: /dev/sdb1:Microsoft Windows XP Home Edition:Windows:chain
Feb 16 20:22:59 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Feb 16 20:22:59 ubuntu ntfs-3g[7187]: Unmounting /dev/sdb1 ()
Feb 16 20:22:59 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb 16 20:22:59 ubuntu ubiquity[4690]: switched to page partman
Feb 16 20:23:59 ubuntu ubiquity[4690]: switched to page partman
Feb 16 20:25:14 ubuntu ubiquity[4690]: last message repeated 3 times
Feb 16 20:26:14 ubuntu ubiquity[4690]: last message repeated 7 times
Feb 16 20:26:19 ubuntu ubiquity[4690]: debconffilter_done: ubi-partman (current: ubi-partman)
Feb 16 20:26:19 ubuntu ubiquity[4690]: Step_before = stepPartAdvanced
Feb 16 20:26:20 ubuntu kernel: [  332.219113] Adding 2929660k swap on /dev/sda5.  Priority:-1 extents:1 across:2929660k 
Feb 16 20:26:21 ubuntu partman: mke2fs 1.41.12 (17-May-2010)
Feb 16 20:26:21 ubuntu partman: warning: 256 blocks unused.
Feb 16 20:26:21 ubuntu partman: 
Feb 16 20:26:24 ubuntu clock-setup: Wed Feb 16 20:26:24 UTC 2011
Feb 16 20:26:24 ubuntu clock-setup: rdate: adjust local clock by -0.034224 seconds
Feb 16 20:26:25 ubuntu ubiquity[4690]: switched to page timezone
Feb 16 20:26:28 ubuntu localechooser: info: Locale has been preseeded to it_IT.UTF-8
Feb 16 20:26:28 ubuntu localechooser: info: Set localechooser/languagelist = 'it'
Feb 16 20:26:28 ubuntu localechooser: info: Set debian-installer/country = 'IT'
Feb 16 20:26:28 ubuntu localechooser: info: Set debian-installer/locale = 'it_IT.UTF-8'
Feb 16 20:26:28 ubuntu localechooser: info: Language = 'it'
Feb 16 20:26:28 ubuntu localechooser: info: line=it;1;IT;UTF-8;it_IT.UTF-8;;console-setup
Feb 16 20:26:28 ubuntu localechooser: info: Set debian-installer/language = 'it'
Feb 16 20:26:28 ubuntu localechooser: info: Set debian-installer/locale = 'it_IT.UTF-8'
Feb 16 20:26:28 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'it_IT.UTF-8'
Feb 16 20:26:28 ubuntu localechooser: info: Default country = 'IT'
Feb 16 20:26:28 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Feb 16 20:26:28 ubuntu localechooser: info: Set debian-installer/country = 'IT'
Feb 16 20:26:28 ubuntu localechooser: info: Set debian-installer/locale = 'it_IT.UTF-8'
Feb 16 20:26:28 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'it_IT.UTF-8'
Feb 16 20:26:28 ubuntu ubiquity[4690]: debconffilter_done: ubi-timezone (current: ubi-timezone)
Feb 16 20:26:28 ubuntu ubiquity[4690]: Step_before = stepLocation
Feb 16 20:26:28 ubuntu ubiquity[4690]: log-output -t ubiquity setxkbmap -layout it -option  -option lv3:ralt_switch
Feb 16 20:26:28 ubuntu ubiquity[4690]: switched to page console_setup
Feb 16 20:26:31 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Feb 16 20:26:31 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Feb 16 20:26:31 ubuntu ubiquity[4690]: log-output -t ubiquity setxkbmap -layout it -option 
Feb 16 20:26:31 ubuntu ubiquity[4690]: debconffilter_done: ubi-console-setup (current: ubi-console-setup)
Feb 16 20:26:31 ubuntu ubiquity[4690]: Step_before = stepKeyboardConf
Feb 16 20:26:31 ubuntu ubiquity[4690]: switched to page usersetup
Feb 16 20:26:39 ubuntu ubiquity[4690]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Feb 16 20:26:39 ubuntu ubiquity[4690]: Step_before = stepUserInfo
Feb 16 21:02:51 ubuntu kernel: [ 2523.300549] INFO: task flush-8:0:11856 blocked for more than 120 seconds.
Feb 16 21:02:51 ubuntu kernel: [ 2523.300555] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 16 21:02:51 ubuntu kernel: [ 2523.300559] flush-8:0     D dabedd5c     0 11856      2 0x00000000
Feb 16 21:02:51 ubuntu kernel: [ 2523.300566]  dabedd6c 00000046 00000002 dabedd5c dabedd44 c05d89e0 c08c3700 c08c3700
Feb 16 21:02:51 ubuntu kernel: [ 2523.300576]  6d1f1d5e 00000228 c08c3700 c08c3700 6d1c1c71 00000228 00000000 c08c3700
Feb 16 21:02:51 ubuntu kernel: [ 2523.300586]  c08c3700 ce690cb0 00000001 ce690cb0 c2108700 dabeddb8 dabedd7c c05c6e51
Feb 16 21:02:51 ubuntu kernel: [ 2523.300595] Call Trace:
Feb 16 21:02:51 ubuntu kernel: [ 2523.300608]  [<c05c6e51>] io_schedule+0x61/0xa0
Feb 16 21:02:51 ubuntu kernel: [ 2523.300614]  [<c01d9c4d>] sync_page+0x3d/0x50
Feb 16 21:02:51 ubuntu kernel: [ 2523.300619]  [<c05c74c7>] __wait_on_bit_lock+0x47/0x90
Feb 16 21:02:51 ubuntu kernel: [ 2523.300624]  [<c01d9c10>] ? sync_page+0x0/0x50
Feb 16 21:02:51 ubuntu kernel: [ 2523.300628]  [<c01d9bde>] __lock_page+0x7e/0x90
Feb 16 21:02:51 ubuntu kernel: [ 2523.300634]  [<c0165e60>] ? wake_bit_function+0x0/0x50
Feb 16 21:02:51 ubuntu kernel: [ 2523.300639]  [<c01e178f>] write_cache_pages+0x1ff/0x300
Feb 16 21:02:51 ubuntu kernel: [ 2523.300644]  [<c01e0750>] ? __writepage+0x0/0x40
Feb 16 21:02:51 ubuntu kernel: [ 2523.300651]  [<c02430b0>] ? blkdev_writepage+0x0/0x20
Feb 16 21:02:51 ubuntu kernel: [ 2523.300655]  [<c01e18b4>] generic_writepages+0x24/0x30
Feb 16 21:02:51 ubuntu kernel: [ 2523.300660]  [<c01e18dc>] do_writepages+0x1c/0x40
Feb 16 21:02:51 ubuntu kernel: [ 2523.300665]  [<c02364d8>] writeback_single_inode+0xb8/0x340
Feb 16 21:02:51 ubuntu kernel: [ 2523.300670]  [<c0236c99>] writeback_sb_inodes+0x149/0x230
Feb 16 21:02:51 ubuntu kernel: [ 2523.300675]  [<c02370fa>] writeback_inodes_wb+0x8a/0x160
Feb 16 21:02:51 ubuntu kernel: [ 2523.300680]  [<c02373bb>] wb_writeback+0x1eb/0x230
Feb 16 21:02:51 ubuntu kernel: [ 2523.300685]  [<c0237498>] ? wb_do_writeback+0x98/0x130
Feb 16 21:02:51 ubuntu kernel: [ 2523.300689]  [<c0237529>] wb_do_writeback+0x129/0x130
Feb 16 21:02:51 ubuntu kernel: [ 2523.300694]  [<c0237572>] bdi_writeback_task+0x42/0x110
Feb 16 21:02:51 ubuntu kernel: [ 2523.300700]  [<c01ee890>] ? bdi_start_fn+0x0/0xc0
Feb 16 21:02:51 ubuntu kernel: [ 2523.300705]  [<c01ee8ed>] bdi_start_fn+0x5d/0xc0
Feb 16 21:02:51 ubuntu kernel: [ 2523.300709]  [<c01ee890>] ? bdi_start_fn+0x0/0xc0
Feb 16 21:02:51 ubuntu kernel: [ 2523.300713]  [<c01659e4>] kthread+0x74/0x80
Feb 16 21:02:51 ubuntu kernel: [ 2523.300718]  [<c0165970>] ? kthread+0x0/0x80
Feb 16 21:02:51 ubuntu kernel: [ 2523.300723]  [<c010363e>] kernel_thread_helper+0x6/0x10
Feb 16 21:02:51 ubuntu kernel: [ 2523.300727] INFO: task mkfs.ext4:11931 blocked for more than 120 seconds.
Feb 16 21:02:51 ubuntu kernel: [ 2523.300730] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 16 21:02:51 ubuntu kernel: [ 2523.300733] mkfs.ext4     D 00000441     0 11931  11930 0x00000000
Feb 16 21:02:51 ubuntu kernel: [ 2523.300739]  ce4d1df8 00000086 f66540e0 00000441 f712a000 c023c496 c08c3700 c08c3700
Feb 16 21:02:51 ubuntu kernel: [ 2523.300749]  ab5e43f7 00000227 c08c3700 c08c3700 00000001 00000227 00000000 c08c3700
Feb 16 21:02:51 ubuntu kernel: [ 2523.300758]  c08c3700 ce693f70 01845000 ce693f70 c2108700 ce4d1e40 ce4d1e08 c05c6e51
Feb 16 21:02:51 ubuntu kernel: [ 2523.300767] Call Trace:
Feb 16 21:02:51 ubuntu kernel: [ 2523.300773]  [<c023c496>] ? submit_bh+0x106/0x130
Feb 16 21:02:51 ubuntu kernel: [ 2523.300778]  [<c05c6e51>] io_schedule+0x61/0xa0
Feb 16 21:02:51 ubuntu kernel: [ 2523.300782]  [<c01d9c4d>] sync_page+0x3d/0x50
Feb 16 21:02:51 ubuntu kernel: [ 2523.300787]  [<c05c761d>] __wait_on_bit+0x4d/0x70
Feb 16 21:02:51 ubuntu kernel: [ 2523.300791]  [<c01d9c10>] ? sync_page+0x0/0x50
Feb 16 21:02:51 ubuntu kernel: [ 2523.300795]  [<c01d9e71>] wait_on_page_bit+0x91/0xa0
Feb 16 21:02:51 ubuntu kernel: [ 2523.300800]  [<c0165e60>] ? wake_bit_function+0x0/0x50
Feb 16 21:02:51 ubuntu kernel: [ 2523.300805]  [<c01e16b2>] write_cache_pages+0x122/0x300
Feb 16 21:02:51 ubuntu kernel: [ 2523.300810]  [<c01e0750>] ? __writepage+0x0/0x40
Feb 16 21:02:51 ubuntu kernel: [ 2523.300815]  [<c02430b0>] ? blkdev_writepage+0x0/0x20
Feb 16 21:02:51 ubuntu kernel: [ 2523.300820]  [<c01e18b4>] generic_writepages+0x24/0x30
Feb 16 21:02:51 ubuntu kernel: [ 2523.300824]  [<c01e18dc>] do_writepages+0x1c/0x40
Feb 16 21:02:51 ubuntu kernel: [ 2523.300828]  [<c01da33e>] __filemap_fdatawrite_range+0x5e/0x70
Feb 16 21:02:51 ubuntu kernel: [ 2523.300833]  [<c01da3a7>] filemap_write_and_wait_range+0x57/0x80
Feb 16 21:02:51 ubuntu kernel: [ 2523.300839]  [<c023aad4>] vfs_fsync_range+0x54/0x80
Feb 16 21:02:51 ubuntu kernel: [ 2523.300843]  [<c023aba7>] vfs_fsync+0x27/0x30
Feb 16 21:02:51 ubuntu kernel: [ 2523.300848]  [<c023abdf>] do_fsync+0x2f/0x50
Feb 16 21:02:51 ubuntu kernel: [ 2523.300852]  [<c023ac32>] sys_fsync+0x12/0x20
Feb 16 21:02:51 ubuntu kernel: [ 2523.300857]  [<c05c90a4>] syscall_call+0x7/0xb
Feb 16 21:04:36 ubuntu kernel: [ 2627.949513] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Feb 16 21:04:37 ubuntu ubiquity[4690]: debconffilter_done: ubiquity.components.partman_commit (current: None)
Feb 16 21:04:38 ubuntu python: keeping packages due to preseeding: icedtea6-plugin openoffice.org
Feb 16 21:04:38 ubuntu python: keeping language packs for: en it
Feb 16 21:04:43 ubuntu ubiquity: /usr/lib/python2.6/dist-packages/apt/deprecation.py:96: UserWarning: Deprecated parameter 'autoFix'
Feb 16 21:04:43 ubuntu ubiquity:   warnings.warn("Deprecated parameter %r" % key)
Feb 16 21:17:01 ubuntu CRON[13257]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

Do you know how can i fix the problem??

---

