---
title: "Kernel 2.6.28-7"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2009-02-07
For adventures and bleeding edge "nuts"..  ;)

The meta package is **_NOT_** out


This is a **_big one_** and also 2.6.29 patches.

[https://lists.ubuntu.com/archives/jaunty-changes/2009-February/004434.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-February/004434.html)


> linux (2.6.28-7.18) jaunty; urgency=low

  [ Alok Kataria ]

  * SAUCE: (drop after 2.6.29) x86: add a synthetic TSC_RELIABLE feature
    bit
    - LP: #319945
  * SAUCE: (drop after 2.6.29) x86: add X86_FEATURE_HYPERVISOR feature bit
    - LP: #319945
  * SAUCE: (drop after 2.6.29) x86: Hypervisor detection and get tsc_freq
    from hypervisor
    - LP: #319945
  * SAUCE: (drop after 2.6.29) x86: Add a synthetic TSC_RELIABLE feature
    bit.
    - LP: #319945
  * SAUCE: (drop after 2.6.29) x86: Skip verification by the watchdog for
    TSC clocksource.
    - LP: #319945
  * SAUCE: (drop after 2.6.29) x86: VMware: Fix vmware_get_tsc code
    - LP: #319945
  * SAUCE: (drop after 2.6.29) x86: vmware: look for DMI string in the
    product serial key
    - LP: #319945

  [ Andy Whitcroft ]

  * SAUCE: toshiba_acpi -- pull in current -dev version of driver
    - LP: #269831
  * SAUCE: toshiba_acpi -- add acpi hotkey kernel thread
    - LP: #269831
  * move toshiba laptops back from tlsup to toshiba_acpi
    - LP: #269831

  [ Aneesh Kumar K.V ]

  * SAUCE: (revert before 2.6.28.y update) ext4: Fix the delalloc
    writepages to allocate blocks at the right offset.
  * SAUCE: (revert before 2.6.28.y update) ext4: avoid ext4_error when
    mounting a fs with a single bg
  * SAUCE: (revert before 2.6.28.y update) ext4: Don't overwrite
    allocation_context ac_status
  * SAUCE: (revert before 2.6.28.y update) ext4: Add blocks added during
    resize to bitmap
  * SAUCE: (revert before 2.6.28.y update) ext4: Use
    EXT4_GROUP_INFO_NEED_INIT_BIT during resize
  * SAUCE: (revert before 2.6.28.y update) ext4: cleanup mballoc header
    files
  * SAUCE: (revert before 2.6.28.y update) ext4: don't use blocks freed but
    not yet committed in buddy cache init
  * SAUCE: (revert before 2.6.28.y update) ext4: Fix race between
    read_block_bitmap() and mark_diskspace_used()
  * SAUCE: (revert before 2.6.28.y update) ext4: Fix the race between
    read_inode_bitmap() and ext4_new_inode()
  * SAUCE: (revert before 2.6.28.y update) ext4: Use new buffer_head flag
    to check uninit group bitmaps initialization
  * SAUCE: (revert before 2.6.28.y update) ext4: mark the blocks/inode
    bitmap beyond end of group as used
  * SAUCE: (revert before 2.6.28.y update) ext4: Don't allow new groups to
    be added during block allocation
  * SAUCE: (revert before 2.6.28.y update) ext4: Init the complete page
    while building buddy cache
  * SAUCE: (revert before 2.6.28.y update) ext4: Fix s_dirty_blocks_counter
    if block allocation failed with nodelalloc

  [ Hannes Eder ]

  * SAUCE: (drop after 2.6.29) x86: vmware - fix sparse warnings
    - LP: #319945

  [ Luke Yelavich ]

  * hid modules have hyphens instead of underscores in their names

  [ Mark Fasheh ]

  * SAUCE: (revert before 2.6.28.y update) jbd2: Add BH_JBDPrivateStart

  [ Theodore Ts'o ]

  * SAUCE: (revert before 2.6.28.y update) ext4: Add support for non-native
    signed/unsigned htree hash algorithms
  * SAUCE: (revert before 2.6.28.y update) ext4: tone down
    ext4_da_writepages warnings
  * SAUCE: (revert before 2.6.28.y update) jbd2: Add barrier not supported
    test to journal_wait_on_commit_record
  * SAUCE: (revert before 2.6.28.y update) ext4: Add sanity checks for the
    superblock before mounting the filesystem
  * SAUCE: (revert before 2.6.28.y update) ext4: only use i_size_high for
    regular files
  * SAUCE: (revert before 2.6.28.y update) ext4: Add sanity check to
    make_indexed_dir
  * SAUCE: (revert before 2.6.28.y update) jbd2: On a __journal_expect()
    assertion failure printk "JBD2", not "EXT3-fs"
  * SAUCE: (revert before 2.6.28.y update) ext4: Initialize the new group
    descriptor when resizing the filesystem

  [ Tyler Hicks ]

  * SAUCE: (drop after 2.6.28) [eCryptfs] Regression in unencrypted
    filename symlinks
    - LP: #322532

  [ Upstream Kernel Changes ]

  * Input: atkbd - broaden the Dell DMI signatures
    - LP: #261721
  * ti_usb_3410_5052: support alternate firmware
  * ath5k: fix mesh point operation
  * mac80211: decrement ref count to netdev after launching mesh discovery
  * inotify: clean up inotify_read and fix locking problems
  * fuse: destroy bdi on umount
  * fuse: fix missing fput on error
  * fuse: fix NULL deref in fuse_file_alloc()
  * x86, mm: fix pte_free()
  * klist.c: bit 0 in pointer can't be used as flag
  * sysfs: fix problems with binary files
  * x86: fix page attribute corruption with cpa()
  * USB: fix toggle mismatch in disable_endpoint paths
  * sound: virtuoso: enable UART on Xonar HDAV1.3
  * USB: usbmon: Implement compat_ioctl
  * USB: fix char-device disconnect handling
  * USB: storage: add unusual devs entry
  * alpha: nautilus - fix compile failure with gcc-4.3
  * alpha: fix vmalloc breakage
  * resources: skip sanity check of busy resources
  * rtl8187: Add termination packet to prevent stall
  * it821x: Add ultra_mask quirk for Vortex86SX
  * libata: pata_via: support VX855, future chips whose IDE controller use
    0x0571
  * serial_8250: support for Sealevel Systems Model 7803 COMM+8
  * drm: stash AGP include under the do-we-have-AGP ifdef
  * Fix OOPS in mmap_region() when merging adjacent VM_LOCKED file segments
  * bnx2x: Block nvram access when the device is inactive
  * ext3: Add sanity check to make_indexed_dir
  * rtl8187: Fix error in setting OFDM power settings for RTL8187L
  * epoll: drop max_user_instances and rely only on max_user_watches
  * gpiolib: fix request related issue
  * sgi-xpc: Remove NULL pointer dereference.
  * sgi-xpc: ensure flags are updated before bte_copy
  * include/linux: Add bsg.h to the Kernel exported headers
  * ALSA: hda - Fix PCM reference NID for STAC/IDT analog outputs
  * ALSA: hda - add another MacBook Pro 4, 1 subsystem ID
  * ALSA: hda - Add quirk for HP DV6700 laptop
  * crypto: authenc - Fix zero-length IV crash
  * crypto: ccm - Fix handling of null assoc data
  * x86, pat: fix reserve_memtype() for legacy 1MB range
  * x86, pat: fix PTE corruption issue while mapping RAM using /dev/mem
  * PCI hotplug: fix lock imbalance in pciehp
  * dmaengine: fix dependency chaining
  * NET: net_namespace, fix lock imbalance
  * relay: fix lock imbalance in relay_late_setup_files
  * Linux 2.6.28.3
  * ALSA: Enable SPDIF output on ALC655
  * ALSA: hda - Add ASUS V1Sn support
  * ALSA: hda - support detecting HD Audio devices with PCI class code
  * ALSA: hda: alc883 model for ASUS P5Q-EM boards
  * ALSA: hda - Add quirk for MSI 7260 mobo
  * ALSA: hda - Add quirk for Sony VAIO VGN-SR19XN
  * ALSA: oxygen: add Claro halo support
  * ALSA: hda - Add a new function to seek for a codec ID
  * ALSA: patch_sigmatel: Add missing Gateway entries and autodetection
  * ALSA: hda - More fixes on Gateway entries
  * ALSA: hda - Add MCP67 HDMI support
  * ALSA: hda - fix name for ALC1200
  * LSA: hda - Add HP Acacia detection
  * ALSA: hda - Add quirk for HP 2230s
  * ALSA: hda - Add quirk for Dell Inspiron Mini9
  * ALSA: hda - add support for Intel DX58SO board
  * ALSA: hda - Fix silent headphone output on Panasonic CF-74
  * ALSA: USB quirk for Logitech Quickcam Pro 9000 name
  * ALSA: hda - add quirks for some 82801H variants to use ALC883_MITAC

  [ Yasunori Goto ]

  * SAUCE: (revert before 2.6.28.y update) ext4: Widen type of
    ext4_sb_info.s_mb_maxs[]

Date: Mon, 02 Feb 2009 23:07:13 -0700
Changed-By: Tim Gardner <tim.gardner at canonical.com>
Maintainer: Ubuntu Kernel Team <kernel-team at lists.ubuntu.com>
[https://launchpad.net/ubuntu/jaunty/+source/linux/2.6.28-7.18](https://launchpad.net/ubuntu/jaunty/+source/linux/2.6.28-7.18)
-------------- next part --------------
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

Format: 1.8
Date: Mon, 02 Feb 2009 23:07:13 -0700
Source: linux
Binary: linux-source-2.6.28 linux-doc-2.6.28 linux-headers-2.6.28-7 linux-libc-dev linux-image-2.6.28-7-generic linux-headers-2.6.28-7-generic linux-image-debug-2.6.28-7-generic linux-image-2.6.28-7-iop32x linux-headers-2.6.28-7-iop32x linux-image-debug-2.6.28-7-iop32x linux-image-2.6.28-7-ixp4xx linux-headers-2.6.28-7-ixp4xx linux-image-debug-2.6.28-7-ixp4xx linux-image-2.6.28-7-orion5x linux-headers-2.6.28-7-orion5x linux-image-debug-2.6.28-7-orion5x linux-image-2.6.28-7-server linux-headers-2.6.28-7-server linux-image-debug-2.6.28-7-server linux-image-2.6.28-7-versatile linux-headers-2.6.28-7-versatile linux-image-debug-2.6.28-7-versatile linux-image-2.6.28-7-virtual
Architecture: source
Version: 2.6.28-7.18
Distribution: jaunty
Urgency: low
Maintainer: Ubuntu Kernel Team <kernel-team at lists.ubuntu.com>
Changed-By: Tim Gardner <tim.gardner at canonical.com>
Description: 
 linux-doc-2.6.28 - Linux kernel specific documentation for version 2.6.28
 linux-headers-2.6.28-7 - Header files related to Linux kernel version 2.6.28
 linux-headers-2.6.28-7-generic - Linux kernel headers for version 2.6.28 on x86/x86_64
 linux-headers-2.6.28-7-iop32x - Linux kernel headers for version 2.6.28 on IOP32x-based systems
 linux-headers-2.6.28-7-ixp4xx - Linux kernel headers for version 2.6.28 on IXP4xx-based systems
 linux-headers-2.6.28-7-orion5x - Linux kernel headers for version 2.6.28 on Orion5x-based systems
 linux-headers-2.6.28-7-server - Linux kernel headers for version 2.6.28 on x86/x86_64
 linux-headers-2.6.28-7-versatile - Linux kernel headers for version 2.6.28 on Versatile-based system
 linux-image-2.6.28-7-generic - Linux kernel image for version 2.6.28 on x86/x86_64
 linux-image-2.6.28-7-iop32x - Linux kernel image for version 2.6.28 on IOP32x-based systems
 linux-image-2.6.28-7-ixp4xx - Linux kernel image for version 2.6.28 on IXP4xx-based systems
 linux-image-2.6.28-7-orion5x - Linux kernel image for version 2.6.28 on Orion5x-based systems
 linux-image-2.6.28-7-server - Linux kernel image for version 2.6.28 on x86/x86_64
 linux-image-2.6.28-7-versatile - Linux kernel image for version 2.6.28 on Versatile-based systems
 linux-image-2.6.28-7-virtual - Linux kernel image for version 2.6.28 on x86/x86_64
 linux-image-debug-2.6.28-7-generic - Linux kernel debug image for version 2.6.28 on x86/x86_64
 linux-image-debug-2.6.28-7-iop32x - Linux kernel debug image for version 2.6.28 on IOP32x-based syste
 linux-image-debug-2.6.28-7-ixp4xx - Linux kernel debug image for version 2.6.28 on IXP4xx-based syste
 linux-image-debug-2.6.28-7-orion5x - Linux kernel debug image for version 2.6.28 on Orion5x-based syst
 linux-image-debug-2.6.28-7-server - Linux kernel debug image for version 2.6.28 on x86/x86_64
 linux-image-debug-2.6.28-7-versatile - Linux kernel debug image for version 2.6.28 on Versatile-based sy
 linux-libc-dev - Linux Kernel Headers for development
 linux-source-2.6.28 - Linux kernel source for version 2.6.28 with Ubuntu patches
Launchpad-Bugs-Fixed: 261721 269831 269831 269831 319945 319945 319945 319945 319945 319945 319945 319945 322532
Changes: 
 linux (2.6.28-7.18) jaunty; urgency=low
 .
   [ Alok Kataria ]
 .
   * SAUCE: (drop after 2.6.29) x86: add a synthetic TSC_RELIABLE feature
     bit
     - LP: #319945
   * SAUCE: (drop after 2.6.29) x86: add X86_FEATURE_HYPERVISOR feature bit
     - LP: #319945
   * SAUCE: (drop after 2.6.29) x86: Hypervisor detection and get tsc_freq
     from hypervisor
     - LP: #319945
   * SAUCE: (drop after 2.6.29) x86: Add a synthetic TSC_RELIABLE feature
     bit.
     - LP: #319945
   * SAUCE: (drop after 2.6.29) x86: Skip verification by the watchdog for
     TSC clocksource.
     - LP: #319945
   * SAUCE: (drop after 2.6.29) x86: VMware: Fix vmware_get_tsc code
     - LP: #319945
   * SAUCE: (drop after 2.6.29) x86: vmware: look for DMI string in the
     product serial key
     - LP: #319945
 .
   [ Andy Whitcroft ]
 .
   * SAUCE: toshiba_acpi -- pull in current -dev version of driver
     - LP: #269831
   * SAUCE: toshiba_acpi -- add acpi hotkey kernel thread
     - LP: #269831
   * move toshiba laptops back from tlsup to toshiba_acpi
     - LP: #269831
 .
   [ Aneesh Kumar K.V ]
 .
   * SAUCE: (revert before 2.6.28.y update) ext4: Fix the delalloc
     writepages to allocate blocks at the right offset.
   * SAUCE: (revert before 2.6.28.y update) ext4: avoid ext4_error when
     mounting a fs with a single bg
   * SAUCE: (revert before 2.6.28.y update) ext4: Don't overwrite
     allocation_context ac_status
   * SAUCE: (revert before 2.6.28.y update) ext4: Add blocks added during
     resize to bitmap
   * SAUCE: (revert before 2.6.28.y update) ext4: Use
     EXT4_GROUP_INFO_NEED_INIT_BIT during resize
   * SAUCE: (revert before 2.6.28.y update) ext4: cleanup mballoc header
     files
   * SAUCE: (revert before 2.6.28.y update) ext4: don't use blocks freed but
     not yet committed in buddy cache init
   * SAUCE: (revert before 2.6.28.y update) ext4: Fix race between
     read_block_bitmap() and mark_diskspace_used()
   * SAUCE: (revert before 2.6.28.y update) ext4: Fix the race between
     read_inode_bitmap() and ext4_new_inode()
   * SAUCE: (revert before 2.6.28.y update) ext4: Use new buffer_head flag
     to check uninit group bitmaps initialization
   * SAUCE: (revert before 2.6.28.y update) ext4: mark the blocks/inode
     bitmap beyond end of group as used
   * SAUCE: (revert before 2.6.28.y update) ext4: Don't allow new groups to
     be added during block allocation
   * SAUCE: (revert before 2.6.28.y update) ext4: Init the complete page
     while building buddy cache
   * SAUCE: (revert before 2.6.28.y update) ext4: Fix s_dirty_blocks_counter
     if block allocation failed with nodelalloc
 .
   [ Hannes Eder ]
 .
   * SAUCE: (drop after 2.6.29) x86: vmware - fix sparse warnings
     - LP: #319945
 .
   [ Luke Yelavich ]
 .
   * hid modules have hyphens instead of underscores in their names
 .
   [ Mark Fasheh ]
 .
   * SAUCE: (revert before 2.6.28.y update) jbd2: Add BH_JBDPrivateStart
 .
   [ Theodore Ts'o ]
 .
   * SAUCE: (revert before 2.6.28.y update) ext4: Add support for non-native
     signed/unsigned htree hash algorithms
   * SAUCE: (revert before 2.6.28.y update) ext4: tone down
     ext4_da_writepages warnings
   * SAUCE: (revert before 2.6.28.y update) jbd2: Add barrier not supported
     test to journal_wait_on_commit_record
   * SAUCE: (revert before 2.6.28.y update) ext4: Add sanity checks for the
     superblock before mounting the filesystem
   * SAUCE: (revert before 2.6.28.y update) ext4: only use i_size_high for
     regular files
   * SAUCE: (revert before 2.6.28.y update) ext4: Add sanity check to
     make_indexed_dir
   * SAUCE: (revert before 2.6.28.y update) jbd2: On a __journal_expect()
     assertion failure printk "JBD2", not "EXT3-fs"
   * SAUCE: (revert before 2.6.28.y update) ext4: Initialize the new group
     descriptor when resizing the filesystem
 .
   [ Tyler Hicks ]
 .
   * SAUCE: (drop after 2.6.28) [eCryptfs] Regression in unencrypted
     filename symlinks
     - LP: #322532
 .
   [ Upstream Kernel Changes ]
 .
   * Input: atkbd - broaden the Dell DMI signatures
     - LP: #261721
   * ti_usb_3410_5052: support alternate firmware
   * ath5k: fix mesh point operation
   * mac80211: decrement ref count to netdev after launching mesh discovery
   * inotify: clean up inotify_read and fix locking problems
   * fuse: destroy bdi on umount
   * fuse: fix missing fput on error
   * fuse: fix NULL deref in fuse_file_alloc()
   * x86, mm: fix pte_free()
   * klist.c: bit 0 in pointer can't be used as flag
   * sysfs: fix problems with binary files
   * x86: fix page attribute corruption with cpa()
   * USB: fix toggle mismatch in disable_endpoint paths
   * sound: virtuoso: enable UART on Xonar HDAV1.3
   * USB: usbmon: Implement compat_ioctl
   * USB: fix char-device disconnect handling
   * USB: storage: add unusual devs entry
   * alpha: nautilus - fix compile failure with gcc-4.3
   * alpha: fix vmalloc breakage
   * resources: skip sanity check of busy resources
   * rtl8187: Add termination packet to prevent stall
   * it821x: Add ultra_mask quirk for Vortex86SX
   * libata: pata_via: support VX855, future chips whose IDE controller use
     0x0571
   * serial_8250: support for Sealevel Systems Model 7803 COMM+8
   * drm: stash AGP include under the do-we-have-AGP ifdef
   * Fix OOPS in mmap_region() when merging adjacent VM_LOCKED file segments
   * bnx2x: Block nvram access when the device is inactive
   * ext3: Add sanity check to make_indexed_dir
   * rtl8187: Fix error in setting OFDM power settings for RTL8187L
   * epoll: drop max_user_instances and rely only on max_user_watches
   * gpiolib: fix request related issue
   * sgi-xpc: Remove NULL pointer dereference.
   * sgi-xpc: ensure flags are updated before bte_copy
   * include/linux: Add bsg.h to the Kernel exported headers
   * ALSA: hda - Fix PCM reference NID for STAC/IDT analog outputs
   * ALSA: hda - add another MacBook Pro 4, 1 subsystem ID
   * ALSA: hda - Add quirk for HP DV6700 laptop
   * crypto: authenc - Fix zero-length IV crash
   * crypto: ccm - Fix handling of null assoc data
   * x86, pat: fix reserve_memtype() for legacy 1MB range
   * x86, pat: fix PTE corruption issue while mapping RAM using /dev/mem
   * PCI hotplug: fix lock imbalance in pciehp
   * dmaengine: fix dependency chaining
   * NET: net_namespace, fix lock imbalance
   * relay: fix lock imbalance in relay_late_setup_files
   * Linux 2.6.28.3
   * ALSA: Enable SPDIF output on ALC655
   * ALSA: hda - Add ASUS V1Sn support
   * ALSA: hda - support detecting HD Audio devices with PCI class code
   * ALSA: hda: alc883 model for ASUS P5Q-EM boards
   * ALSA: hda - Add quirk for MSI 7260 mobo
   * ALSA: hda - Add quirk for Sony VAIO VGN-SR19XN
   * ALSA: oxygen: add Claro halo support
   * ALSA: hda - Add a new function to seek for a codec ID
   * ALSA: patch_sigmatel: Add missing Gateway entries and autodetection
   * ALSA: hda - More fixes on Gateway entries
   * ALSA: hda - Add MCP67 HDMI support
   * ALSA: hda - fix name for ALC1200
   * LSA: hda - Add HP Acacia detection
   * ALSA: hda - Add quirk for HP 2230s
   * ALSA: hda - Add quirk for Dell Inspiron Mini9
   * ALSA: hda - add support for Intel DX58SO board
   * ALSA: hda - Fix silent headphone output on Panasonic CF-74
   * ALSA: USB quirk for Logitech Quickcam Pro 9000 name
   * ALSA: hda - add quirks for some 82801H variants to use ALC883_MITAC
 .
   [ Yasunori Goto ]
 .
   * SAUCE: (revert before 2.6.28.y update) ext4: Widen type of
     ext4_sb_info.s_mb_maxs[]


---

### Post by jfernyhough on 2009-02-07
Any idea how this compares to 29-rc3?

I've been having issues with Liferea and its database (similar to the old Firefox fsync bug) on my laptop and ext4 with 28-6 and 29-rc3, have to try rebooting with 28-7 and see if it helps. Didn't happen before (or on another install with ext3).

---

### Post by plun on 2009-02-07
No idea...;)

You have several fixes from the "guru" Theodore Tso about Ext4

I am also running Ff3.2 and totally refuses 3.06...:D


The Debian way with old junk....  :p

---

### Post by jfernyhough on 2009-02-07
Ack, same thing with 28-7 - lots of hard disk thrashing. Might be time to open a bug for Liferea...

---

### Post by plun on 2009-02-07
> **jfernyhough said:**
> Ack, same thing with 28-7 - lots of hard disk thrashing. Might be time to open a bug for Liferea...

Ok..... a news aggregator..:confused::confused:


I cannot see any difference between 2.6.28-7 and 2.6.29-RC3

Both just works, how do you see the trashing  ???

---

### Post by jfernyhough on 2009-02-07
Whenever I update feeds or change the status of an item (e.g. mark it as read) Liferea updates its database. It appears to do a lot of disk activity for each item (creates liferea.db-journal, updates liferea.db, deletes journal, as far as I can tell), so an Update All... takes a long time and creates a lot of disk activity. This is a little odd as it used to work perfectly (and still does on a USB install of Jaunty using ext3, and a USB install of Jaunty using ext4). The only thing that's different on this install is I haven't removed tracker (and I installed and tried KDE4.2, still have konquerer installed) and it's a new hard drive (400GB SATA WD Blue). It even does this with a clean ~/.liferea_1.4 .

---

### Post by plun on 2009-02-07
> **jfernyhough said:**
> Whenever I update feeds or change the status of an item (e.g. mark it as read) Liferea updates its database. It appears to do a lot of disk activity for each item (creates liferea.db-journal, updates liferea.db, deletes journal, as far as I can tell), so an Update All... takes a long time and creates a lot of disk activity. This is a little odd as it used to work perfectly (and still does on a USB install of Jaunty using ext3, and a USB install of Jaunty using ext4). The only thing that's different on this install is I haven't removed tracker (and I installed and tried KDE4.2, still have konquerer installed) and it's a new hard drive (400GB SATA WD Blue). It even does this with a clean ~/.liferea_1.4 .

OK.. this one is difficult.

One starter is what database Liferea is using..I am lazy and doesnt check.

It might be a good idea to also file abug against Liferea upstream.


Running 2.8.28-7 for the moment and everything is "rock solid".

---

### Post by MacUntu on 2009-02-07
Bleeding edge nuts are running at least 2.6.29-rc3 (which runs fine by the way ;)).

---

### Post by plun on 2009-02-07
> **MacUntu said:**
> Bleeding edge nuts are running at least 2.6.29-rc3 (which runs fine by the way ;)).

Of course.... but this "nuts" is testing Ubuntus latest nuts kernel...:D

I don't know when a meta package arrive....

---

### Post by ronacc on 2009-02-07
up and running fine here except for the non-kernel thing about compiz and xorg pi**ng on each other :D

---

### Post by plun on 2009-02-07
> **ronacc said:**
>  compiz and xorg pi**ng on each other :D

Well..... I am running the Metacity cr-p.... :D


(another infraction but this is stupid)

---

### Post by ronacc on 2009-02-07
on reboots I just alt>F2 to term, kill compiz.real then alt>F7 and re start compiz with fusion-icon , a bit of a pain but it works .

---

### Post by plun on 2009-02-07
> **ronacc said:**
> on reboots I just alt>F2 to term, kill compiz.real then alt>F7 and re start compiz with fusion-icon , a bit of a pain but it works .

Yup... but I killed my compiz.real binary...running the real Compiz script.

Nevertheless the kernel works..;)

---

### Post by Nullack on 2009-02-08
I wish the kernel team would keep consistently using upstream revision tags in their dam GIT log entries

---

