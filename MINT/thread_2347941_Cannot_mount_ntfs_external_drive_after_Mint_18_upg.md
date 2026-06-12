---
title: "Cannot mount ntfs external drive after Mint 18 upgrade"
date: 2016-12-30
forum: MINT
---

### Post by bkrram on 2016-12-30
I recently upgraded from mint 17.3 to 18. Since then, I have not been able to mount my external hard drive which I could do before. I get the following error :

Error mounting /dev/sdd1 at /media/ram/Nagini_n_Ram's_Drive: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdd1" "/media/ram/Nagini_n_Ram's_Drive"' exited with non-zero exit status 21: mount: according to mtab, /dev/sdd1 is already mounted on /media/ram/Nagini_n_Ram's_Drive

The weird thing is that mount does not show that it is mounted. Here's the output from mount :
-------------------

sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=1987624k,nr_inodes=496906,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=400256k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
none on /sys/fs/cgroup type tmpfs (rw,relatime,size=4k,mode=755)
none on /sys/fs/fuse/connections type fusectl (rw,relatime)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
none on /run/shm type tmpfs (rw,nosuid,nodev,relatime)
none on /run/user type tmpfs (rw,nosuid,nodev,noexec,relatime,size=102400k,mode=755)
none on /sys/fs/pstore type pstore (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw,relatime)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdb1 on /media/ram/0039-0DE3 type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro)
/dev/sdc1 on /media/ram/Kindle type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro)
--------------------------

My /etc/fstab has an entry for the drive but it never gets mounted :
---------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=42c29194-a492-4c4c-b6f6-11dff3a3b570 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=1a6b9442-c54a-444e-b5c7-3be52f3705ab none            swap    sw              0       0
/dev/disk/by-id/usb-TOSHIBA_External_USB_3.0_20141110061302-0:0-part1 /mnt/usb-TOSHIBA_External_USB_3.0_20141110061302-0:0-part1 auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0

-------------------------
Here' my /etc/mtab :
---------
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
rpc_pipefs /run/rpc_pipefs rpc_pipefs rw 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
/dev/sdb1 /media/ram/0039-0DE3 vfat rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2 0 0
/dev/sdc1 /media/ram/Kindle vfat rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2 0 0
----------

---

### Post by oldfred on 2016-12-30
Did you mount with Windows 8 or 10?
That leaves the file system in hibernated state. All NTFS partitions get locked up with Windows fast startup hibernation.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

[/URL]
 More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation) 

[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

