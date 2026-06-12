---
title: "Updated from 14.04 to 16.04 - Bug, PC half dead."
date: 2016-12-15
forum: Installation &amp; Upgrades
---

### Post by JorgeO on 2016-12-15
Hello,

PC is HP dv7, 16GB RAM, running smoothly w/ 14.04

After update, at every boot there were error messages (2 times) related to a crash in some 14.04 leftover file. For a good time I clicked on report problem to Canonical. Besides, the fan was running faster - and noisier.

After many Canonical updates and the problem wasn't solved, I decided to look for a solution in the WEB.

The one I applied was a 16.04 reinstall without reformatting any partition, it looked easy since I have separated root and Home partitions. Both problems were gone, but....

Now, the PC is half dead, I'm using the 16.04 in a flash drive since using the HD I can boot the PC but it won't acces (at boot) my original Home partition and Wifi is not working.

- There are 2 Home partitions, one very small and another, larger that is my original Home. It looks like all data is there.

- WiFi won't connect, even with my user name and SSID being shown correctly.

Thanks for your help!

---

### Post by ajgreeny on 2016-12-15
I suspect when you reinstalled you did not set the old /home partition as the new /home partition. I am assuming you used the "Something Else" option at partitioning stage or all your old files might be now lost.

Show us the terminal output of ```
mount
``` for a start to see if you now have a separate /home partition, which I don't think you have, and then the output of ```
sudo parted -l && sudo blkid -c /dev/null
``` which will tell us the partitions on disk and their UUIDs.

We should then be able to show you how to edit /etc/fstab to add the old /home partition to your new OS.

---

### Post by JorgeO on 2016-12-15
Thanks, ajgreeny

You're right, I used something else.

```

ubuntu@ubuntu:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8174692k,nr_inodes=2043673,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1637868k,mode=755)
/dev/sdc on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=36,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1637868k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sdb3 on /media/ubuntu/Home type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb1 on /media/ubuntu/928df496-243c-4891-a553-c6cc04b882d6 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)                                                 



```

AS I've stated in my question, there's a root and a Home partition and I can read files in the old home directory.

```

ubuntu@ubuntu:~$ sudo parted -l && sudo blkid -c /dev/null
Model: ATA ST9750420AS (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      210MB   55.3GB  55.0GB  primary  ext4         boot
 2      55.3GB  750GB   695GB   primary  ext4


Model: ATA ST9750420AS (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  42.8GB  42.8GB  primary  ext4         boot
 3      42.8GB  157GB   115GB   primary  ext4
 2      157GB   750GB   593GB   primary  ext4


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel?                                                            



```

As you can see, there are 2 HD's in the PC. First one used as boot, Vmware for a windows install and backup and storage.

Second one was the Ubuntu one, 42.8 GB was root, 115GB was Home, the rest is just storage area.

---

### Post by ajgreeny on 2016-12-15
> **JorgeO said:**
> Thanks, ajgreeny

You're right, I used something else.

```

ubuntu@ubuntu:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8174692k,nr_inodes=2043673,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1637868k,mode=755)
/dev/sdc on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=36,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1637868k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sdb3 on /media/ubuntu/Home type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb1 on /media/ubuntu/928df496-243c-4891-a553-c6cc04b882d6 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)                                                 



```

AS I've stated in my question, there's a root and a Home partition and I can read files in the old home directory.

```

