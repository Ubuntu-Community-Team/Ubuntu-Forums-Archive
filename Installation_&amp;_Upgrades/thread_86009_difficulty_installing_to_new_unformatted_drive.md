---
title: "difficulty installing to new unformatted drive"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by holiday on 2005-11-04
This is my fourth Ubuntu installation and the first that's given me trouble. I have successfully installed to an empty drive before so I'm concerned there may be trouble with the drive or perhaps some incompatibility at some point. 

The partman log *looks* ok to me. I'll post it if anyone thinks there may be a problem there. Here's its last statement

p```
arted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 214
parted_server: Opening infifo
/lib/partman/finish.d/80parted: *******************************************************
/lib/partman/finish.d/80parted: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting



```

The messages log seems to show trouble here:Sorry to post so much but I can't make sense of it. I think the trouble starts right here at the top = not sure. 

```
Nov  3 23:27:45 main-menu[4125]: DEBUG: configure harddrive-detection, status: 0  
Nov  3 23:27:45 main-menu[4125]: DEBUG: virtual package harddrive-detection  
Nov  3 23:30:09 main-menu[4125]: (process:15559): unsupported 
Nov  3 23:30:09 main-menu[4125]: (process:15559): kernelmodules_basicfilesystems 
Nov  3 23:30:09 main-menu[4125]: (process:15559): kernelmodules_ext3 
Nov  3 23:30:09 main-menu[4125]: (process:15559): kernelmodules_jfs 
Nov  3 23:30:09 main-menu[4125]: (process:15559): kernelmodules_reiserfs 
Nov  3 23:30:09 main-menu[4125]: (process:15559): kernelmodules_xfs 
Nov  3 23:30:09 main-menu[4125]: (process:15559): umount_target 
Nov  3 23:30:09 main-menu[4125]: (process:15559): parted 
Nov  3 23:30:09 main-menu[4125]: (process:15559): md-devices 
Nov  3 23:30:09 main-menu[4125]: (process:15559): grep:  
Nov  3 23:30:09 main-menu[4125]: (process:15559): /proc/mdstat 
Nov  3 23:30:09 main-menu[4125]: (process:15559): : No such file or directory 
Nov  3 23:30:09 main-menu[4125]: (process:15559): dump 
Nov  3 23:30:09 main-menu[4125]: (process:15559): lvm 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 3 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 4 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 5 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 6 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559):    
Nov  3 23:30:09 main-menu[4125]: (process:15559): /proc/misc: No entry for device-mapper found 
Nov  3 23:30:09 main-menu[4125]: (process:15559):  
Nov  3 23:30:09 main-menu[4125]: (process:15559):    
Nov  3 23:30:09 main-menu[4125]: (process:15559): Is device-mapper driver missing from kernel? 
Nov  3 23:30:09 main-menu[4125]: (process:15559):  
Nov  3 23:30:09 main-menu[4125]: (process:15559):    
Nov  3 23:30:09 main-menu[4125]: (process:15559): Failure to communicate with kernel device-mapper driver. 
Nov  3 23:30:09 main-menu[4125]: (process:15559):  
Nov  3 23:30:09 main-menu[4125]: (process:15559):    
Nov  3 23:30:09 main-menu[4125]: (process:15559): /proc/misc: No entry for device-mapper found 
Nov  3 23:30:09 main-menu[4125]: (process:15559):  
Nov  3 23:30:09 main-menu[4125]: (process:15559):    
Nov  3 23:30:09 main-menu[4125]: (process:15559): Is device-mapper driver missing from kernel? 
Nov  3 23:30:09 main-menu[4125]: (process:15559):  
Nov  3 23:30:09 main-menu[4125]: (process:15559):    
Nov  3 23:30:09 main-menu[4125]: (process:15559): Failure to communicate with kernel device-mapper driver. 
Nov  3 23:30:09 main-menu[4125]: (process:15559):  
Nov  3 23:30:09 main-menu[4125]: (process:15559):    
Nov  3 23:30:09 main-menu[4125]: (process:15559): Incompatible libdevmapper 1.01.03 (2005-06-13)(compat) and kernel driver  
Nov  3 23:30:09 main-menu[4125]: (process:15559):  
Nov  3 23:30:09 main-menu[4125]: (process:15559): md 
Nov  3 23:30:09 main-menu[4125]: (process:15559): update_partitions 
Nov  3 23:30:09 main-menu[4125]: (process:15559): filesystems_detected 
Nov  3 23:30:09 main-menu[4125]: (process:15559): auto_mountpoints 
Nov  3 23:30:09 main-menu[4125]: (process:15559): autouse_swap 
Nov  3 23:30:09 main-menu[4125]: (process:15559): backup 
Nov  3 23:30:09 main-menu[4125]: (process:15559): grep:  
Nov  3 23:30:09 main-menu[4125]: (process:15559): [[:space:]]/boot[[:space:]] 
Nov  3 23:30:09 main-menu[4125]: (process:15559): : No such file or directory 
Nov  3 23:30:09 main-menu[4125]: (process:15559): eval: 43:  
Nov  3 23:30:09 main-menu[4125]: (process:15559): cannot create 255015936-200047034879/: Is a directory 
Nov  3 23:30:09 main-menu[4125]: (process:15559):  
Nov  3 23:30:09 main-menu[4125]: (process:15559): eval: 43:  
Nov  3 23:30:09 main-menu[4125]: (process:15559): cannot create 255015936-200047034879/: Is a directory 
Nov  3 23:30:09 main-menu[4125]: (process:15559):  
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 3 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 4 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 5 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 3 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 4 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 5 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): grep:  
Nov  3 23:30:09 main-menu[4125]: (process:15559): /proc/mdstat 
Nov  3 23:30:09 main-menu[4125]: (process:15559): : No such file or directory 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 3 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 4 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): File descriptor 5 left open 
Nov  3 23:30:09 main-menu[4125]: (process:15559): swapon:  
Nov  3 23:30:09 main-menu[4125]: (process:15559): /dev/mapper/Ubuntu-swap_1 
Nov  3 23:30:09 main-menu[4125]: (process:15559): : Device or resource busy 
Nov  3 23:30:09 main-menu[4125]: (process:15559): swapon:  
Nov  3 23:30:09 main-menu[4125]: (process:15559): /dev/mapper/Ubuntu-swap_1 
Nov  3 23:30:09 main-menu[4125]: (process:15559): : Device or resource busy 
Nov  3 23:30:09 main-menu[4125]: (process:15559): swapon:  
Nov  3 23:30:09 main-menu[4125]: (process:15559): /dev/mapper/Ubuntu-swap_1 
Nov  3 23:30:09 main-menu[4125]: (process:15559): : Device or resource busy 
Nov  3 23:30:09 main-menu[4125]: (process:15559): swapon:  
Nov  3 23:30:09 main-menu[4125]: (process:15559): /dev/mapper/Ubuntu-swap_1 
Nov  3 23:30:09 main-menu[4125]: (process:15559): : Device or resource busy 
Nov  3 23:30:09 main-menu[4125]: (process:15559): umount /target/ 
Nov  3 23:30:09 main-menu[4125]: (process:15559): umount /target/boot 
Nov  3 23:30:09 main-menu[4125]: (process:15559): swapoff /dev/mapper/Ubuntu-swap_1 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libc6): search, dependency from cdebconf-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libnss-dns-udeb): mark, dependency from libc6-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libnss-files-udeb): mark, dependency from libc6-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libc6-udeb): mark, dependency from cdebconf-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libdebian-installer4): search, dependency from cdebconf-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libdebian-installer4-udeb): mark, dependency from cdebconf-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libtextwrap1): package doesn't exist (ignored) 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (cdebconf-udeb): mark, dependency from localechooser 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (iso-3166-udeb): mark, dependency from localechooser 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (localechooser): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libdebconfclient0): search, dependency from kbd-chooser 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libdebconfclient0-udeb): mark, dependency from kbd-chooser 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (console-keymaps): search, dependency from kbd-chooser 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (console-keymaps-usb): mark, dependency from kbd-chooser 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (kbd-chooser): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (discover): package doesn't exist (ignored) 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (rootskel): mark, dependency from hw-detect 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (archdetect): mark, dependency from hw-detect 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (pciutils-udeb): mark, dependency from hw-detect 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (hw-detect): mark, dependency from cdrom-detect 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (hdparm-udeb): mark, dependency from cdrom-detect 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (cdrom-detect): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (di-utils): mark, dependency from file-preseed 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (preseed-common): mark, dependency from file-preseed 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (file-preseed): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (cdrom-retriever): mark, dependency from load-cdrom 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (anna): mark, dependency from load-cdrom 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (load-cdrom): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (ethdetect): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libiw28-udeb): mark, dependency from netcfg 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (dhcp-client-udeb): mark, dependency from netcfg 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (ethernet-card-detection): search, dependency from netcfg 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (netcfg): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (configured-network): search, dependency from network-preseed 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (network-preseed): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libusb-0.1-udeb): mark, dependency from usbutils-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (usbutils-udeb): mark, dependency from multiseat-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (input-modules): search, dependency from multiseat-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (kernel-image-2.6.12-9-386-di): mark, dependency from input-modules-2.6.12-9-386-di 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (usb-modules-2.6.12-9-386-di): mark, dependency from input-modules-2.6.12-9-386-di 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (input-modules-2.6.12-9-386-di): mark, dependency from multiseat-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (multiseat-udeb): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (hw-detect-full): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libparted1.6-12): search, dependency from partman-base 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libuuid1): search, dependency from libparted1.6-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libuuid1-udeb): mark, dependency from libparted1.6-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libparted1.6-udeb): mark, dependency from partman-base 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (ntfstools-udeb): mark, dependency from partman-partitioning 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (partman-partitioning): mark, dependency from partman-base 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (libblkid1-udeb): mark, dependency from e2fsprogs-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (e2fsprogs-udeb): mark, dependency from partman-basicfilesystems 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (ext2-modules): search, dependency from partman-basicfilesystems 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (fat-modules): search, dependency from partman-basicfilesystems 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (fat-modules-2.6.12-9-386-di): mark, dependency from partman-basicfilesystems 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (partconf-mkfstab): mark, dependency from partman-basicfilesystems 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (partman-basicfilesystems): mark, dependency from partman-target 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (partman-basicmethods): mark, dependency from partman-target 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (di-utils-mapdevfs): mark, dependency from partman-target 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (partman-target): mark, dependency from partman-base 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (harddrive-detection): search, dependency from partman-base 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (partman-base): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (mounted-partitions): search, dependency from base-installer 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (debootstrap-udeb): mark, dependency from base-installer 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (created-fstab): search, dependency from base-installer 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (base-installer): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (archive-copier): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (target-base-system): search, dependency from tzsetup-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (ext3-modules): search, dependency from os-prober 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (ext3-modules-2.6.12-9-386-di): mark, dependency from os-prober 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (reiserfs-modules): search, dependency from os-prober 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (reiserfs-modules-2.6.12-9-386-di): mark, dependency from os-prober 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (xfs-modules): search, dependency from os-prober 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (xfs-modules-2.6.12-9-386-di): mark, dependency from os-prober 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (ntfs-modules): search, dependency from os-prober 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (ntfs-modules-2.6.12-9-386-di): mark, dependency from os-prober 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (os-prober): mark, dependency from tzsetup-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (rtc-modules): search, dependency from tzsetup-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (rtc-modules-2.6.12-9-386-di): mark, dependency from tzsetup-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (tzsetup-udeb): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (initial-passwd-udeb): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (apt-setup-udeb): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (kernel-installer): search, dependency from grub-installer 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (grub-installer): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (fdisk-udeb): mark, dependency from lilo-installer 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (lilo-installer): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (parted-udeb): mark, dependency from nobootloader 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (nobootloader): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (bootable-system): search, dependency from prebaseconfig 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (prebaseconfig): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (cdebconf-priority): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (cdrom-checker): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (save-logs): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (di-utils-shell): mark 
Nov  3 23:30:09 main-menu[4125]: DEBUG: resolver (di-utils-reboot): mark 
Nov  3 23:30:09 main-menu[4125]: INFO: Falling back to the package description for multiseat-udeb 
Nov  3 23:30:09 main-menu[4125]: INFO: Falling back to the package description for multiseat-udeb 
Nov  3 23:30:09 main-menu[4125]: DEBUG: Menu item 'base-installer' selected 
Nov  3 23:30:09 main-menu[4125]: DEBUG: configure base-installer, status: 2  
Nov  3 23:30:09 main-menu[4125]: DEBUG: configure libc6, status: 0  
Nov  3 23:30:09 main-menu[4125]: DEBUG: virtual package libc6  
Nov  3 23:30:09 main-menu[4125]: DEBUG: configure libdebconfclient0, status: 0  
Nov  3 23:30:09 main-menu[4125]: DEBUG: virtual package libdebconfclient0  
Nov  3 23:30:09 main-menu[4125]: DEBUG: configure libdebian-installer4, status: 0  
Nov  3 23:30:09 main-menu[4125]: DEBUG: virtual package libdebian-installer4  
Nov  3 23:30:09 main-menu[4125]: DEBUG: configure mounted-partitions, status: 0  
Nov  3 23:30:09 main-menu[4125]: DEBUG: virtual package mounted-partitions  
Nov  3 23:30:09 main-menu[4125]: DEBUG: configure created-fstab, status: 0  
Nov  3 23:30:09 main-menu[4125]: DEBUG: virtual package created-fstab  
Nov  3 23:30:10 base-installer: info: Execution hook before debootstrap
Nov  3 23:30:10 base-installer: info: Running /usr/lib/base-installer.d/01save-logs
Nov  3 23:30:10 base-installer: info: Running /usr/lib/base-installer.d/40netcfg
Nov  3 23:31:05 base-installer: error: exiting on error base-installer/debootstrap-failed
Nov  3 23:31:11 main-menu[4125]: WARNING **: Configuring 'base-installer' failed with error code 1 
Nov  3 23:31:11 main-menu[4125]: WARNING **: Menu item 'base-installer' failed. 
Nov  3 23:31:15 main-menu[4125]: INFO: Modifying debconf priority limit from 'high' to 'medium' 
Nov  3 23:31:15 debconf: Setting debconf/priority to medium
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libc6): search, dependency from cdebconf-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libnss-dns-udeb): mark, dependency from libc6-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libnss-files-udeb): mark, dependency from libc6-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libc6-udeb): mark, dependency from cdebconf-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libdebian-installer4): search, dependency from cdebconf-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libdebian-installer4-udeb): mark, dependency from cdebconf-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libtextwrap1): package doesn't exist (ignored) 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (cdebconf-udeb): mark, dependency from localechooser 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (iso-3166-udeb): mark, dependency from localechooser 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (localechooser): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libdebconfclient0): search, dependency from kbd-chooser 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libdebconfclient0-udeb): mark, dependency from kbd-chooser 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (console-keymaps): search, dependency from kbd-chooser 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (console-keymaps-usb): mark, dependency from kbd-chooser 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (kbd-chooser): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (discover): package doesn't exist (ignored) 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (rootskel): mark, dependency from hw-detect 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (archdetect): mark, dependency from hw-detect 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (pciutils-udeb): mark, dependency from hw-detect 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (hw-detect): mark, dependency from cdrom-detect 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (hdparm-udeb): mark, dependency from cdrom-detect 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (cdrom-detect): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (di-utils): mark, dependency from file-preseed 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (preseed-common): mark, dependency from file-preseed 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (file-preseed): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (cdrom-retriever): mark, dependency from load-cdrom 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (anna): mark, dependency from load-cdrom 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (load-cdrom): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (ethdetect): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libiw28-udeb): mark, dependency from netcfg 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (dhcp-client-udeb): mark, dependency from netcfg 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (ethernet-card-detection): search, dependency from netcfg 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (netcfg): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (configured-network): search, dependency from network-preseed 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (network-preseed): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libusb-0.1-udeb): mark, dependency from usbutils-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (usbutils-udeb): mark, dependency from multiseat-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (input-modules): search, dependency from multiseat-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (kernel-image-2.6.12-9-386-di): mark, dependency from input-modules-2.6.12-9-386-di 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (usb-modules-2.6.12-9-386-di): mark, dependency from input-modules-2.6.12-9-386-di 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (input-modules-2.6.12-9-386-di): mark, dependency from multiseat-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (multiseat-udeb): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (hw-detect-full): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libparted1.6-12): search, dependency from partman-base 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libuuid1): search, dependency from libparted1.6-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libuuid1-udeb): mark, dependency from libparted1.6-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libparted1.6-udeb): mark, dependency from partman-base 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (ntfstools-udeb): mark, dependency from partman-partitioning 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (partman-partitioning): mark, dependency from partman-base 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (libblkid1-udeb): mark, dependency from e2fsprogs-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (e2fsprogs-udeb): mark, dependency from partman-basicfilesystems 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (ext2-modules): search, dependency from partman-basicfilesystems 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (fat-modules): search, dependency from partman-basicfilesystems 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (fat-modules-2.6.12-9-386-di): mark, dependency from partman-basicfilesystems 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (partconf-mkfstab): mark, dependency from partman-basicfilesystems 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (partman-basicfilesystems): mark, dependency from partman-target 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (partman-basicmethods): mark, dependency from partman-target 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (di-utils-mapdevfs): mark, dependency from partman-target 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (partman-target): mark, dependency from partman-base 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (harddrive-detection): search, dependency from partman-base 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (partman-base): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (mounted-partitions): search, dependency from base-installer 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (debootstrap-udeb): mark, dependency from base-installer 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (created-fstab): search, dependency from base-installer 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (base-installer): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (archive-copier): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (target-base-system): search, dependency from tzsetup-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (ext3-modules): search, dependency from os-prober 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (ext3-modules-2.6.12-9-386-di): mark, dependency from os-prober 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (reiserfs-modules): search, dependency from os-prober 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (reiserfs-modules-2.6.12-9-386-di): mark, dependency from os-prober 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (xfs-modules): search, dependency from os-prober 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (xfs-modules-2.6.12-9-386-di): mark, dependency from os-prober 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (ntfs-modules): search, dependency from os-prober 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (ntfs-modules-2.6.12-9-386-di): mark, dependency from os-prober 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (os-prober): mark, dependency from tzsetup-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (rtc-modules): search, dependency from tzsetup-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (rtc-modules-2.6.12-9-386-di): mark, dependency from tzsetup-udeb 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (tzsetup-udeb): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (initial-passwd-udeb): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (apt-setup-udeb): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (kernel-installer): search, dependency from grub-installer 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (grub-installer): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (fdisk-udeb): mark, dependency from lilo-installer 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (lilo-installer): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (parted-udeb): mark, dependency from nobootloader 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (nobootloader): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (bootable-system): search, dependency from prebaseconfig 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (prebaseconfig): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (cdebconf-priority): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (cdrom-checker): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (save-logs): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (di-utils-shell): mark 
Nov  3 23:31:15 main-menu[4125]: DEBUG: resolver (di-utils-reboot): mark 
Nov  3 23:31:15 main-menu[4125]: INFO: Falling back to the package description for multiseat-udeb 
Nov  3 23:31:35 main-menu[4125]: INFO: Falling back to the package description for multiseat-udeb 
Nov  3 23:31:35 main-menu[4125]: DEBUG: Menu item 'save-logs' selected 
Nov  3 23:31:35 main-menu[4125]: DEBUG: configure save-logs, status: 2  

```

