---
title: "Mount encrypted secondary drives at boot time with prompt for password"
date: 2017-10-21
forum: Installation &amp; Upgrades
---

### Post by blm14 on 2017-10-21
Had a machine running 16.04 and for various reasons (space, drive may be dying, no TRIM support) I am replacing its boot SSD. I installed a new SSD and still have the old one available and attached via USB.

There are two other magnetic 1TB drives installed. They are both encrypted using dmCrypt. I have installed a new instance of 16.04 on the new SSD, and other than installing packages the only change I have made is the following one to /etc/default/grub

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

is now

```

GRUB_CMDLINE_LINUX_DEFAULT=""

```

and run update-grub after that change.

The way I had it set up before, one of the magnetic drives would mount at boot to /storage and the other one to /home2. Password entry was required at boot time for both drives separately, and boot would not continue (and X not start) until they had mounted properly. I wish to accomplish this again but can't seem to get it working.

Old /etc/fstab, from the installation that was working the way I want:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/sdb5_crypt /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=78a315a8-099a-4cfc-895f-b682f463d208 /boot           ext2    defaults        0       2
/dev/disk/by-uuid/be8df079-b2a7-49f8-9973-a59e54134a9e /storage auto nosuid,nodev,x-gvfs-show 0 0
/dev/disk/by-uuid/1575a1e8-c7d9-4f21-b089-4154c32cc272 /home2 auto nosuid,nodev,x-gvfs-show 0 0
#/dev/disk/by-uuid/c57824f2-966f-4186-b1b2-9bffacfe828b /external auto nosuid,nodev,x-gvfs-show 0 0

```

old /etc/crypttab, from same:

```

sdb5_crypt UUID=867ca601-524e-47c8-8a0c-2fdf374c3456 none luks,discard
luks-019940c1-e6ec-4142-871a-1601cf30ac00 UUID=be8df079-b2a7-49f8-9973-a59e54134a9e none nofail,bootwait
luks-ac8536c7-afa9-4590-baca-1f66aac72dec UUID=1575a1e8-c7d9-4f21-b089-4154c32cc272 none nofail,bootwait

```

If I open the "disks" utility and unlock the two partitions that I want, output of lsblk -o +UUID is:

```

NAME                     MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT                                        UUID
sdf                        8:80   0 931.5G  0 disk                                                    
&#9492;&#9472;sdf1                     8:81   0 931.5G  0 part                                                    019940c1-e6ec-4142-871a-1601cf30ac00
  &#9492;&#9472;luks-019940c1-e6ec-4142-871a-1601cf30ac00
                         253:5    0 931.5G  0 crypt                                                   be8df079-b2a7-49f8-9973-a59e54134a9e
sdd                        8:48   0 238.5G  0 disk                                                    
&#9500;&#9472;sdd2                     8:50   0     1K  0 part                                                    
&#9500;&#9472;sdd5                     8:53   0   238G  0 part                                                    83c3b28b-38ec-46ab-b780-4696f0b56efa
&#9474; &#9492;&#9472;sda5_crypt           253:0    0   238G  0 crypt                                                   eYmkuj-GIy8-oJqy-vya8-4uuA-nt83-Ei5edn
&#9474;   &#9500;&#9472;ubuntu--vg-root    253:1    0   174G  0 lvm   /                                                 0dd8e345-79d7-43bb-9f32-d651548d46ec
&#9474;   &#9492;&#9472;ubuntu--vg-swap_1  253:2    0    64G  0 lvm   [SWAP]                                            e1c16e2f-75a8-48a4-a262-a4c82d0d7ebf
&#9492;&#9472;sdd1                     8:49   0   487M  0 part  /boot                                             69406eca-de40-4915-aaca-a7cffbc4099a
sde                        8:64   0 931.5G  0 disk                                                    
&#9500;&#9472;sde2                     8:66   0     1K  0 part                                                    
&#9500;&#9472;sde5                     8:69   0 871.9G  0 part                                                    ac8536c7-afa9-4590-baca-1f66aac72dec
&#9474; &#9492;&#9472;luks-ac8536c7-afa9-4590-baca-1f66aac72dec
&#9474;                        253:4    0 871.9G  0 crypt                                                   1575a1e8-c7d9-4f21-b089-4154c32cc272
&#9492;&#9472;sde1                     8:65   0  59.6G  0 part                                                    b7186175-26b0-4e6c-903e-4cecf1097716
sda                        8:0    0 238.5G  0 disk                                                    
&#9500;&#9472;sda2                     8:2    0     1K  0 part                                                    
&#9500;&#9472;sda5                     8:5    0 234.6G  0 part                                                    867ca601-524e-47c8-8a0c-2fdf374c3456
&#9474; &#9492;&#9472;luks-867ca601-524e-47c8-8a0c-2fdf374c3456
&#9474;                        253:3    0 234.6G  0 crypt /media/blm14/5ff36980-711e-4d2c-85fc-5af244e96b60 5ff36980-711e-4d2c-85fc-5af244e96b60
&#9492;&#9472;sda1                     8:1    0   3.9G  0 part  /media/blm14/78a315a8-099a-4cfc-895f-b682f463d208 78a315a8-099a-4cfc-895f-b682f463d208

```

So, the boot disk is sdd, the old SSD boot drive is sda, sdf1's encrypted volume is what I want as /storage, and sde5's encrypted volume is what I want to be /home2

From the current install I see that the UUIDs of the encrypted volumes have not changed, nor have the disk-by-UUID alias designations. 

If I copy the two lines referring to /home2 and /storage into the new installation's fstab and cryttab (respectively) and run update-initramfs -u -k all, instead of being prompted for the passwords at boot time with a wait for input like before, now I get that error message about "a start job is waiting" for a minute and thirty seconds, at which point I am prompted to drop into single user mode.

Any ideas would be greatly appreciated - this is my primary workstation at my office. The machine itself is a Dell Precision T7610. Can provide more information on the hardware if needed. I am going to try and reply to this message after another reboot with a pastebin of dmesg from a failed boot.

---

### Post by blm14 on 2017-10-21
dmesg, from a failed boot: [http://paste.ubuntu.com/25787808/](http://paste.ubuntu.com/25787808/)

The system boots normally when I comment out the two lines from fstab and crypttab...

---

### Post by blm14 on 2017-10-21
interesting finding - the old install was using kernel 4.4.0-97 and the new one is using 4.10.0-37. Not sure if that would matter.

---

### Post by blm14 on 2017-10-21
OK, fixed. Needed to specify the correct UUIDs in the right places. /etc/fstab entries for the two external drives now:

```

UUID=be8df079-b2a7-49f8-9973-a59e54134a9e /storage auto nosuid,nodev,x-gvfs-show 0 0
UUID=1575a1e8-c7d9-4f21-b089-4154c32cc272 /home2 auto nosuid,nodev,x-gvfs-show 0 0

```

/etc/crypttab relevant entries:

```

sdd1 UUID=019940c1-e6ec-4142-871a-1601cf30ac00 none nofail,bootwait
sdc5 UUID=ac8536c7-afa9-4590-baca-1f66aac72dec none nofail,bootwait

```

So crypttab specifies the UUIDs of the partition that contains the encrypted volume and fstab contains the UUIDs of the encrypted volume specified. bootwait forces the kernel to mount those drives before the boot process finishes and I have to enter the passwords at boot. Yay!

---

