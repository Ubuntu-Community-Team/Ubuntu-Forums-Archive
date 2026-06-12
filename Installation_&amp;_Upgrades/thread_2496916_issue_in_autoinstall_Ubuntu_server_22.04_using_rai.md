---
title: "issue in autoinstall Ubuntu server 22.04 using raid 1 configuration"
date: 2024-04-17
forum: Installation &amp; Upgrades
---

### Post by rcolombo-tecnavia on 2024-04-17
[COLOR=#0C0D0E][FONT=-apple-system]I tried to install Ubuntu server 22.04 (even with the latest daily version 24.04) using the autoinstall process, to get a bootable raid 1 configuration, using two 2TB m2 disks.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]The process keeps crashing at the point where it needs to install grub on the EFI partition.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I have tried different configurations for creating the raid, using both disks and partitions as devices, but to no avail, it fails to make the raid bootable.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]So the question for you guys is:, how can I set up my storage to have a bootable raid 1 configuration? I guess someone has already positively addressed this problem...[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]The storage section I am using, with all my attempts, is as follows:
[/FONT][/COLOR]
```
#cloud-config
autoinstall:
  version: 1
storage:
    grub:
      reorder_uefi: false
    config:
    # Partition table of two disks
    # - { type: disk, ptable: gpt, path: /dev/nvme0n1, wipe: superblock, preserve: false, name: '', grub_device: true, id: disk-nvme0n1 }
    # - { type: disk, ptable: gpt, path: /dev/nvme1n1, wipe: superblock, preserve: false, name: '', grub_device: true, id: disk-nvme1n1 }
    - { type: disk, ptable: gpt, path: /dev/nvme0n1, wipe: superblock, preserve: false, name: '', id: disk-nvme0n1 }
    - { type: disk, ptable: gpt, path: /dev/nvme1n1, wipe: superblock, preserve: false, name: '', id: disk-nvme1n1 }
    - { type: partition, device: disk-nvme0n1, size: 1024MB, wipe: superblock, flag: 'boot',partition_type: EF00, preserve: false,  grub_device: true, id: part-grub }
    #- { type: partition, device: disk-nvme0n1, size: 32GB, wipe: superblock, flag: 'swap', preserve: false, id: part-swap }
    - { type: partition, device: disk-nvme0n1, size: 256GB, wipe: superblock, preserve: false,  id: part-home }
    - { type: partition, device: disk-nvme0n1, size: -1, wipe: superblock, preserve: false,  id: part-data }
    #
    - { type: partition, device: disk-nvme1n1, size: 1024MB, wipe: superblock, preserve: false,  grub_device: false, id: part2-grub }
    #- { type: partition, device: disk-nvme1n1, size: 32GB, wipe: superblock, flag: 'swap', preserve: false, id: part2-swap }
    - { type: partition, device: disk-nvme1n1, size: 256GB, wipe: superblock, preserve: false,  id: part2-home }
    - { type: partition, device: disk-nvme1n1, size: -1, wipe: superblock, preserve: false,  id: part2-data }
    #
    #- { type: raid, name: md0, raidlevel: 1, devices: [ part-grub, part2-grub ], spare_devices: [], preserve: false, wipe: superblock-recursive, ptable: gpt, id: disk-raid-grub }
    #- { type: raid, name: md1, raidlevel: 1, devices: [ part-swap, part2-swap ], spare_devices: [], preserve: false, wipe: superblock-recursive, ptable: gpt, id: disk-raid-swap }
    - { type: raid, name: md2, raidlevel: 1, devices: [ part-home, part2-home ], spare_devices: [], preserve: false, wipe: superblock-recursive, ptable: gpt, id: disk-raid-home }
    - { type: raid, name: md3, raidlevel: 1, devices: [ part-data, part2-data ], spare_devices: [], preserve: false, wipe: superblock-recursive, ptable: gpt, id: disk-raid-data }
    #- { type: raid, name: md0, raidlevel: 1, devices: [ disk-nvme0n1, disk-nvme1n1 ], spare_devices: [], preserve: false, wipe: superblock-recursive, ptable: gpt, id: disk-raid }
    #- { type: partition, device: disk-raid, flag: bios_grub, id: part-grub, number: 1, preserve: false,  size: 1MB }
    # - { type: partition, device: disk-raid, size: 1024MB, wipe: superblock, flag: 'bios_grub', preserve: false,  grub_device: true, id: part-grub }
    #- { type: partition, device: disk-raid, size: 1024MB, wipe: superblock, flag: 'boot',partition_type: EF00, preserve: false,  grub_device: true, id: part-grub }
    #- { type: partition, device: disk-raid, size: 32GB, wipe: superblock, flag: 'swap', preserve: false, id: part-swap }
    #- { type: partition, device: disk-raid, size: 256GB, wipe: superblock, preserve: false,  id: part-home }
    #- { type: partition, device: disk-raid, size: -1, wipe: superblock, preserve: false,  id: part-data }
    #- { type: partition, device: disk-raid-grub, size: 1024MB, wipe: superblock, flag: 'boot',partition_type: EF00, preserve: false,  grub_device: true, id: part-raid-grub }
    #- { type: partition, device: disk-raid-grub, size: 1024MB, wipe: superblock, flag: 'boot', preserve: false,  grub_device: true, id: part-raid-grub }
    #- { type: partition, device: disk-raid-swap, size: 32GB, wipe: superblock, flag: 'swap', preserve: false, id: part-raid-swap }
    - { type: partition, device: disk-raid-home, size: 256GB, wipe: superblock, preserve: false,  id: part-raid-home }
    - { type: partition, device: disk-raid-data, size: -1, wipe: superblock, preserve: false,  id: part-raid-data }
    #
    - { type: format, volume: part-grub, fstype: fat32, preserve: false, id: format-grub }
    # { type: format, volume: part2-grub, fstype: fat32, preserve: false, id: format2-grub }
    #- { type: format, volume: part-raid-swap, fstype: swap, preserve: false, id: format-swap }
    - { type: format, volume: part-raid-home, fstype: btrfs, preserve: false, id: format-home }
    - { type: format, volume: part-raid-data, fstype: btrfs, preserve: false, id: format-data }
    - { type: mount, path: '/boot/efi', device: format-grub, id: mount-grub }
    #- { type: mount, path: '/boot/efi', device: format2-grub, id: mount2-grub }
    #- { type: mount, path: '', device: format-swap, id: mount-swap }
    - { type: mount, path: '/', device: format-home, id: mount-home }
    - { type: mount, path: '/data', device: format-data, id: mount-data }

    # - { type: raid, name: md1, raidlevel: 1, devices: [ part-swap, part2-swap ], spare_devices: [], preserve: false, wipe: superblock, ptable: gpt, id: raid-swap }
    # - { type: partition, device: raid-swap, size: 32GB, wipe: superblock, flag: 'swap', number: 2, preserve: false, id: part-raid-swap }
    # - { type: format, volume: part-raid-swap, fstype: swap, preserve:false, id:format-swap }
    # - { ptable: gpt, path: /dev/nvme1n1, wipe: superblock-recursive, preserve: false, name: '', grub_device: true, type: disk, id: disk-nvme1n1 }
    # - { device: disk-nvme1n1, flag: bios_grub, id: partition-1, number: 1, preserve: false, size: 1048576, type: partition }
    # - { device: disk-nvme1n1, size: 1024M, wipe: superblock, flag: boot, number: 2, preserve: false, grub_device: true, type: partition, id: partition-3 }
    # - { device: disk-nvme1n1, size: 32G, wipe: superblock, flag: '', number: 3, preserve: false, grub_device: false, type: partition, id: partition-5 }
    # - { device: disk-nvme1n1, size: 256G, wipe: superblock, flag: '', number: 4, preserve: false, grub_device: false, type: partition, id: partition-7 }
    #- { name: md0, raidlevel: raid1, devices: [ partition-2, partition-3 ], spare_devices: [], preserve: false, wipe: superblock, ptable: gpt, type: raid, id: raid-0 }
    #- { device: raid-0, size: 1024M, wipe: superblock, flag: 'boot', number: 1, preserve: false, grub_device: true, type: partition, id: partition-8 }
    #- { fstype: fat32, volume: partition-8, preserve: false, type: format, id: format-3 }
    
    # - { name: md1, raidlevel: raid1, devices: [ partition-4, partition-5 ], spare_devices: [], preserve: false, wipe: superblock, ptable: gpt, type: raid, id: raid-1 }
    # - { device: raid-1, size: 32G, wipe: superblock, flag: swap, number: 2, preserve: false, grub_device: false, type: format, id: partition-9}
    # - { fstype: swap, volume: partition-9, preserve: false, type: format, id: format-4 }
    # - { type: mount, path: '', device: format-4, id: mount-3 }
    # - { name: md2, raidlevel: raid1, devices: [ partition-6, partition-7 ], spare_devices: [], preserve: false, wipe: superblock, ptable: gpt, type: raid, id: raid-2 }
    # - { device: raid-2, size: 256G, wipe: superblock, flag: '', number: 3, preserve: false, grub_device: false, type: partition, id: partition-10 }
    # - { fstype: btrfs, volume: partition-10, preserve: false, type: format, id: format-5 }
    # - { path: /, device: format-5, type: mount, id: mount-4 }
```

---

### Post by TheFu on 2024-04-17
I've never successfully used automatic installations to setup storage.  I do pre-configure storage and LVM before I get to the installer "Do something else" disk setup options.  The interactive installer is terrible for customizing RAID and/or LVM storage.  They should just copy the GUI that CentOS used 10 yrs ago.  That was workable.  

I prefer to use mdadm+LVM for data storage, just not for the OS.

For RAID1 with the OS storage, I've never had luck with software RAID that wasn't using LVM, not mdadm.  In the installer, have it setup LVM for the entire disk during the install as the first step.

Post-install, resize the default LVs (root/swap_1) to be smaller, more reasonable, and create new LVs for /var/, /home/, /tmp/ to meet your needs, then add the 2nd PV to the VG and use lvchange to switch from simple LV to RAID1 LV.  You'll end up with something that looks like this:
```
$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME                      TYPE FSTYPE       SIZE FSAVAIL FSUSE% LABEL MOUNTPOINT
vda                       disk               15G                      
&#9500;&#9472;vda1                    part                1M                      
&#9500;&#9472;vda2                    part ext4         768M  397.5M    39%       /boot
&#9492;&#9472;vda3                    part LVM2_member 13.2G                      
  &#9500;&#9472;vg--00-lv--0_rmeta_0  lvm                 4M                      
  &#9474; &#9492;&#9472;vg--00-lv--0        lvm  ext4          10G    4.7G    46%       /
  &#9500;&#9472;vg--00-lv--0_rimage_0 lvm                10G                      
  &#9474; &#9492;&#9472;vg--00-lv--0        lvm  ext4          10G    4.7G    46%       /
  &#9492;&#9472;vg--00-lv--swap       lvm  swap           1G                      [SWAP]
vdb                       disk               15G                      
&#9500;&#9472;vdb1                    part                1M                      
&#9500;&#9472;vdb2                    part              768M                      
&#9492;&#9472;vdb3                    part LVM2_member 13.2G                      
  &#9500;&#9472;vg--00-lv--0_rmeta_1  lvm                 4M                      
  &#9474; &#9492;&#9472;vg--00-lv--0        lvm  ext4          10G    4.7G    46%       /
  &#9492;&#9472;vg--00-lv--0_rimage_1 lvm                10G                      
    &#9492;&#9472;vg--00-lv--0        lvm  ext4          10G    4.7G    46%       /
```
That was a play VM to test the idea. It works.  I didn't give the VM much storage, so the "root" LV wasn't 500GB and an abomination.

I find the way that LVM does RAID to be a bit ugly, but it definitely works.  On my home systems, I don't bother with RAID1 for the OS.  Failures of SSDs are very infrequent, especially if enterprise SSDs are used.  At a storage conference, I spoke with an enterprise storage SE.  He said that enterprises were still buying SSD-RAID setups, but that it was a waste of money for almost all of them. The SSDs they sell had expected lifespans of over 10 yrs and none had failed when delivered to a customer's site with their other equipment.  Obviously, he was selling high-end storage solutions and not the consumer SSD you and I would have at home.  I don't need HA at home. 1-2 hours of downtime is fine. Plus, we need good backups anyway, so if my money is going to the storage, I'm going to ensure I have great backups to HDD storage before I even think of RAID1.

Last year, I had a system with RAID! HDDs.  When I upgraded to a new system with an SSD, I specifically decided not to RAID it. After the first 30 days without any issues, I started relaxing.  In consumer SSDs, failures seem to happen when first installed.  Just be certain to watch the TBW numbers, so you aren't caught with overused storage that fails.  Any stick with quality SSD vendors, but that should go without saying.

/boot/ isn't RAID for good reason. You can manually rsync it and /boot/efi to the storage on the 2nd disk, but only 1 can be seen during boot when using SW-RAID.  If you want/need full RAID for everything, then getting a quality LSI-RAID HBA would be best.  No way should you be tempted to use Fake-RAID built into a motherboard. You already know this.

I know the 20.04 installer forced me to have an extra partition that is useless for an EFI boot. Here's what that looks like:
```
nvme0n1              disk                   931.5G                               
**&#9500;&#9472;nvme0n1p1          part  ext2                 1M                               **
&#9500;&#9472;nvme0n1p2          part  vfat                50M   43.9M    12%                /boot/efi
&#9500;&#9472;nvme0n1p3          part  ext4               700M  339.8M    42%                /boot
&#9492;&#9472;nvme0n1p4          part  LVM2_member      930.8G                               
  &#9500;&#9472;vg01-swap01      lvm   swap               4.1G                               [SWAP]
  &#9500;&#9472;vg01-root01      lvm   ext4                35G   24.8G    22%                /
  &#9500;&#9472;vg01-var01       lvm   ext4                20G     14G    23%                /var
  &#9500;&#9472;vg01-tmp01       lvm   ext4                 4G    3.6G     1% tmp01          /tmp
  &#9500;&#9472;vg01-home01      lvm   ext4                20G   10.1G    44% home01         /home

```
nvme0n1p1 is useless, but I wasn't able to get the installation to work without it.  In a prior 20.04 install (about 18 months earlier), it wasn't needed.  The motherboards and BIOS versions are identical for both systems, so I think the installer changed.  Also, /boot/ wasn't allowed to be ext2 anymore. The installer forced ext4.  I don't see the point of having /boot/ journalled, but they know best.  A few months ago, I saw that ext2 is being deprecated.

Hope all this helps with your choices.  Perhaps it won't. Sorry.

---