---

### Post by SickTwist on 2005-11-04
The install CD could be corrupted or the optical drive bad. What happens/fails during the install?

---

### Post by holiday on 2005-11-04
Right. The install iso was bad. 

But now I have another problem. Ubuntu has installed but it sees the disc as hdb(slave)  whereas it is jumpered to master, cabled as master, and is recognized as master by the BIOS. 

Am I missing something? Ubuntu seems to be working though.

---

### Post by SickTwist on 2005-11-04
Very strange. So if this is the IDE cable

B=======================S======M

where B is the motherboard, S is the slave device (if any) and M is the master, you have the HDD hooked up to the M position, correct? Also you may want to verify the jumpers but it sounds like you did all that.

If you *do* have a slave device on the same cable as the HDD, check to see that the slave device is also jumpered correctly.

Not sure what else it could be. Check the website of your motherboard/computer manufacturer to see if there are any BIOS updates. Perhaps there is a bug in the BIOS?

---

### Post by holiday on 2005-11-04
Yes - thank you. I was *sure* the jumpers were correct but after putting my eyes in their right sides I saw that the jumpers were reversed. So I set them right  and - well - what hell ensued. Sweat drips on my keyboard. Monkeying with BIOS settings...

Ubuntu seems to be happily installing now to hd0. I wonder if it will boot. 

If not, I'll have to dig up my BIOS docs  I guess. 

Thanks for the prompts.

---

