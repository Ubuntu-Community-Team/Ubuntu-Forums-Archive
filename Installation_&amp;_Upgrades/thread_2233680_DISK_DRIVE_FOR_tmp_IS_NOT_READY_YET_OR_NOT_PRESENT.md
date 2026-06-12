---
title: "DISK DRIVE FOR /tmp IS NOT READY YET OR NOT PRESENT"
date: 2014-07-10
forum: Installation &amp; Upgrades
---

### Post by jesse21 on 2014-07-10
how do i get passed this and finish installing my ubuntu ?? i partitioned my hard drive with windows 8.1. windows loads fine, ubuntu not so much. ive read that this is some kinda BUG and can be fixed somehow but i do not know how. I have tried
Sudo mv /tmp /tmp_old
with the response - Can not move /tmp Read-only file-system
H E L P !??!?

---

### Post by slooksterpsv on 2014-07-10
Could you paste the output of the following commands:
```

cat /etc/fstab
mount
df

```
So you've installed Ubuntu or are trying to install Ubuntu? Did you create a partition for /tmp?

---

### Post by jesse21 on 2014-07-12
someone else partitioned my hard drive. not sure exactly what he did but I paid a professional. Fat32 partition sticks in my head for some reason. he did not however install ubuntu. i did that after he left. it installed, then rebooted and said it was Finishing up installation then starts to load into Ubuntu and then says Serious errors were found while checking the disk drive for /.     I   to ignore, S  to skip, M  for manual recovery.    When i ignore or skip,   it says  - Disk drive for /tmp is not ready yet or not present....

---

### Post by jesse21 on 2014-07-12
in windows, under Computer Management it showed the following
                                               Layout                  type             file system           status
C: (windows)             simple                   basic              NTFS                 healthy
system reserved    simple                  basic              NTFS                  healthy
D: (ubuntu)                   simple                    basic             NTFS                  healthy

---

### Post by jesse21 on 2014-07-12
Im not sure how to take screen shots but i took a picture and rewrote it here

/host/ubuntu/disks/root.disk /             ext4                loop,errors=remount-ro 0         1
/host/ubuntu/disks/swap.disk none       swap              loop,sw             0         0

/dev/loop2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda3 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/loop0 on /cdrom type iso9660 (ro,noatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=4042260k,nr_inodes=1010565,mode=775)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=817356k,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)

mount: warning: /etc/mtab is not writable (e.g. readonly filesystem)
                      its possible that information reported by mount(8) is not up to date. for actual information about system mount points check the /proc/mounts file


Filesystem       1K-blocks              used   available   use%   mounted on
/dev/loop2        29848536      3119404    25189856    12%       /
/dev/sda3        181184508   32809000    148375508    19%     /host
udev                 4043052             336     4042716      1%      /dev
tmpfs                 817356            1084      816272       1%     /run

---

### Post by jesse21 on 2014-07-12
in windows, under Computer Management it showed the following
                                Layout       type        filesystem status
C: (windows)          simple      basic    NTFS            healthy
system reserved    simple     basic    NTFS             healthy
D: (ubuntu)              simple     basic    NTFS             healthy 				&#65279;

---

### Post by ubfan1 on 2014-07-12
On the Ubuntu partition, you should have used the ext4 type filessystem instead of ntfs.  Also, you don't hve a swap partition, which is optional, but recommended.  You could just reinstall and select the "something else" choice, and change the filesystem and reformat the existing Ubuntu partition, or delete it, recreate it smaller, and also create a swap partition.  Likely, you have four primary partitions already, so what you need to do to make the swap (which will be the fifth), is to 1)delete the Ubuntu partition, 2)make the entire free space an extended partition, then add the logical Ubuntu partition (smaller) and a logical swap partition.

---

### Post by jesse21 on 2014-07-12
i saw no 'something else' option while reinstalling but i have relayed your suggestion to my computer guy to see what he can do. thanks !

---

### Post by yancek on 2014-07-12
> Sudo mv /tmp /tmp_old
with the response - Can not move /tmp Read-only file-system

Is "Sudo" above a typo?  Because it needs to be all lower case.  Also, you get that error because you are using a Live CD on a flash drive and a Live CD by definition is a "read-only" filesystem.  You can do some things and make some changes but all will be lost on reboot and that is the way it is supposed to work.

 > Serious errors were found while checking the disk drive for /.     I   to ignore, S  to skip, M  for manual recovery

I see that message on occasion but, it is never for the root partition which contains the filesystems as in your case.  If it were some other data partition for instance, you could tap the 'S' key and continue booting successfully.  The "/" forward slash in the message indicates the root of the filesystem. 

> D: (ubuntu)                   simple                    basic             NTFS                  healthy 		

As pointed out above, that absolutely will not work.  You need a Linux filesystem just as you need a windows filesystem to install windows.

When you booted to install, which options did you see in the first Installation Type windows.  There should be a minimum of 2 but often as many as 4 or 5.  If you didn't see the 'Something Else' option it probably because you didn't look or you may not remember.  That should always be there.  It's a term only used on recent Ubuntu versions which previously used Manual or Expert as an option.  If you chose 'Install Alongside', that should have worked.

Additional complicating factors in your case are that you are using windows 8 so that you have to deal with Secure Boot, Fast Boot and UEFI instead of the standard BIOS.

To see if Ubuntu is installed and what partition it is on, you could boot the Ubuntu flash and open a terminal by simultaneously holding down the Ctrl+Alt+t keys and entering:  sudo fdisk -l(Lower Case Letter L in the command).  You could also google from the Ubuntu flash, bootinfoscript, go to the site and download and run it and post the output which gives a lot of detail on your drives/partitions, boot files and other relevant information.

---

### Post by ubfan1 on 2014-07-12
Oh, with Windows 8.1, your disk partitioning is GPT, not MSDOS, so no extended partition business is needed, just add the partitions you want.

---

