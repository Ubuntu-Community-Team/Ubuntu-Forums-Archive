---
title: "Server won't boot (fstab or superblock problem?)"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by allenhiltz on 2012-10-13
[B]Hello. I have a server that won't boot despite my numerous attempts to fix it. I tried my own solutions combined with several hours of Google's solutions. Obviously none of these solutions worked, so I wanted to present my problems to the Linux community to see what you have to say.

The server will not boot. At first it gave me an error about the fstab. I went into single user mode, to examine the contents of that file and discovered it was empty! A Google result informed my that the mtab file in dev/etc was compatible with the fstab file. So I copied its contents into the empty fstab file. It looked like this:[/B]


/dev/mapper/VolGroup00-LogVol00 / ext3 rw 0 0
none /proc proc rw 0 0
none /sys sysfs rw 0 0
none /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/sda1 /boot ext3 rw 0 0
none dev/shm tmpfs rw 0 0
/dev/sda2 /var ext3 rw 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
sunrpc /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0


**It still was not booting so I tried changing some of the attributes in that file (like changing rw to defaults, or changing where it mounts) But all I get is this:**


Checking root filesystem
fsck.ext2: /:
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 file system (and not swap or ufs or something else, then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

Is a directory while trying to open /
                                                                           [FAILED]
*** An error occurred during the file system check.
*** Dropping you to a shell: the system will reboot
*** when you leave the shell.
Give root password for maintenace
(or type Control-D to continue):

**I feel like my server has two porblems, an incorrect fstab file and a corrupt superblock. Also, I tried to restore the superblock from another, but that did not work either. I know basically what an fstab file should look like, but I don't know what the EXACT contents of mine should be. Can anyone tell me exactly what my fstab file should have in it? Below is some additional information that may help**

(Repair filesystem) 10 # fdisk -l

Disk /dev/sda: 72.7 GB, 72729231360 bytes
255 heads, 63 sectors/tracks, 8842 cylinders
Units = cylinders of 16065 * 512 = 8225280

   Device     Boot     Start     End     Blocks         Id     System
/dev/sda1     *          1          13       104391        83     Linux
/dev/sda2                14         535     4192965      83     Linux
/dev/sda3                536       8842   66725977+   8e     Linux LVM

**I hope somebody has some ideas and thanks in advance for any assistance.**

---

### Post by darkod on 2012-10-13
Have you tried running a fsck on the root in the LVM? Not sure if it can fix any problems with the superblock or not, but it's worth the shot I guess.

In order to be able to see the LVM from live mode, you need to add the lvm2 package first and activate it. Note that since this is inside live mode you have to do it every time after you restart in live mode.

```
sudo apt-get install lvm2
sudo vgchange -ay
```

That should display message about the logical volumes being activated. The root LV should be something like /dev/VolGroup00/LogVol00.

After it's activated try the:
```
sudo fsck /dev/VolGroup00/LogVol00
```

See how that goes.

If that manages to fix any superblock or other issues, creating a new fstab should be easy. According to your setup, the /etc/fstab should look something like:
```
/dev/VolGroup00/LogVol00 / ext3 errors=remount-ro 0 1
/dev/sda1 /boot ext3 defaults 0 0
/dev/sda2 /var ext3 defaults 0 0
```

The above fstab would be my first bet.

---

### Post by allenhiltz on 2012-10-15
Thanks, darkod! I'll give that a try and post the results.

---

### Post by allenhiltz on 2012-10-22
So apparently the HDD had some severe corruption. Even after restoring/repairing a superblock, most of the data was still unreadable. Thanks, but this system was begging for retirement anyway.

---

