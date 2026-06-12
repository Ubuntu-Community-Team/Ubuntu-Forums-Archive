---
title: "Can't increase size of /boot when asked by upgrade program"
date: 2015-09-03
forum: Installation &amp; Upgrades
---

### Post by Dave_Mann on 2015-09-03
The Software Updater application ran ust now and after downloading everything, I got this message:

The upgrade needs a total of 96.0 M free space on disk '/boot'. Please free at least an additional 12.9 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

GParted doesn't see to be able to change sizes of /dev/sda  /dev/sda is a 1TB drive and consists of: 

[ATTACH=CONFIG]264215[/ATTACH]

Now, when I went into Gparted and dismounted /dev/sda1 (FAT32, 512MB) and /dev/sda2 (ext2, boot, 244MB) and left /dev/sba3 (lvm2pv, 930MB) the upgrade-update went through smoothly.

Why does this happen?

---

### Post by Bashing-om on 2015-09-03
Dave_Mann; Humm ..

Can not say why with unmounting the partitions, that the installer proceeded ... but but I do know that in choosing 'LVM' the system expects you to know how to deal with the /boot partition. By default the /boot partition is created with but a small value and one has to manage that partition.
What returns from terminal commands:
```

df -h
df -i
dpkg -l | grep linux-

```
I do expect we find that the /boot partition is full and we can expect to have to remove the old no-longer-needed kernels .

[INDENT][INDENT]all in the care and feeding
[INDENT][INDENT][INDENT]of your 'buntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ubfan1 on 2015-09-03
Because /boot is simply a directory on your root filesystem.  Normally, it's invisible since you mount the boot partition there.  By unmounting the partition, the available space in /boot is only limited by the space on the root filesystem (900G+), but when you reboot, any additions will not be seen, when the boot partition is mounted there.  You might need a boot partition for things like an encrypted root, or if your bios cannot reliably run a kernel from anywhere on the 1T disk, but normally, the volume group business is just another layer of complication most people can do without.

---

### Post by gordintoronto on 2015-09-04
Install Synaptic Package Manager.
Use Synaptic to completely remove all but the latest two kernels. (Three files each.)
Run: sudo update-grub

---