ubuntu@ubuntu:~$ sudo parted -l && sudo blkid -c /dev/null
Model: ATA ST9750420AS (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      210MB   55.3GB  55.0GB  primary  ext4         boot
 2      55.3GB  750GB   695GB   primary  ext4


Model: ATA ST9750420AS (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  42.8GB  42.8GB  primary  ext4         boot
 3      42.8GB  157GB   115GB   primary  ext4
 2      157GB   750GB   593GB   primary  ext4


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel?                                                            



```

As you can see, there are 2 HD's in the PC. First one used as boot, Vmware for a windows install and backup and storage.

Second one was the Ubuntu one, 42.8 GB was root, 115GB was Home, the rest is just storage area.
Well, as you can see from the mount output, you do not have a partition mounted at /home as you should with a separate home partition, and unfortunately, as there was an error showing in the parted output the blkid output did not show.

So now please run the ```
sudo blkid -c /dev/null
``` command to see what the UUIDs of partitions are.  We can then try to add your old /home partition to your new installed OS by adding the UUID of /dev/sdb3 to your /etc/fstab file and see if that moves us forwards and gives you back your old /home partition.

---

### Post by JorgeO on 2016-12-15
```

ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="Windows_VM" UUID="2898e682-e46b-4247-aa88-be9961b6ccfd" TYPE="ext4" PARTUUID="e03b6e32-01"
/dev/sda2: LABEL="LinBkp" UUID="98601a80-c291-4894-b511-86f633123655" TYPE="ext4" PARTUUID="e03b6e32-02"
/dev/sdb1: UUID="928df496-243c-4891-a553-c6cc04b882d6" TYPE="ext4" PTTYPE="dos" PARTUUID="def2742f-01"
/dev/sdb2: LABEL="Lindata" UUID="8bcb8c7a-82c7-4149-8c06-266d350fa775" TYPE="ext4" PARTUUID="def2742f-02"
/dev/sdb3: LABEL="Home" UUID="819949f3-f2a6-4138-b88c-2b43db1aa02f" TYPE="ext4" PARTUUID="def2742f-03"
/dev/sdc1: UUID="2016-07-19-21-27-51-00" LABEL="Ubuntu 16.04.1 LTS amd64" TYPE="iso9660" PTUUID="40a863e7" PTTYPE="dos" PARTUUID="40a863e7-01"
/dev/sdc2: SEC_TYPE="msdos" UUID="0F7B-9366" TYPE="vfat" PARTUUID="40a863e7-02"


```

---

### Post by JorgeO on 2016-12-15
```


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=928df496-243c-4891-a553-c6cc04b882d6 /               ext4    errors=remount-ro 0       1



```

---

### Post by ajgreeny on 2016-12-16
OK.
First back up your current fstab file with ```
sudo cp /etc/fstab /etc/fstab.backup
```
Now open the file in gedit or whatever text editor you normally use with ```
sudo -H gedit /etc/fstab
```
and at the bottom add the lines 
```
# /home was added on /dev/sdb3 manually after installation
UUID=819949f3-f2a6-4138-b88c-2b43db1aa02f /home           ext4    defaults        0       2
``` and finally save the file.
Now run command ```
sudo mount -a
``` and if no errors appear and terminal goes straight back to the prompt, all should be well and the old /home should now be mounted as /home in your new OS.

If any errors do appear in terminal let us know and we'll try to put that right.

---

### Post by JorgeO on 2016-12-16
I'm unable to save the gedit file. These are the error messages:

```

   ubuntu@ubuntu:~$ sudo -H gedit /etc/fstab
 
 
 ** (gedit:13362): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported
 
 
 ** (gedit:13362): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported
 
 
 ** (gedit:13362): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
 ubuntu@ubuntu:~$  





```

---

### Post by JorgeO on 2016-12-16
ajgreeny

Would it be possible to copy the partitions (minus root) to the second HD, do a full reinstall formating the Linux partitions and then copy the backup files to the work HD?

---

### Post by ajgreeny on 2016-12-16
It looks as if you could not even open the /etc/fstab file in gedit with that command?  That is very strange and you should be able to do so.

Try using ```
sudo nano /etc/fstab
```and manually copy by typing the second of the lines I show very carefully using that. The first line is just a comment and does nothing.
If you do not know nano, it is a terminal text editor; you navigate with the cursor keys and type normally, but it is difficult, maybe impossible, to paste text, so you'll have to type it carefully.
Once you have edited the fstab file press "Ctrl+o" and it will offer to save the tmp file as fstab.  Hit "Enter" to accept the save then Ctrl+x to close nano, and now again try ```
sudo mount -a
``` to test the new fstab file.

---

### Post by JorgeO on 2016-12-16
**fstab is a read only file! Both when booting from Ubuntu's flash drive or the HD.**

---

### Post by JorgeO on 2016-12-17
ajgreeny

I have two Filezilla images from last September - root and Home. I could restore them, just a small loss. But then, how would I upgrade to 16.04 without messing it all again?

---

### Post by ajgreeny on 2016-12-17
> **JorgeO said:**
> **fstab is a read only file! Both when booting from Ubuntu's flash drive or the HD.**
I have no idea why that is so on your system; it should not be read only if you edit it as root.
What is the output of terminal command ```
ls -l /etc/fstab
```
It should show ```
-rw-r--r-- 1 root root 854 Dec 16 21:28 /etc/fstab
```or something very similar with rw as the second and third characters.
You should be able to edit it either by booting to your hard drive or from a live USB system, but in either case you must use root permissions, ie **sudo -H gedit** or **sudo nano** or you will not be able to save the edited file.

I do not believe there is any real point it trying to restore backups and then upgrade again as it will involve so much more work for you than just getting your old /home partition mounted again as the new /home partition which should be only a few seconds work.

Are you certain you are doing everything exactly in the way I suggest?

---

### Post by JorgeO on 2016-12-17
ajgreeny

Whatever was broken in the root partition was VERY broken. Crazy.

I bite the bullet, reformated the root partition and did a fresh reinstall of 16.04.1 from the flash drive. Just after install, the WiFi connected.

Then I followed your instructions (again) and after the reboot my Home partition was mounted and on line.

Two lessons learned: 
- NEVER, EVER install with a single partition for root and Home;
- NEVER update to a new LTS as soon as Canonical offers it. Too risky.

Thanks a lot for your help and patiense!

Jorge

---

