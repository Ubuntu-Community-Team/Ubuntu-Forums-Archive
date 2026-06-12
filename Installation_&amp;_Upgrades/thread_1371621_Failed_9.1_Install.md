---
title: "Failed 9.1 Install"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by gkaucher on 2010-01-03
About a year ago I was able to successfully turn my laptop into a Windows XP / Ubuntu Dual Boot system without really knowing what I did. 

Recently I was given a Dell Dimension 4700 desktop running XP, and I figured I would do the same thing using a System Rescue CD and a CD that I burned from a recently downloaded Ubuntu 9.1 iso.

So I restored XP using the F11 Restore option on the Dell, and partitioned things in accordance with some instructions that I found online, and then proceeded to install Ubuntu 9.1. Afterwards, I was able to boot to XP, but not to Ubuntu. I suspect that Grub never installed or something.  I didn't really care if I had XP or not, so I then tried to gpart the whole drive for just Ubuntu, so there would be a bootable ext4 partiton for Ubuntu 9.1 and a small 2GB swap drive. Either the partitioning or the install was unsuccessful. I am not knowledgable enough to know. At this point I am unable to "see" any partitions on the HDD (160GB Maxtor DiamondMax Plus 9 serial ATA) using gpart, so I am lost.

My partitions are of the /dev/sda type. I would really appreciate if someone could give me the terminal commands needed to assess/repair things and I will post.

Thanks,
Gary

---

### Post by running_rabbit07 on 2010-01-03
Sounds like a reinstall. Should try 9.10 though. I heard the January 09 Edition isn't that great.

---

### Post by gkaucher on 2010-01-03
Sorry about that! I meant 9.10

Gary

---

### Post by gkaucher on 2010-01-03
Here are the results of the Boot Info Summary. I can get into the Terminal on the Ubuntu Live CD. 

Looks like I need a bootloader. What commmands from the terminal would make that possible?

Thanks,
Gary


```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


blkid -c /dev/null: ____________________________________________________________


=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory[CODE][CODE][CODE][CODE]
```[/CODE][/CODE][/CODE][/CODE]

---

### Post by running_rabbit07 on 2010-01-03
Hakuna Matada. It does look like the partition table is bad. I don't know of any way to bring them back, if at all possible. If you can, you may want to download and burn the GParted LiveCD and see if it has any functions that can fix the partitions, but it is doubtful. Godd luck.:)

---

