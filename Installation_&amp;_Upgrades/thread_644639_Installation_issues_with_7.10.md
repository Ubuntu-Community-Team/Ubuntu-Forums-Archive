---
title: "Installation issues with 7.10"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by joachi on 2007-12-19
I have been trying to install Ubuntu 7.10 for the past few months but have no success.  This is on a Dell Dimension 4100 with the following CPU:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 6
cpu MHz         : 996.826
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat p
se36 mmx fxsr sse up
bogomips        : 1994.77
clflush size    : 32

I am able to boot from the Live CD and play with it. But as soon as I boot from it and try to do a clean install it freezes while downloading and installing either the server kernel or the desktop kernel. I cannot upgrade my current system because it has a broken 7.04 install. I get constant firefox crashes and other application misbehaviour.  I have crash reports in my /var/crash which I don't know how to debug:
_usr_lib_firefox_firefox-bin.1000.crash  _usr_share_apport_apport.0.crash

---

### Post by overdrank on 2007-12-19
HI and have you tried the alternate cd
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)
It is a text based installation and you can install on top of you existing partition.

---

### Post by Pumalite on 2007-12-19
How much memory do you have?

---

### Post by joachi on 2007-12-20
512 Meg of RAM. The Dell Dimension 4100 cannot take more than that. I think this is the issue. The problem seems to be that when it starts installing the kernel it runs out of memory. So, the status bar stays on at 83% for a while. I also checked the system log on <Ctl><alt><F4>. It complained about unable to install the kernel and then drops out.

---

### Post by Pumalite on 2007-12-20
Get a Live CD and make a 500 MB of /swap partition ahead of time, Then try again.

---

### Post by joachi on 2007-12-20
So every time I install i redo my partitions. I have 1 Gig swap partition while I am installing. This is why I am a bit concerned as to why this is not working. My current partition table on the first disk looks like this:
/dev/sda1               1        1094     8787523+  83  Linux
/dev/sda2            1095        1216      979965   82  Linux swap / Solaris

---

### Post by Pumalite on 2007-12-20
Go Manual and follow this scheme:
10 GB for '/'
1 GB for /swap
The rest for /home
Then press 'Follow'

---

### Post by joachi on 2007-12-20
I do go manual. I have two drives and I create the following partitions:
/dev/sda1               1        1094     8787523+  83  Linux ==> /
/dev/sda2            1095        1216      979965   82  Linux swap / Solaris ==> swap
/dev/sdb1               1        1246    10008494+  83  Linux ==> home
/dev/sdb2            1247        2462     9767520   83  Linux ==> /usr
/dev/sdb3            2463        4865    19302097+   5  Extended 
/dev/sdb5            2463        3435     7815591   83  Linux
/dev/sdb6            3436        4865    11486443+  83  Linux

... etc. before I start the install. I infact leave only the /home unformatted. All other partitions are formatted for the install.

---

### Post by Pumalite on 2007-12-20
Follow my suggestion in the drive of your choice.

---

### Post by joachi on 2007-12-21
Will try this today.... Stay tuned. By the way thanks for your help.

---

### Post by Pumalite on 2007-12-21
Good luck!

---

### Post by joachi on 2007-12-22
It looks like I am kind of low on this luck thing :)

So here is the latest on the saga of my installation with 7.10 Gutsy Gibbon.

Partitioned and re-partitioned about 6 times with all different sizes. The final drive map is as follows:
/dev/sda1 /home 10 Gig.
/dev/sdb1 / 20 GB
/dev/sdb2 swap 2 GB
/dev/sdbn /usr/local

