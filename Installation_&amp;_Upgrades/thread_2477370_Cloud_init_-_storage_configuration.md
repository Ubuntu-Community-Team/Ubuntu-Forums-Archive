---
title: "Cloud init - storage configuration"
date: 2022-07-22
forum: Installation &amp; Upgrades
---

### Post by hellboy11 on 2022-07-22
[FONT=-apple-system][COLOR=#232629]Hi everyone, ( I am new member :) )[/COLOR][/FONT]
[FONT=-apple-system][COLOR=#232629]I have two problem in the section of the storage (user-data file).
1. When I try to increase the /dev/sda2 with Gparted I cannot do it because the creation of the volume boot. ( see picture bellow, P.S I need 2 giga of boot) 
2. In addition, I am trying to automatically allocate free space to / (root) on the installation.[/COLOR][/FONT]


[IMG]https://i.stack.imgur.com/xsso6.png[/IMG]


[FONT=-apple-system][COLOR=#232629]I am adding the section of the storage after a lot of changes.

 [/COLOR][/FONT]who can assist please :\


storage:
   config:
   - ptable: gpt
     path: /dev/sda
     wipe: superblock-recursive
     preserve: false
     name: ''
     grub_device: true
     type: disk
     id: disk-sda
   - device: disk-sda
     size: 1048576
     flag: bios_grub
     number: 1
     preserve: false
     grub_device: false
     type: partition
     id: partition-0
   - {device: disk-sda, size: 536870912, wipe: superblock, flag: boot, number: 2,
     preserve: false, grub_device: true, type: partition, id: disk-sda2}
   - {fstype: ext4, volume: partition-1, preserve: false, type: format, id: format-2}  
   - device: disk-sda
     size: 100%
     wipe: superblock
     flag: ''
     number: 2
     preserve: false
     grub_device: false
     type: partition
     id: partition-1
   - name: vg0
     devices:
     - partition-1
     preserve: false
     type: lvm_volgroup
     id: lvm_volgroup-0
   - device: disk-sda
     size: -1
     wipe: superblock
     flag: ''
     number: 3
     preserve: false
     grub_device: false
     type: partition
     id: partition-3
   - fstype: ext4
     volume: partition-3
     preserve: false
     type: format
     id: format-0
   - name: lv-swap
     volgroup: lvm_volgroup-0
     size: 4294967296B
     wipe: superblock
     preserve: false
     type: lvm_partition
     id: lvm_partition-0
   - name: lv-root
     volgroup: lvm_volgroup-0
     size: -1
     wipe: superblock
     preserve: false
     type: lvm_partition
     id: lvm_partition-1
   - fstype: ext4
     volume: lvm_partition-1
     preserve: false
     type: format
     id: format-3
   - path: /
     device: format-3
     type: mount
     id: mount-3
   - fstype: swap
     volume: lvm_partition-0
     preserve: false
     type: format
     id: format-4
   - path: ''
     device: format-4
     type: mount
     id: mount-4
   - path: /boot
     device: format-0
     type: mount
     id: mount-0

---

### Post by TheFu on 2022-07-24
I can't understand your post due to terrible formatting.  Please, please, please wrap things entered into and output from any terminal in 'forum code tags'. That's available in the "Adv Reply" ... or once you learn the tags, you can manually enter it.

You are using LVM.  That is an enterprise volume manager. That's good and bad.  While the current layout isn't ideal, thanks to LVM, there are many, many, ways to get around the issue.  

OTOH, if you want to learn to do this stuff "correctly", then moving /boot/ to a new partition placed elsewhere is needed.  If it were me, and I'm lazy, I've move /boot to be 600MB at the far end of the storage.  But if you aren't good-to-great at dealing with boot problems, moving /boot (the partition) will likely break the ability to boot and cause some other issues which won't be fun to solve.

If you don't know LVM, you should read up on it before doing anything else.  Also, you should create a Try Ubuntu flash drive (installation flash drive) with the same release as what you already have installed. You will need this to do many things with the existing storage, as it is.
a) make a try ubuntu flash drive that you 100% know it works
b) backup anything you don't want to lose. I wouldn't worry about this if you understand LVM, partitions, booting under Linux, but if you do not, the risk is high that a wrong choice will accidentally wipe something very important.
c) Read up on LVM.  LVM is the same on Ubuntu, Servers, Fedora, SuSE, Mint, Debian, ... all Linux distros. LVM is LVM, so you don't need to worry if the tutorial/training that you find is for a different OS too much.  There is no GUI for LVM creation and management. Don't even bother looking.

Conceptually, the different solution options aren't hard to understand.  I see 3 major choices, though there are 500+ choices.   Plus, I'd never make the root LV larger than about 35GB in size.  Keep the OS separate from other things stored on the system. It makes for cleaner backups, better OS release upgrades with less risk and can aid with system security by using specific, restricted, mount options for other partitions/logical volumes.

It would help me to see the output from a few commands to get the truth about the storage on the system.  The commands to run:
```
sudo parted -lm
sudo pvs
sudo vgs
sudo lvs
```
The command and the output need to be posted here wrapped in 'code tags', so it is readable. The output uses columns and without that being perfectly retained, it is impossible to see the necessary information.

That's probably enough for now.

---

