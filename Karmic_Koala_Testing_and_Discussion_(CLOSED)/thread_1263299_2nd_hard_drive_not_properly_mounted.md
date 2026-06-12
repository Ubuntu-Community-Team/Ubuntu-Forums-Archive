---
title: "2nd hard drive not properly mounted?"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by henriquemaia on 2009-09-10
I have to hard drives on my computer. The main one is working ok under Karmic, but the 2nd one, where I keep most of my files, appears as having no files at all. If I start with the live CD (9.04) and mount that 2nd drive, the files are all there, everything's in place.

Any ideas about what's happening here?

---

### Post by cariboo on 2009-09-10
A little more info would be helpful, how is your second drive formatted? NTFS or ext3/4?

---

### Post by henriquemaia on 2009-09-10
Ah, of course.

ext3.

---

### Post by henriquemaia on 2009-09-12
Bump. Still no files on the second drive. On windows everything is ok. I've checked with parted, gpart, etc, and everything is also ok there, but no files shown in nautilus or the command line (ls). Now what? 

thanks

---

### Post by dinxter on 2009-09-12
what happens when you mount the drive from the command line? eg
$sudo mount /dev/sda1 /media/sda1
$ls -al /media/sda1
obviously with your own /dev/ and pre-existing directory

---

### Post by VMC on 2009-09-12
I'll assume on means inside your pc not usb. So whats the output of

```
sudo fdisk -l

```Also what does fsck think of that drive?

---

### Post by taavikko on 2009-09-12
> **VMC said:**
> I'll assume on means inside your pc not usb. So whats the output of

```
sudo fdisk -l

```Also what does fsck think of that drive?

fdisk will show usb-devices as well.

Me thinks that the partition is mounted wrongly, 
Output of "mount" and "cat /etc/fstab" is needed for more details.

---

### Post by henriquemaia on 2009-09-15
> **VMC said:**
> I'll assume on means inside your pc not usb. So whats the output of

```
sudo fdisk -l

```Also what does fsck think of that drive?

Here's the result:

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8b7f8b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10011    80413326    f  W95 Ext'd (LBA)
/dev/sdb5               1       10011    80413294+  83  Linux

[QUOTE=dinxter]what happens when you mount the drive from the command line? eg
$sudo mount /dev/sda1 /media/sda1
$ls -al /media/sda1
obviously with your own /dev/ and pre-existing directory[/quote]

It works! Something wrong with fstab or mounting that partition on boot?

Thanks.

---

### Post by henriquemaia on 2009-09-15
> **taavikko said:**
> fdisk will show usb-devices as well.

Me thinks that the partition is mounted wrongly, 
Output of "mount" and "cat /etc/fstab" is needed for more details.

Thanks for your suggestions. Here's the output of "mount":

mount
/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
/dev/sdb5 on /arquivo type ext3 (rw,relatime)
/dev/sda8 on /home type ext3 (rw,relatime)
/dev/sda7 on /usr type ext4 (rw,relatime)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/henriquemaia/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=henriquemaia)


And the /etc/fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=1066bfcc-cde8-4b71-8845-43b6e4a57000 /               ext4    relatime,errors=remount-ro 0       1
# /arquivo was on /dev/sdb5 during installation
/dev/sdb5 /arquivo        ext3    relatime        0       2
# /home was on /dev/sda8 during installation
UUID=33a2af3d-eb78-49d7-af1e-dc9460df974f /home           ext3    relatime        0       2
# /usr was on /dev/sda7 during installation
UUID=385b38c2-b813-4d11-9a59-a49c8fca81cf /usr            ext4    relatime        0       2
# /windows was on /dev/sda1 during installation
UUID=A2A0E0B1A0E08D5B /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=86a05713-eb94-4bd5-b2c5-e16d4f4e1bbb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by henriquemaia on 2009-10-02
Even after massive amounts of updates, the disk is still not being mounted. Any ideas how to overcome this? Thanks.

note: manual mounting works.

---

### Post by dinxter on 2009-10-02
whats the uuid of your partition ?

$ ls /dev/disk/by-uuid -l | grep sdX

(replace X with your actual partition)

compare this uuid with the one in your /etc/fstab

---

### Post by henriquemaia on 2009-10-06
> **dinxter said:**
> whats the uuid of your partition ?

$ ls /dev/disk/by-uuid -l | grep sdX

(replace X with your actual partition)

compare this uuid with the one in your /etc/fstab

Done that, everything is ok. But still no go. Upon boot, there's a fsck notification telling the drive is not ok, but I've already checked it and it's ok. Can't figure out why it's not mounting properly upon boot.

---

### Post by henriquemaia on 2009-10-21
Still no go. :)

Well, time to reinstall ubuntu with a proper beta (not upgraded)

---

