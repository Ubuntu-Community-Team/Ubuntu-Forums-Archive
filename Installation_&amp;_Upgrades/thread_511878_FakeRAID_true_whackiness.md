---
title: "FakeRAID true whackiness"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by jlintz on 2007-07-28
So I followed the fakeraid howto, got my install up and running fine.  Setup all my programs, copied my files over, yada yada.  Rebooted a couple of times, everything is fine.  I decided to change one of my partitions while I was in windows, rebooted, grub had an error.  Well duh I thought I just needed to fix what would be the new root partition in grub now.  I boot to a livecd, install dmraid and lvm support, mount my root partition and boot partition.  Fix grub and re-install it, reboot and everything is good with grub.   The next part is where it gets real whacky...

I boot into ubuntu and notice my dual screen setup is no longer gone and I have the default login screen... odd I think.  I login to Ubuntu with my username and pw, that works fine, and im presented with the default install desktop?!  I look in my home folder and everything is gone??!?  I dont know how to explain how this happened.  I'm in the livecd right now trying to figure out where all my files and settings went and how on earth they got reset to the default installation.  Anyone clue me in to how this could have possible happened before I go insane?:confused:

---

### Post by jlintz on 2007-07-28
Here is an output of my partitioning

root@ubuntu:/# fdisk -l /dev/mapper/nvidia_ajafeffc

Disk /dev/mapper/nvidia_ajafeffc: 320.0 GB, 320072932352 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_ajafeffc1   *           1        5099    40957686    7  HPFS/NTFS
/dev/mapper/nvidia_ajafeffc2            8925       14024    40965750   8e  Linux LVM
/dev/mapper/nvidia_ajafeffc3           14025       14033       72292+  83  Linux
/dev/mapper/nvidia_ajafeffc4           14034       38913   199848600    7  HPFS/NTFS


and I have an lvm volgroup at /dev/mapper/volgroup/root and /dev/mapper/volgroup/swap

---

### Post by jlintz on 2007-07-28
I just figured out what is going on.  Everytime I reboot, it's booting to a different harddrive in the mirror and its not mirroring properly.  Anyone know what I could have done wrong to cause this?  I am dual booting with windows also

---

