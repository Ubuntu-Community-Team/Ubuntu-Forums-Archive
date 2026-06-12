---
title: "Dist-upgrade 8.04 LTS--64 to 10.04 LTS--64 failed"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by kingneutron on 2010-05-06
[FONT="Courier New"][SIZE="1"]--Began with an up-to-date Ubuntu 8.04.3--64 LTS install; tar-copied everything from sda2 to sda3 and booted SDA3 so I wouldn't fry my main install:

[[ ' fdisk -l /dev/sda /dev/sdb '

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86dae77a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2491    20008926    7  HPFS/NTFS
/dev/sda2            2492        3355     6940080   83  Linux
/dev/sda3            3356        4219     6940080   83  Linux
/dev/sda4            4220       38913   278679555    5  Extended
/dev/sda5            4220       38913   278679523+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2685095

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         864     6940048+  83  Linux
/dev/sdb2             865        1728     6940080   83  Linux
/dev/sdb3            1729       38913   298688512+   5  Extended
/dev/sdb5            1729        1853     1004031   82  Linux swap / Solaris
/dev/sdb6            1854        6717    39070048+   b  W95 FAT32
/dev/sdb7            6718        7963    10008463+  83  Linux
/dev/sdb8            7964        8997     8305573+   b  W95 FAT32
/dev/sdb9            8998       12767    30282493+   7  HPFS/NTFS
/dev/sdb10          12768       38913   210017713+  83  Linux
]]

--I booted OK into SDA3 and began the upgrade process from there.  Home is on SDB7 ( Notes attached )

( NOTE I am using Reiserfs as root filesystem, not ext4 ) - and still booting from Super Grub Disk CD to 8.04's GRUB 0.97-29ubuntu21.2 )

--I was constantly running into disk-space issues for the dist-upgrade, so moved /var/cache/apt to SDB3 to "git 'er done."

--I manually edited /etc/fstab and /boot/grub/menu.lst for the new volume IDs and kernel filenames.

--After dist-upgrade finished and rebooting, getting error message after FSCK: 

" INIT: ureadahead-other main process (9999) terminated with status 4 "

- Substitute 9999 with various PID numbers - error comes up about 8-10x and boot process hangs, no login prompt.

-- Will attach any logs requested; but I'm about to scrap the failed install and start over, 'cuz I want to test 10.04 LTS and the new Vmware Workstation 7.1--64 beta.  The only thing I can think of is that I did not boot into the new kernel ( apt-get upgrade ) before doing the dist-upgrade.

--I've done a few of these dist-upgrades in the past this way; 6.06-LTS to 8.04, 8.04 to 9.x, etc

--Any help is appreciated, TIA
[/SIZE][/FONT]

---

### Post by kingneutron on 2010-05-06
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677)

--Seems to apply

---

### Post by kingneutron on 2010-05-06
LSPCI results attached:

---

### Post by kingneutron on 2010-05-07
--Late-breaking update:

--After several hours of head-beating, I figured out the kernel programmers ( or udev people ) F'd us again -- the ' fdisk -l ' order is DIFFERENT from 8.04.

--Long story short, I have a mix of (1) IDE drive and the rest SATA.  10.04 decided to move the IDE to SDA, where it was **dead last** ( reliably ) in 8.04.

- Got 10.04 booting OK now after changing LABEL in fstab and Grub menu.lst to UUID

-- Graphics are still problematic; I can't use the Nvidia binary driver (either one) without getting screen corruption on text terminals, and MY STATIC IP SETTINGS (that were CLEARLY defined in /etc/network/interfaces ) WERE DESTROYED on upgrade -- this is HORRIBLE BEHAVIOR FOR A SUPPOSED " STABLE RELEASE!! "

--I've got pretty much everything up and runnning now, including Vmware Workstation Beta - but it was a HUGE pain in the ***, and most people I know wouldn't put up with it.

--This release needs quite a bit of work before I can recommend it to my friends -- dist-upgrade from 8.04 was *anything* but " seamless. "

---