I get the following in the log:
Dec 22 14:59:50 syslogd started: BusyBox v1.1.3
Dec 22 14:59:50 kernel: klogd started: BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7)
Dec 22 14:59:50 kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ub
untu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Dec 22 14:59:50 kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 22 14:59:50 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 22 14:59:50 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 22 14:59:50 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 22 14:59:50 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffc0000 (usable)
Dec 22 14:59:50 kernel: [    0.000000]  BIOS-e820: 000000001ffc0000 - 000000001fff8000 (ACPI data)
Dec 22 14:59:50 kernel: [    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
Dec 22 14:59:50 kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Dec 22 14:59:50 kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Dec 22 14:59:50 kernel: [    0.000000] 0MB HIGHMEM available.
Dec 22 14:59:50 kernel: [    0.000000] 511MB LOWMEM available.
Dec 22 14:59:50 kernel: [    0.000000] Entering add_active_range(0, 0, 131008) 0 entries of 256 used
Dec 22 14:59:50 kernel: [    0.000000] Zone PFN ranges:
Dec 22 14:59:50 kernel: [    0.000000]   DMA             0 ->     4096
Dec 22 14:59:50 kernel: [    0.000000]   Normal       4096 ->   131008
Dec 22 14:59:50 kernel: [    0.000000]   HighMem    131008 ->   131008
Dec 22 14:59:50 kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 22 14:59:50 kernel: [    0.000000]     0:        0 ->   131008
Dec 22 14:59:50 kernel: [    0.000000] On node 0 totalpages: 131008
Dec 22 14:59:50 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 22 14:59:50 kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 22 14:59:50 kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Dec 22 14:59:50 kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Dec 22 14:59:50 kernel: [    0.000000]   Normal zone: 125921 pages, LIFO batch:31
Dec 22 14:59:50 kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Dec 22 14:59:50 kernel: [    0.000000] DMI 2.3 present.
Dec 22 14:59:50 kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FF980 checksum 0
Dec 22 14:59:50 kernel: [    0.000000] ACPI: RSDP 000FF980, 0014 (r0 AMI   )
Dec 22 14:59:50 kernel: [    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 DELL   ZUUL     20001128 MSFT     1011)
Dec 22 14:59:50 kernel: [    0.000000] ACPI: FACP 1FFF1000, 0074 (r1 DELL   ZUUL     20001128 MSFT     1011)
Dec 22 14:59:50 kernel: [    0.000000] ACPI: DSDT 1FFE0000, 2DEB (r1 D815EA EA81510A       12 MSFT  100000B)
Dec 22 14:59:50 kernel: [    0.000000] ACPI: FACS 1FFF8000, 0040
Dec 22 14:59:50 kernel: [    0.000000] ACPI: BOOT 1FFF4000, 002B (r1 DELL   ZUUL     20001128 MSFT     1011)
Dec 22 14:59:50 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Dec 22 14:59:50 kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb80000)
Dec 22 14:59:50 kernel: [    0.000000] Built 1 zonelists.  Total pages: 129985
Dec 22 14:59:50 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed init
rd=/install/initrd.gz quiet --
Dec 22 14:59:50 kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Dec 22 14:59:50 kernel: [    0.000000] mapped APIC to ffffd000 (0140d000)
Dec 22 14:59:50 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 22 14:59:50 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 22 14:59:50 kernel: [    0.000000] Initializing CPU#0
Dec 22 14:59:50 kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Dec 22 14:59:50 kernel: [    0.000000] Detected 996.801 MHz processor.
Dec 22 14:59:50 kernel: [   43.173816] Console: colour VGA+ 80x25
Dec 22 14:59:50 kernel: [   43.174624] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 22 14:59:50 kernel: [   43.175678] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 22 14:59:50 kernel: [   43.218094] Memory: 510220k/524032k available (2015k kernel code, 13320k reserved, 916k data, 364k init,
 0k highmem)
