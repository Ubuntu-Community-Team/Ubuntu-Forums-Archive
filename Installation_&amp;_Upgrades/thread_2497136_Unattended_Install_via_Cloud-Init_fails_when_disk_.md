---
title: "Unattended Install via Cloud-Init fails when disk already contains LVM"
date: 2024-04-24
forum: Installation &amp; Upgrades
---

### Post by miramind on 2024-04-24
Hey,

I am trying to automate the installation of Ubuntu 22 on Hardware Servers via network boot and cloud-init.

While configuring storage, the installation crashes, due to the following error:

```

Command: ['vgcreate', '--force', '--zero=y', '--yes', 'vg_system', '/dev/sda3']
Exit code: 3
Reason: -
Stdout: ''
Stderr:   /dev/vg_System: already exists in filesystem
             Run `vgcreate --help` for more information

```

I also (think I) understand, why this error pops up: The hard disk in that machine was used before and previously contained a VG with that name.

My Expectation would be, that during the disk setup, the installer will purge existing LVM configuration, but it seems like (as I create the partition table exactly like it was before) that the old VG survives.

This is the related cloud-init configuration:

```

  storage:
    version: 1
    config:
      - type: disk
        id: disk-sda
        ptable: gpt
        path: /dev/sda
        wipe: superblock-recursive
        grub_device: false
      - type: partition
        id: partition-sda1
        device: disk-sda
        size: 500M
        flag: boot
        grub_device: true
      - type: partition
        id: partition-sda2
        device: disk-sda
        size: 2G
      - type: partition
        id: partition-sda3
        device: disk-sda
        wipe: superblock
        size: -1
        flag: lvm
      - type: lvm_volgroup
        name: vg_system
        id: vg_system
        preserve: false
        devices: [partition-sda3]
      - type: lvm_partition
        id: lv_swap
        volgroup: vg_system
        name: lv_swap
        size: 4G
      - type: lvm_partition
        id: lv_root
        volgroup: vg_system
        name: lv_root
        size: 10G
      - type: lvm_partition
        id: lv_var
        volgroup: vg_system
        name: lv_var
        size: 10G

```

---

### Post by MAFoElffen on 2024-04-24
What if you add these as early commands?
```

sudo blkdiscard -f /dev/sda
sudo wipefs -a /dev/sda
sudo sgdisk --zap-all /dev/sda

```
This is what I have to do if disks have had mdadm or ZFS on them previously to zero them...

I'm thinking that those types of defines (including LVM2 def's), exist on the disk somewhere outside of the confines of the partition tables. Although I have not found documentation telling me where those are stored 'exactly'. (If someone knows, please point me to it, for my own FYI...) Those commands seem to take care of zeroing those.

---

### Post by miramind on 2024-04-24
Awesome, that worked for me.
I sadly can't help you about where exactly lvm-related definitions are stored either :/

---

