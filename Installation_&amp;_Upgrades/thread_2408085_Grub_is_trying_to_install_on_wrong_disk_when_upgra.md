---
title: "Grub is trying to install on wrong disk when upgrading"
date: 2018-12-13
forum: Installation &amp; Upgrades
---

### Post by scporse on 2018-12-13
Greetings fellow Ubuntu people :)

I'm seeing an error on my Ubuntu 16.04.5 LTS (Lubuntu) system when upgrading grub.
This is the second time it has happened - having upgraded grub packages once before, where the error first presented itself.

So, the situation is this:

In terminal, I initiate an apt-upgrade of grub (among other pakages), and then suddenly I'm presented with this prompt in the terminal:

```
[Grub failed to install to the following devices:

/dev/sdb

Do you want to continue anyway? If you do, your computer may not start up properly.

Writing GRUB to boot device failed - continue

<Yes>    <No>
```


I then select Yes and the upgrade finishes - successfully it seems, as command grub-install shows: grub-install (GRUB) 2.02~beta2-36ubuntu3.20

The first time I got the above prompt I was quite worried that I would be unable to boot up linux afterwards, as per the message it contained. 
To my great relief, this was not the case - the system booted up just fine and there seems to have been no further complications.

It might be relevant to state the fact that I first saw the error, not so long after restoring my system to an earlier configuration from a full system backup, having unintentionally broken some media center software beforehand...

A strange thing about the grub upgrade error is that the device it points to (dev/sdb) is not my system disk, and is actually a device with only one large ext4 partion, as seen when running the command parted -l as sudo:

```
sudo parted -l
Model: ATA OCZ-VERTEX3 (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB                        bios_grub
 2      2097kB  4098MB  4096MB  linux-swap(v1)
 3      4098MB  29.1GB  25.0GB  ext4
 4      29.1GB  60.0GB  30.9GB  ext4




Model: ATA WDC WD30EFRX-68E (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  ext4

```

Does anyone have an idea what's wrong with my current configuration and how I might be able to correct it, so that I avoid this rather alarming error upon future grub-upgrades?

I thought it could be helpful to include the terminal output from the last grub-upgrade process as well:


```
The following packages will be upgraded:
  grub-common grub-pc grub-pc-bin grub2-common libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1 libfreerdp-common1.1.0
  libfreerdp-core1.1 libfreerdp-crypto1.1 libfreerdp-gdi1.1 libfreerdp-locale1.1 libfreerdp-primitives1.1 libfreerdp-utils1.1
  libpoppler-glib8 libpoppler58 libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1 libwinpr-file0.1 libwinpr-handle0.1
  libwinpr-heap0.1 libwinpr-input0.1 libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1 libwinpr-pool0.1
  libwinpr-registry0.1 libwinpr-rpc0.1 libwinpr-sspi0.1 libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1
  poppler-utils
35 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/5,126 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 194961 files and directories currently installed.)
Preparing to unpack .../grub-pc_2.02~beta2-36ubuntu3.20_amd64.deb ...
Unpacking grub-pc (2.02~beta2-36ubuntu3.20) over (2.02~beta2-36ubuntu3.19) ...
Preparing to unpack .../grub-pc-bin_2.02~beta2-36ubuntu3.20_amd64.deb ...
Unpacking grub-pc-bin (2.02~beta2-36ubuntu3.20) over (2.02~beta2-36ubuntu3.19) ...
Preparing to unpack .../grub2-common_2.02~beta2-36ubuntu3.20_amd64.deb ...
Unpacking grub2-common (2.02~beta2-36ubuntu3.20) over (2.02~beta2-36ubuntu3.19) ...
Preparing to unpack .../grub-common_2.02~beta2-36ubuntu3.20_amd64.deb ...
Unpacking grub-common (2.02~beta2-36ubuntu3.20) over (2.02~beta2-36ubuntu3.19) ...
Preparing to unpack .../libwinpr-sysinfo0.1_1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3_amd64.deb ...
Unpacking libwinpr-sysinfo0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) over (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.2) ...
Preparing to unpack .../libfreerdp-primitives1.1_1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3_amd64.deb ...
Unpacking libfreerdp-primitives1.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) over (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.2) ...
Preparing to unpack .../libwinpr-handle0.1_1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3_amd64.deb ...
Unpacking libwinpr-handle0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) over (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.2) ...
Preparing to unpack .../libwinpr-interlocked0.1_1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3_amd64.deb ...
Unpacking libwinpr-interlocked0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) over (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.2) ...
Preparing to unpack .../libwinpr-thread0.1_1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3_amd64.deb ...
Unpacking libwinpr-thread0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) over (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.2) ...
...

Processing triggers for man-db (2.7.5-1) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Processing triggers for systemd (229-4ubuntu21.10) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Setting up grub-common (2.02~beta2-36ubuntu3.20) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up grub2-common (2.02~beta2-36ubuntu3.20) ...
Setting up grub-pc-bin (2.02~beta2-36ubuntu3.20) ...
Setting up grub-pc (2.02~beta2-36ubuntu3.20) ...
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: error: embedding is not possible, but this is required for cross-disk install.
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-140-generic
Found initrd image: /boot/initrd.img-4.4.0-140-generic
Found linux image: /boot/vmlinuz-4.4.0-139-generic
Found initrd image: /boot/initrd.img-4.4.0-139-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```

---

### Post by yancek on 2018-12-13
The proper choice when you saw the message Grub failed to install to /dev/sdb would have been NO.  If it's a data drive, there is no need to install there but only to the drive on which your OS is installed.  Looks similar to what is done with boot repair when it installs to all drives.  Next time, either select No or dis-connect the drive first.

---

### Post by oldfred on 2018-12-13
In BIOS mode grub remembers where it installed originally.
If drive has changed, then that can be an issue.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  
      
 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by scporse on 2018-12-14
> **oldfred said:**
> In BIOS mode grub remembers where it installed originally.
If drive has changed, then that can be an issue.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  
      
 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Indeed, the wrong disk was selected in grub config, which I fixed in the way you suggested.

This is the current output from ```
 sudo debconf-show grub-pc :

  grub-pc/timeout: 3
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/chainload_from_menu.lst: true
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/install_devices_disks_changed:
  grub-pc/install_devices_empty: false
  grub-pc/hidden_timeout: true
  grub2/device_map_regenerated:
* grub2/linux_cmdline_default: text
  grub2/force_efi_extra_removable: false
  grub-pc/partition_description:
  grub2/kfreebsd_cmdline:
  grub2/update_nvram: true
  grub-pc/disk_description:
  grub-pc/install_devices_failed_upgrade: true
* grub-pc/install_devices_failed: true
* grub2/linux_cmdline:
  grub-pc/kopt_extracted: false
* grub-pc/install_devices: /dev/disk/by-id/ata-OCZ-VERTEX3_OCZ-ESX7K5AZYX25H2EH
```

As is evident, my OCZ SSD system disk is now selected and I've confirmed that my system is still able to boot up without issues.

So, unless you see anything else in the config above that needs correcting, I'll go ahead and mark this thread as solved.


Thank you very much taking the time to help me in this matter!

---