Dec 22 14:59:50 kernel: [   43.218117] virtual kernel memory layout:
Dec 22 14:59:50 kernel: [   43.218119]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Dec 22 14:59:50 kernel: [   43.218122]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 22 14:59:50 kernel: [   43.218125]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Dec 22 14:59:50 kernel: [   43.218128]     lowmem  : 0xc0000000 - 0xdffc0000   ( 511 MB)
Dec 22 14:59:50 kernel: [   43.218131]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Dec 22 14:59:50 kernel: [   43.218134]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
<snip>
Dec 22 15:00:13 debconf: BLURB7
Dec 22 15:00:13 debconf: BLURB8
Dec 22 15:00:13 debconf: BLURB5
Dec 22 15:00:13 debconf: BLURB6
Dec 22 15:00:13 debconf: BLURB7
Dec 22 15:00:14 debconf: BLURB8
Dec 22 15:00:14 debconf: BLURB5
Dec 22 15:00:14 debconf: BLURB6
Dec 22 15:00:14 debconf: BLURB9
Dec 22 15:00:14 debconf: return us
Dec 22 15:00:15 main-menu[3188]: (process:3801): md5sum:  
Dec 22 15:00:15 main-menu[3188]: (process:3801): /etc/console-setup/boottime.kmap.gz 
Dec 22 15:00:15 main-menu[3188]: (process:3801): : No such file or directory 
Dec 22 15:00:15 main-menu[3188]: DEBUG: resolver (libc6): package doesn't exist (ignored) 
Dec 22 15:00:15 main-menu[3188]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec 22 15:00:15 main-menu[3188]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 15:00:15 main-menu[3188]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 15:00:15 main-menu[3188]: INFO: Menu item 'cdrom-detect' selected 
Dec 22 15:00:16 net/hw-detect.hotplug: Detected hotpluggable network interface lo
Dec 22 15:00:18 hw-detect: Detected module 'trm290' for 'IDE chipset support'
Dec 22 15:00:18 hw-detect: insmod /lib/modules/2.6.22-14-generic/kernel/drivers/ide/pci/trm290.ko 
Dec 22 15:00:18 hw-detect: Detected module 'sc1200' for 'IDE chipset support'
Dec 22 15:00:18 hw-detect: insmod /lib/modules/2.6.22-14-generic/kernel/drivers/ide/pci/sc1200.ko 
Dec 22 15:00:18 hw-detect: Detected module 'via82cxxx' for 'IDE chipset support'
Dec 22 15:00:19 hw-detect: insmod /lib/modules/2.6.22-14-generic/kernel/drivers/ide/pci/via82cxxx.ko 
Dec 22 15:00:19 hw-detect: Detected module 'opti621' for 'IDE chipset support'
Dec 22 15:00:19 hw-detect: insmod /lib/modules/2.6.22-14-generic/kernel/drivers/ide/pci/opti621.ko 
Dec 22 15:00:19 hw-detect: Detected module 'ns87415' for 'IDE chipset support'
Dec 22 15:00:19 hw-detect: insmod /lib/modules/2.6.22-14-generic/kernel/drivers/ide/pci/ns87415.ko 
Dec 22 15:00:19 hw-detect: Detected module 'hpt366' for 'IDE chipset support'
<snip>
Dec 22 15:09:50 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb5
Dec 22 15:09:50 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb5
Dec 22 15:09:50 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb5
Dec 22 15:09:50 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb5
Dec 22 15:09:50 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb5
Dec 22 15:09:52 main-menu[3188]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec 22 15:09:52 main-menu[3188]: DEBUG: resolver (efi-modules): package doesn't exist (ignored) 
Dec 22 15:09:52 main-menu[3188]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 15:09:52 main-menu[3188]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 15:09:52 main-menu[3188]: INFO: Menu item 'user-setup-udeb' selected 
Dec 22 15:10:02 main-menu[3188]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec 22 15:10:02 main-menu[3188]: DEBUG: resolver (efi-modules): package doesn't exist (ignored) 
Dec 22 15:10:02 main-menu[3188]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 15:10:02 main-menu[3188]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 15:10:02 main-menu[3188]: INFO: Menu item 'base-installer' selected 
Dec 22 15:10:04 apt-install: Queueing package console-setup for later installation
Dec 22 15:11:00 debootstrap: Selecting previously deselected package base-files.
Dec 22 15:11:00 debootstrap: (Reading database ... 0 files and directories currently installed.)
Dec 22 15:11:00 debootstrap: Unpacking base-files (from .../base-files_4.0.0ubuntu5_i386.deb) ...
Dec 22 15:11:00 debootstrap: Selecting previously deselected package base-passwd.
Dec 22 15:11:00 debootstrap: Unpacking base-passwd (from .../base-passwd_3.5.11build1_i386.deb) ...
Dec 22 15:11:00 debootstrap: dpkg: base-passwd: dependency problems, but configuring anyway as you request:
Dec 22 15:11:00 debootstrap:  base-passwd depends on libc6 (>= 2.6); however:
Dec 22 15:11:00 debootstrap:   Package libc6 is not installed.
Dec 22 15:11:00 debootstrap: Setting up base-passwd (3.5.11build1) ...
Dec 22 15:11:00 debootstrap: 
Dec 22 15:11:00 debootstrap: dpkg: base-files: dependency problems, but configuring anyway as you request:
Dec 22 15:11:00 debootstrap:  base-files depends on awk; however:
Dec 22 15:11:00 debootstrap:   Package awk is not installed.
Dec 22 15:11:00 debootstrap:  base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
Dec 22 15:11:00 debootstrap:   Package libpam-modules is not installed.
Dec 22 15:11:00 debootstrap: Setting up base-files (4.0.0ubuntu5) ...
Dec 22 15:11:01 debootstrap: 
Dec 22 15:11:02 debootstrap: dpkg: regarding .../dpkg_1.14.5ubuntu16_i386.deb containing dpkg, pre-dependency problem:
Dec 22 15:11:02 debootstrap:  dpkg pre-depends on libc6 (>= 2.6-1)
Dec 22 15:11:02 debootstrap: dpkg: warning - ignoring pre-dependency problem !
Dec 22 15:11:02 debootstrap: dpkg: regarding .../dpkg_1.14.5ubuntu16_i386.deb containing dpkg, pre-dependency problem:
Dec 22 15:11:02 debootstrap:  dpkg pre-depends on coreutils (>= 5.93-1)
Dec 22 15:11:02 debootstrap: dpkg: warning - ignoring pre-dependency problem !
Dec 22 15:11:02 debootstrap: (Reading database ... 
Dec 22 15:11:02 debootstrap: 91 files and directories currently installed.)
Dec 22 15:11:02 debootstrap: Preparing to replace dpkg 1.14.5ubuntu16 (using .../dpkg_1.14.5ubuntu16_i386.deb)
<snip>
Dec 22 15:11:27 debootstrap: Unpacking replacement base-files ...
Dec 22 15:11:27 debootstrap: Preparing to replace base-passwd 3.5.11build1 (using .../base-passwd_3.5.11build1_i386.deb) ...
Dec 22 15:11:27 debootstrap: Unpacking replacement base-passwd ...
Dec 22 15:11:27 debootstrap: Selecting previously deselected package bash.
Dec 22 15:11:27 debootstrap: dpkg: regarding .../bash_3.2-0ubuntu11_i386.deb containing bash, pre-dependency problem:
Dec 22 15:11:27 debootstrap:  bash pre-depends on libncurses5 (>= 5.6)
Dec 22 15:11:27 debootstrap: dpkg: warning - ignoring pre-dependency problem !
Dec 22 15:11:27 debootstrap: Unpacking bash (from .../bash_3.2-0ubuntu11_i386.deb) ...
Dec 22 15:11:27 debootstrap: Selecting previously deselected package belocs-locales-bin.
Dec 22 15:11:27 debootstrap: Unpacking belocs-locales-bin (from .../belocs-locales-bin_2.4-2.2ubuntu5_i386.deb) ...
Dec 22 15:11:28 debootstrap: Selecting previously deselected package coreutils.
Dec 22 15:11:28 debootstrap: dpkg: regarding .../coreutils_5.97-5.3ubuntu3_i386.deb containing coreutils, pre-dependency problem:
Dec 22 15:11:28 debootstrap:  coreutils pre-depends on libacl1 (>= 2.2.11-1)
Dec 22 15:11:28 debootstrap:   libacl1 is unpacked, but has never been configured.
Dec 22 15:11:28 debootstrap: dpkg: warning - ignoring pre-dependency problem !
Dec 22 15:11:28 debootstrap: dpkg: regarding .../coreutils_5.97-5.3ubuntu3_i386.deb containing coreutils, pre-dependency problem:
Dec 22 15:11:28 debootstrap:  coreutils pre-depends on libselinux1 (>= 2.0.15)
Dec 22 15:11:28 debootstrap: dpkg: warning - ignoring pre-dependency problem !
Dec 22 15:11:28 debootstrap: Unpacking coreutils (from .../coreutils_5.97-5.3ubuntu3_i386.deb) ...
Dec 22 15:11:28 debootstrap: Use of uninitialized value in string eq at /usr/sbin/dpkg-divert line 224.
Dec 22 15:11:28 debootstrap: Use of uninitialized value in length at /usr/sbin/dpkg-divert line 224.
Dec 22 15:11:28 debootstrap: Use of uninitialized value in length at /usr/sbin/dpkg-divert line 224.
Dec 22 15:11:28 debootstrap: Use of uninitialized value in length at /usr/sbin/dpkg-divert line 224.
Dec 22 15:11:28 debootstrap: No diversion `any diversion of /usr/share/man/man1/md5sum.textutils.1.gz', none removed
Dec 22 15:11:28 debootstrap: Use of uninitialized value in string eq at /usr/sbin/dpkg-divert line 224.
Dec 22 15:11:28 debootstrap: Use of uninitialized value in length at /usr/sbin/dpkg-divert line 224.
Dec 22 15:11:28 debootstrap: Use of uninitialized value in length at /usr/sbin/dpkg-divert line 224.
Dec 22 15:11:28 debootstrap: Use of uninitialized value in length at /usr/sbin/dpkg-divert line 224.
Dec 22 15:11:28 debootstrap: No diversion `any diversion of /usr/bin/md5sum.textutils', none removed
Dec 22 15:11:29 debootstrap: Selecting previously deselected package dash.
Dec 22 15:11:29 debootstrap: Unpacking dash (from .../dash_0.5.4-1ubuntu3_i386.deb) ...
Dec 22 15:11:29 debootstrap: Selecting previously deselected package libdb4.5.
Dec 22 15:11:29 debootstrap: Unpacking libdb4.5 (from .../libdb4.5_4.5.20-5ubuntu3_i386.deb) ...
Dec 22 15:11:29 debootstrap: Selecting previously deselected package debconf-i18n.
Dec 22 15:11:29 debootstrap: Unpacking debconf-i18n (from .../debconf-i18n_1.5.14ubuntu1_all.deb) ...
Dec 22 15:11:29 debootstrap: Preparing to replace debconf 1.5.14ubuntu1 (using .../debconf_1.5.14ubuntu1_all.deb) ...
Dec 22 15:11:29 debootstrap: Unpacking replacement debconf ...
Dec 22 15:11:29 debootstrap: Selecting previously deselected package debianutils.
Dec 22 15:11:29 debootstrap: Unpacking debianutils (from .../debianutils_2.22.1_i386.deb) ...
Dec 22 15:11:29 debootstrap: Selecting previously deselected package libdevmapper1.02.1.
Dec 22 15:11:29 debootstrap: Unpacking libdevmapper1.02.1 (from .../libdevmapper1.02.1_2%3a1.02.20-1ubuntu4_i386.deb) ...
Dec 22 15:11:29 debootstrap: Selecting previously deselected package diff.
Dec 22 15:11:29 debootstrap: Unpacking diff (from .../diff_2.8.1-12ubuntu1_i386.deb) ...
Dec 22 15:11:29 debootstrap: dpkg: regarding .../dpkg_1.14.5ubuntu16_i386.deb containing dpkg, pre-dependency problem:
<snip>
Dec 22 15:13:21 apt-install:   linux-ubuntu-modules-2.6.22-14-server
Dec 22 15:13:21 apt-install: Suggested packages:
Dec 22 15:13:21 apt-install:   fdutils linux-doc-2.6.22 linux-source-2.6.22
Dec 22 15:13:21 apt-install: Recommended packages:
Dec 22 15:13:21 apt-install:   lilo grub
Dec 22 15:13:21 apt-install: The following NEW packages will be installed:
Dec 22 15:13:21 apt-install:   linux-image-2.6.22-14-server linux-image-server linux-server
Dec 22 15:13:21 apt-install:   linux-ubuntu-modules-2.6.22-14-server
Dec 22 15:13:27 apt-install: 0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Dec 22 15:13:27 apt-install: Need to get 0B/21.7MB of archives.
Dec 22 15:13:27 apt-install: After unpacking 73.8MB of additional disk space will be used.
Dec 22 15:13:28 apt-install: Selecting previously deselected package linux-image-2.6.22-14-server.
Dec 22 15:13:28 apt-install: (Reading database ... 10316 files and directories currently installed.)
Dec 22 15:13:28 apt-install: Unpacking linux-image-2.6.22-14-server (from .../linux-image-2.6.22-14-server_2.6.22-14.46_i386.deb) ...
Dec 22 15:13:29 apt-install: Done.
Dec 22 15:14:00 apt-install: Selecting previously deselected package linux-ubuntu-modules-2.6.22-14-server.
Dec 22 15:14:00 apt-install: Unpacking linux-ubuntu-modules-2.6.22-14-server (from .../linux-ubuntu-modules-2.6.22-14-server_2.6.22-14.
37_i386.deb) ...
Dec 22 15:14:05 apt-install: Selecting previously deselected package linux-image-server.
Dec 22 15:14:05 apt-install: Unpacking linux-image-server (from .../linux-image-server_2.6.22.14.21_i386.deb) ...
Dec 22 15:14:06 apt-install: Selecting previously deselected package linux-server.
Dec 22 15:14:06 apt-install: Unpacking linux-server (from .../linux-server_2.6.22.14.21_i386.deb) ...
Dec 22 15:14:06 apt-install: Setting up linux-image-2.6.22-14-server (2.6.22-14.46) ...
Dec 22 15:14:06 apt-install: Running depmod.
Dec 22 15:14:09 apt-install: Failed to run depmod
Dec 22 15:14:09 apt-install: dpkg: error processing linux-image-2.6.22-14-server (--configure):
Dec 22 15:14:09 apt-install:  subprocess post-installation script returned error exit status 1
Dec 22 15:14:09 apt-install: dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-server:
Dec 22 15:14:09 apt-install:  linux-ubuntu-modules-2.6.22-14-server depends on linux-image-2.6.22-14-server; however:
Dec 22 15:14:09 apt-install:   Package linux-image-2.6.22-14-server is not configured yet.
Dec 22 15:14:09 apt-install: dpkg: error processing linux-ubuntu-modules-2.6.22-14-server (--configure):
Dec 22 15:14:09 apt-install:  dependency problems - leaving unconfigured
Dec 22 15:14:09 apt-install: dpkg: dependency problems prevent configuration of linux-image-server:
Dec 22 15:14:09 apt-install:  linux-image-server depends on linux-image-2.6.22-14-server; however:
Dec 22 15:14:09 apt-install:   Package linux-image-2.6.22-14-server is not configured yet.
Dec 22 15:14:09 apt-install:  linux-image-server depends on linux-ubuntu-modules-2.6.22-14-server; however:
Dec 22 15:14:09 apt-install:   Package linux-ubuntu-modules-2.6.22-14-server is not configured yet.
Dec 22 15:14:09 apt-install: dpkg: error processing linux-image-server (--configure):
Dec 22 15:14:09 apt-install:  dependency problems - leaving unconfigured
Dec 22 15:14:09 apt-install: dpkg: dependency problems prevent configuration of linu
Dec 22 15:14:09 apt-install: x-server:
Dec 22 15:14:09 apt-install:  linux-server depends on linux-image-server (= 2.6.22.14.21); however:
Dec 22 15:14:09 apt-install:   Package linux-image-server is not configured yet.
Dec 22 15:14:09 apt-install: dpkg: error processing linux-server (--configure):
Dec 22 15:14:09 apt-install:  dependency problems - leaving unconfigured
Dec 22 15:14:09 apt-install: E: 
Dec 22 15:14:09 apt-install: Sub-process /usr/bin/dpkg returned an error code (1)
Dec 22 15:14:09 apt-install: 
Dec 22 15:14:09 base-installer: error: exiting on error base-installer/kernel/failed-install
Dec 22 15:14:19 init: Starting pid 3119, console /dev/tty2: '/bin/sh'


