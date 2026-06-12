---
title: "UEFI manual partitions &amp; dual boot"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by Spae on 2018-04-27
I'm really confused about how to install ubuntu in uefi boot mode. 

1. I am fairly sure that I have booted the installation media in uefi mode since my bios has uefi only with legacy support OFF. Is this safe to assume?
2. I have an existing windows UEFI boot partition

edit:
I have tried a few different install options, as I have read more information but I still receive ```
[COLOR=#111111][FONT=Ubuntu]the grub-efi-amd64-signed package failed to install into /target/[/FONT][/COLOR]
```

I now know that the installer ignores if you choose anything for boot if you are installing in uefi mode.
Still not sure whether to select the windows uefi partition as efi system partition or reserved bios boot but I suppose it's the former. Still no success.

I'm looking through this [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)
But I can't see anything to do differently. I disabled fast boot on windows, secure boot is disabled. I don't understand when it says gpt is recommended. The disk i'm installing to already has a partition table since windows is already installed on it, so I can't change it.
I have backed up my windows UEFI boot partition although after all of my failed installs it remains untouched anyway.

---

### Post by Spae on 2018-04-27
i have only two linux partitions, / and swap. 
Is this adequate?

```
ubuntu@ubuntu:~$ grep grub /var/log/syslogApr 27 21:01:16 ubuntu grub-common[1074]:  * Recording successful boot for GRUB
Apr 27 21:01:16 ubuntu grub-common[1074]:    ...done.
Apr 27 21:02:49 ubuntu ureadahead[984]: ureadahead:/etc/init.d/grub-common: Error retrieving chunk extents: Operation not supported
Apr 27 21:02:50 ubuntu ureadahead[984]: ureadahead:/etc/bash_completion.d/grub: Error retrieving chunk extents: Operation not supported
Apr 27 12:43:02 ubuntu ubiquity: grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
Apr 27 12:44:30 ubuntu grub-installer: info: architecture: amd64/efi
Apr 27 12:44:30 ubuntu grub-installer: info: Identified partition label for /dev/mapper/*removed*
Apr 27 12:44:30 ubuntu grub-installer: (Reading database ... 143891 files and directories currently installed.)
Apr 27 12:44:30 ubuntu grub-installer: Removing grub-gfxpayload-lists (0.7) ...
Apr 27 12:44:31 ubuntu grub-installer: Removing grub-pc (2.02-2ubuntu8) ...
Apr 27 12:44:31 ubuntu grub-installer: Purging configuration files for grub-pc (2.02-2ubuntu8) ...
Apr 27 12:44:31 ubuntu grub-installer: Removing grub-pc-bin (2.02-2ubuntu8) ...
Apr 27 12:44:31 ubuntu grub-installer: Processing triggers for man-db (2.8.3-2) ...
Apr 27 12:44:35 ubuntu ubiquity:   grub-efi-amd64 grub-efi-amd64-bin
Apr 27 12:44:35 ubuntu ubiquity:   grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed
Apr 27 12:44:35 ubuntu ubiquity: Get:1 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic/main amd64 grub-efi-amd64-bin amd64 2.02-2ubuntu8 [654 kB]
Apr 27 12:44:35 ubuntu ubiquity: Get:2 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic/main amd64 grub-efi-amd64 amd64 2.02-2ubuntu8 [46.8 kB]
Apr 27 12:44:35 ubuntu ubiquity: Get:3 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic/main amd64 grub-efi-amd64-signed amd64 1.93+2.02-2ubuntu8 [297 kB]
Apr 27 12:44:35 ubuntu ubiquity: Selecting previously unselected package grub-efi-amd64-bin.
Apr 27 12:44:35 ubuntu ubiquity: Preparing to unpack .../grub-efi-amd64-bin_2.02-2ubuntu8_amd64.deb ...
Apr 27 12:44:35 ubuntu ubiquity: Unpacking grub-efi-amd64-bin (2.02-2ubuntu8) ...
Apr 27 12:44:36 ubuntu ubiquity: Selecting previously unselected package grub-efi-amd64.
Apr 27 12:44:36 ubuntu ubiquity: Preparing to unpack .../grub-efi-amd64_2.02-2ubuntu8_amd64.deb ...
Apr 27 12:44:36 ubuntu ubiquity: Unpacking grub-efi-amd64 (2.02-2ubuntu8) ...
Apr 27 12:44:36 ubuntu ubiquity: Selecting previously unselected package grub-efi-amd64-signed.
Apr 27 12:44:36 ubuntu ubiquity: Preparing to unpack .../grub-efi-amd64-signed_1.93+2.02-2ubuntu8_amd64.deb ...
Apr 27 12:44:36 ubuntu ubiquity: Unpacking grub-efi-amd64-signed (1.93+2.02-2ubuntu8) ...
Apr 27 12:44:36 ubuntu ubiquity: Setting up grub-efi-amd64-bin (2.02-2ubuntu8) ...
Apr 27 12:44:36 ubuntu ubiquity: Setting up grub-efi-amd64 (2.02-2ubuntu8) ...
Apr 27 12:44:36 ubuntu ubiquity: Creating config file /etc/default/grub with new version
Apr 27 12:44:37 ubuntu ubiquity: File descriptor 3 (pipe:[114374]) leaked on vgs invocation. Parent PID 9776: grub-install
Apr 27 12:44:37 ubuntu ubiquity: File descriptor 5 (/dev/sda1) leaked on vgs invocation. Parent PID 9776: grub-install
Apr 27 12:44:37 ubuntu ubiquity: File descriptor 3 (pipe:[114374]) leaked on vgs invocation. Parent PID 9776: grub-install
Apr 27 12:44:37 ubuntu ubiquity: File descriptor 5 (/dev/sda1) leaked on vgs invocation. Parent PID 9776: grub-install
Apr 27 12:44:37 ubuntu ubiquity: grub-install: error: attempt to install to encrypted disk without cryptodisk enabled. Set `GRUB_ENABLE_CRYPTODISK=y' in file `/etc/default/grub'.
Apr 27 12:44:37 ubuntu ubiquity: Failed: grub-install --target=x86_64-efi
Apr 27 12:44:37 ubuntu ubiquity: Setting up grub-efi-amd64-signed (1.93+2.02-2ubuntu8) ...
Apr 27 12:44:38 ubuntu ubiquity: File descriptor 4 (/dev/sda1) leaked on vgs invocation. Parent PID 9827: grub-install
Apr 27 12:44:38 ubuntu ubiquity: File descriptor 4 (/dev/sda1) leaked on vgs invocation. Parent PID 9827: grub-install
Apr 27 12:44:38 ubuntu ubiquity: grub-install: error: attempt to install to encrypted disk without cryptodisk enabled. Set `GRUB_ENABLE_CRYPTODISK=y' in file `/etc/default/grub'.
Apr 27 12:44:38 ubuntu ubiquity: dpkg: error processing package grub-efi-amd64-signed (--configure):
Apr 27 12:44:38 ubuntu ubiquity:  installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
Apr 27 12:44:38 ubuntu ubiquity:  grub-efi-amd64-signed
Apr 27 12:44:43 ubuntu ubiquity: File descriptor 3 (pipe:[117206]) leaked on vgs invocation. Parent PID 9965: grub-install
Apr 27 12:44:43 ubuntu ubiquity: File descriptor 5 (/dev/sda1) leaked on vgs invocation. Parent PID 9965: grub-install
Apr 27 12:44:43 ubuntu ubiquity: File descriptor 3 (pipe:[117206]) leaked on vgs invocation. Parent PID 9965: grub-install
Apr 27 12:44:43 ubuntu ubiquity: File descriptor 5 (/dev/sda1) leaked on vgs invocation. Parent PID 9965: grub-install
Apr 27 12:44:43 ubuntu ubiquity: grub-install: error: attempt to install to encrypted disk without cryptodisk enabled. Set `GRUB_ENABLE_CRYPTODISK=y' in file `/etc/default/grub'.
Apr 27 12:44:43 ubuntu ubiquity: Setting up grub-efi-amd64-signed (1.93+2.02-2ubuntu8) ...
Apr 27 12:44:44 ubuntu ubiquity: File descriptor 4 (/dev/sda1) leaked on vgs invocation. Parent PID 10014: grub-install
Apr 27 12:44:44 ubuntu ubiquity: File descriptor 4 (/dev/sda1) leaked on vgs invocation. Parent PID 10014: grub-install
Apr 27 12:44:44 ubuntu ubiquity: grub-install: error: attempt to install to encrypted disk without cryptodisk enabled. Set `GRUB_ENABLE_CRYPTODISK=y' in file `/etc/default/grub'.
Apr 27 12:44:44 ubuntu ubiquity: dpkg: error processing package grub-efi-amd64-signed (--configure):
Apr 27 12:44:44 ubuntu ubiquity:  installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
Apr 27 12:44:44 ubuntu ubiquity:  grub-efi-amd64-signed
Apr 27 12:44:46 ubuntu grub-installer: info: Calling 'apt-install grub-efi-amd64-signed' failed
``` 
I'm going to sleep but I hope someone can have a look at this for me. Seems like there are multiple errors.

---

### Post by oldfred on 2018-04-27
Ubuntu since 17.04 does not use swap partition unless you already have one. It now creates & uses a swap file.

With UEFI grub only installs to ESP - efi system partition on drive seen as sda. Sometimes that is not the drive your really want, it can depend on order that UEFI/BIOS mount & see drives.

Some have corrupted ESP and need repairs to the FAT32 partition. You can use Windows chkdsk or Linux dosfsck.

       Must be unmounted, change sdb1 example to your ESP/FAT32 partition.
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185) 

    
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Spae on 2018-04-28
Here's the log [http://paste.ubuntu.com/p/tHkswPf4qJ/](http://paste.ubuntu.com/p/tHkswPf4qJ/) that you asked for.

I have a question about the syslog that I previously posted. It says
> [COLOR=#000000][FONT=&quot] grub-install: error: attempt to install to encrypted disk without cryptodisk enabled. Set `GRUB_ENABLE_CRYPTODISK=y' in file `/etc/default/grub'.[/FONT][/COLOR]
Yes I am installing to an encrypted disk. Do I have to change anything? Even if I edit the file apparently I have to use update-grub command for it to take effect, and that causes an error itself.

---

### Post by oldfred on 2018-04-28
Do not know about encrypted drives.
That uses LVM and encryption.
And some newer versions do not require the separate /boot partition, so grub would need some way to ask for encryption key to get into encrypted /boot to start booting.

Boot-Repair may not turn on the [COLOR=#000000][FONT=&amp]cryptodisk settings?
If that is an issue we need to report a bug to Boot-Repair.
[/FONT][/COLOR]

---