That ends the session. Sorry for the long post. I am unable to upload the bzipped file. So , I have booted from the Live CD and in the Forum....

Current plight is Dead in the Water...

---

### Post by Pumalite on 2007-12-22
Try to install a different distro and find out if you are incompatible with Linux in general or Ubuntu in particular

---

### Post by ColinOpseth on 2007-12-22
Try PCLinuxOS. First distrib that worked the first time and every subsquent attempt to reinstall. It uses KDE as the gui, though. Definitely not my favorite. Installing Gnome is buggy at times although it's gotten easier as time Texstar has embraced Gnome users. 

I've been trying to install Ubuntu with nothing but error 15 problems through Grub. My partitions are set correctly in grub and I've rechecked the symbolic links. Something isn't right but after 3 days I'm tired of dealing with what seems to be a very common problem.

Try PCLOS. I'm on the LiveCD for it right now, installing over Ubuntu right now. I wish I could get Ubuntu to work. It looks really nice.

---

### Post by Pumalite on 2007-12-22
Harsware works in some distros better than others. Too bad you had to give up Ubuntu.

---

### Post by joachi on 2007-12-22
Finally I have recovered back to 7.04 and it seems to be working fine. But, I am sure that the installation is not complete or smooth. But it seems to be working reasonably well as before. I have been an Ubuntu user since the first 6.06LTS and was very happy. The reason I wanted to move was the later version of Java that I need for some application. I am still not sure why depmod fails. Maybe I should do some digging. Even while I was installing the 7.04 there was a segmentation violation at that stage but the application seems to be ignoring it and completing the install. When I have some time I will debug it some more....

---

### Post by Pumalite on 2007-12-22
Glad you got Ubuntu working.

---

### Post by jbeckford1 on 2007-12-26
just my $0.02...

I suggest you setup networking with a static IP even if you have DHCP working just to be sure... And if it still gets stuck @ 83%, do a ctrl+alt+F1/2/3 whichever gives a prompt or just open a terminal and run the following to restart networking... 
```

sudo -i
/etc/init.d/networking restart
exit

```

I suggest a terminal since you can just copy and paste... I had to do this every other time I installed on my iBook as well as once on my SC5200 server... I suggest this since 83% on both installs is where it is DOWNLOADING the rest of my language pack, which is english, which I thought the majority of ubuntu users would use..?? 

Anywho, I also had to uncheck the box in networking where it stated to "scan and discover network services", since one of my neighbors somewhere around here has a wireless setup that points to no-where and the Airport card would identify it as the DNS and would not be able to resolve the ubuntu.com domain... 

If you have difficulty locating your ISPs DNS server addy, I suggest using searching for the OpenDNS server IPs and write those down for use during installation... [I didnt post the IP as I dont know if it any post violation, just google OpenDNS]...

Hope that helps...

---

### Post by Pumalite on 2007-12-26
Good idea. Main thing is to be wired to the internet during installation and configure your wireless later.

---

### Post by joachi on 2007-12-28
Thanks. I will try that as soon as I am back....

-- DJ

---

