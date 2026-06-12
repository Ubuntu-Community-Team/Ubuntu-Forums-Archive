---
title: "[solved] 14.10 install does not recognize previous install"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by yeshua-1 on 2015-01-20
I used the 14.10 x64 install disk to upgrade from a 13.10 dist. on a dual boot with Win7.

I checked the 'do something else' and indicated which partician should be used as /home, / for system and one other partician for data.
The result is the computer now boots directly into 14.10 and no grub screen is offered.
The install set up its own home directory, apparently in the system partician, and my previous home remains in an unrecognized partician.

How can I get the install to setup my old /home partician as the home directory?
Is grub actually installed, if so, how can I get it to recognize the windows install?
Advice greatly appreciated.

---

### Post by TheFu on 2015-01-20
There is not direct upgrade from 13.10 to 14.10.  You had to go through 14.04.  For any non-LTS release, the only upgrade is from the release immediately before.

There are a few different ways to get back to a boot selector. The easiest way is probably to install **boot-repair** and run it.
**sudo update-grub** might work too.

---

### Post by yeshua-1 on 2015-01-20
Dual boot is now resolved. Inability to access home directory in seperate partition unreolved.

---

### Post by grahammechanical on 2015-01-20
You have opened another thread with the same problem. Please do not do that.

[http://ubuntuforums.org/showthread.php?t=2261705&p=13211991#post13211991](http://ubuntuforums.org/showthread.php?t=2261705&p=13211991#post13211991)

Every install of Ubuntu has an /home folder. Even when we use the Something Else option to tell the installer to use a partition as /home the Ubuntu / will still have a /home folder but it will be automagically linked to the username folder on the /home partition

The technique is to select the partition we want as /, click Change, and in the Use As panel select Ext4 from the drop down menu, then tick the box labelled Format the partition and in the Mount point panel select / from the drop down menu. Then click OK.

Next select the partition we want to be /home, click Change, and in the Use As panel select Ext4 but this time do not tick the box labelled Format the partition. I repeat, do not tick to have the partition formatted. Then in the Mount point panel select /home and click OK.

If we fail to give the intended partition a mount point of /home then that partition will not be used as a /home partition.

All the above applies to reinstalling Ubuntu where there is an existing /home partition. But if the /home partition does not exist and we are doing the install to create a /home partition, then we will format the partition and the install will create the default folders of Documents, Downloads, Music, Pictures, and Videos for us.

What really concerns me is that when Ubuntu is the only OS we do not get a Grub boot menu. But Windows 7 should be on that disk. So, you should be getting a Grub boot menu and it should give options to load either Ubuntu or Windows 7. So, I am wondering if Windows 7 has been over written. A boot Repair report will help answer that question.

Regards.

---

### Post by yeshua-1 on 2015-01-20
I used boot repair and was able to fix the grub problem, by removing two old versions of grub and installing a new one where I wanted it. So dual boot is now working again.
The selection of mount at /home was done during re-installation, however I didn't format the system area before re-installation, perhaps that is the problem. I'll do a re-install now and format the old system area.

---

### Post by yeshua-1 on 2015-01-20
I did a re-install of 14.10, and the problem remains the same. I am still connected to the new home directory, and my former insalls home directory on a seperate partition is not used by Ubuntu.

---

### Post by TheFu on 2015-01-20
Please post the output from these commands inside "code tags" so things line up.
* sudo parted -l
* mount
* cat /etc/fstab

---

### Post by yeshua-1 on 2015-01-20
parted -l
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  276GB   276GB   primary   ntfs            boot
 2      276GB   2000GB  1724GB  extended
 8      276GB   277GB   499MB   logical   ext4
 9      277GB   536GB   260GB   logical   ext4
 5      536GB   542GB   6000MB  logical   linux-swap(v1)
 6      542GB   1400GB  858GB   logical   ext4
 7      1400GB  2000GB  600GB   logical   fat32

--------------------
mount

/dev/sda9 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,nodev,noexec,nosuid)
sysfs on /sys type sysfs (rw,nodev,noexec,nosuid)
none on /sys/fs/cgroup type tmpfs (rw,uid=0,gid=0,mode=0755,size=1024)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,nodev,noexec,nosuid,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,nodev,noexec,nosuid,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /home type ext4 (rw)
/dev/sda7 on /data1 type vfat (rw,utf8,umask=007,gid=46)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,noexec,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=yeshua)

-------------------------
fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=3f30a02a-06b1-4e22-9261-14b3ca89f394 /               ext4    errors=remount-ro 0       1
# /data1 was on /dev/sda7 during installation
UUID=5CD5-2F9A  /data1          vfat    utf8,umask=007,gid=46 0       1
# /home was on /dev/sda6 during installation
UUID=8ceb8b8e-73ee-438c-bab9-7a3dff593e79 /home           ext4    defaults        0       2
# /windows was on /dev/sda1 during installation
UUID=204F406A2D979568 /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=372c7945-4df2-4a92-a030-19207d4700c0 none            swap    sw              0       0

---

### Post by TheFu on 2015-01-20
Ah UUIDs - need the output from **sudo blkid** too. Sorry.

---

### Post by yeshua-1 on 2015-01-20
here tis

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=3f30a02a-06b1-4e22-9261-14b3ca89f394 /               ext4    errors=remount-ro 0       1
# /data1 was on /dev/sda7 during installation
UUID=5CD5-2F9A  /data1          vfat    utf8,umask=007,gid=46 0       1
# /home was on /dev/sda6 during installation
UUID=8ceb8b8e-73ee-438c-bab9-7a3dff593e79 /home           ext4    defaults        0       2
# /windows was on /dev/sda1 during installation
UUID=204F406A2D979568 /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=372c7945-4df2-4a92-a030-19207d4700c0 none            swap    sw              0       0

---

### Post by fantab on 2015-01-20
Post the output of:
```
sudo blkid
```

--- Please use [code] tags to wrap the output. See my signature on how to use code tags.

---

### Post by yeshua-1 on 2015-01-20
```

/dev/sda1: UUID="204F406A2D979568" TYPE="ntfs" PARTUUID="000ce8b8-01" 
/dev/sda5: UUID="372c7945-4df2-4a92-a030-19207d4700c0" TYPE="swap" PARTUUID="000ce8b8-05" 
/dev/sda6: UUID="8ceb8b8e-73ee-438c-bab9-7a3dff593e79" TYPE="ext4" PARTUUID="000ce8b8-06" 
/dev/sda7: UUID="5CD5-2F9A" TYPE="vfat" PARTUUID="000ce8b8-07" 
/dev/sda8: UUID="61a26364-89c0-4685-942d-49f75d0bec6d" TYPE="ext4" PARTUUID="000ce8b8-08" 
/dev/sda9: UUID="3f30a02a-06b1-4e22-9261-14b3ca89f394" TYPE="ext4" PARTUUID="000ce8b8-09" 

```

---

### Post by fantab on 2015-01-20
```
parted -l
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  276GB   276GB   primary   ntfs            boot
 2      276GB   2000GB  1724GB  extended
 8      276GB   277GB   499MB   logical   ext4
 9      277GB   536GB   260GB   logical   ext4
 5      536GB   542GB   6000MB  logical   linux-swap(v1)
 6      542GB   1400GB  858GB   logical   ext4
 7      1400GB  2000GB  600GB   logical   fat32
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=3f30a02a-06b1-4e22-9261-14b3ca89f394 /               ext4    errors=remount-ro 0       1
[COLOR=#0000cd][I]# /data1 was on /dev/sda7 during installation
UUID=5CD5-2F9A  /data1          vfat    utf8,umask=007,gid=46 0       1[/I][/COLOR]
[COLOR=#006400]# /home was on /dev/sda6 during installation
UUID=8ceb8b8e-73ee-438c-bab9-7a3dff593e79 /home           ext4    defaults        0       2[/COLOR]
[COLOR=#0000cd][I]# /windows was on /dev/sda1 during installation
UUID=204F406A2D979568 /windows        ntfs    defaults,umask=007,gid=46 0       0[/I][/COLOR]
# swap was on /dev/sda5 during installation
UUID=372c7945-4df2-4a92-a030-19207d4700c0 none            swap    sw              0       0
```

```

/dev/sda1: UUID="204F406A2D979568" TYPE="ntfs" PARTUUID="000ce8b8-01" 
/dev/sda5: UUID="372c7945-4df2-4a92-a030-19207d4700c0" TYPE="swap" PARTUUID="000ce8b8-05" 
/dev/sda6: UUID="8ceb8b8e-73ee-438c-bab9-7a3dff593e79" TYPE="ext4" PARTUUID="000ce8b8-06" 
/dev/sda7: UUID="5CD5-2F9A" TYPE="vfat" PARTUUID="000ce8b8-07" 
/dev/sda8: UUID="61a26364-89c0-4685-942d-49f75d0bec6d" TYPE="ext4" PARTUUID="000ce8b8-08" 
/dev/sda9: UUID="3f30a02a-06b1-4e22-9261-14b3ca89f394" TYPE="ext4" PARTUUID="000ce8b8-09"
```

According to the info you provided:
** **/dev/sda6 is being mounted as /home**. I can't see why it can't be used. 
** /dev/sda1 (Windows C probably) is also mounting at boot. It is not a good idea to mount Win C partition. You can mount it selectively but mounting on boot should be avoided.

I can't see why you can't use your /home, perhaps we need more info.

Since you say:
> ...my previous home remains in an unrecognized partician.


Boot Ubuntu from DVD/USB and 'Try Ubuntu'. Download and install [Boot-Repair tool]("https://help.ubuntu.com/community/Boot-Repair"). 
Run Boot-Repair and '**create a Bootinfo Summary**', _note down the URL_ link to the file and post it back here.
Just DON'T run any repairs yet, we need to see the info which boot summary provides first.

---

### Post by yeshua-1 on 2015-01-20
yes, I can see that it is supposed to be mounted, and I can find it when browsing files if I go to the system folder and look for it, but it is not the home directory being used by the system.

bootinfo summary is at; [http://paste.ubuntu.com/9800957/](http://paste.ubuntu.com/9800957/)

---

### Post by fantab on 2015-01-20
```

df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda9      ext4      239G  4.6G  222G   3% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  3.9G  4.0K  3.9G   1% /dev
tmpfs          tmpfs     787M  1.2M  785M   1% /run
none           tmpfs     5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs     3.9G  700K  3.9G   1% /run/shm
none           tmpfs     100M   44K  100M   1% /run/user
/dev/sda1      fuseblk   258G   44G  214G  17% /windows
[COLOR=#006400]**/dev/sda6      ext4      787G  271G  477G  37% /home**[/COLOR]
[COLOR=#0000cd]/dev/sda7      vfat      559G  165G  394G  30% /data1[/COLOR]
/dev/sr0       iso9660   614M  614M     0 100% /media/yeshua/Boot-Repair-Disk 64bit
/dev/sda8      ext4      453M   72M  354M  17% /mnt/boot-sav/sda8
```

How do you know that /dev/sda6 is not being used as /home? 
AFIK /home partition is being mounted and that is the only /home you have.
What is /data1 or /dev/sda7 partition?

Lets edit you /etc/fstab file and stop /dev/sda7 and /dev/sda1 from mounting.
From installed ubuntu:
```
sudo gedit /etc/fstab
```

Edit the file by adding '#' at the start of the following lines in red:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=3f30a02a-06b1-4e22-9261-14b3ca89f394 /               ext4    errors=remount-ro 0       1
# /data1 was on /dev/sda7 during installation
[COLOR=#b22222]**#**UUID=5CD5-2F9A  /data1          vfat    utf8,umask=007,gid=46 0       1[/COLOR]
# /home was on /dev/sda6 during installation
UUID=8ceb8b8e-73ee-438c-bab9-7a3dff593e79 /home           ext4    defaults        0       2
# /windows was on /dev/sda1 during installation
[COLOR=#b22222]**#**UUID=204F406A2D979568 /windows        ntfs    defaults,umask=007,gid=46 0[/COLOR]       [COLOR=#b22222]0[/COLOR]
# swap was on /dev/sda5 during installation
UUID=372c7945-4df2-4a92-a030-19207d4700c0 none            swap    sw              0       0
```

Save the file and restart ubuntu. Let us know if /home is being used.

---

### Post by yeshua-1 on 2015-01-20
sda7 is an extra partition in which data is kept,

how do I know that sda6 is not being used?
well, it has many files in it, if I open home on my file browser in the new install it shows only the stock music, pictures, etc. , not all the files that are in my /home directory from previous install, therefore it is not being used, also I have a special firefox profile, which firefox finds and loads when my /home directory from previous install is used. This is the first time I've come across this problem. On previous re-installs, when I indicated that a certain partition is /home, it was. I've never encountered this before.

---

### Post by fantab on 2015-01-20
So on which partition do you have present Home?

---

### Post by yeshua-1 on 2015-01-20
I don't know where it is. In the new install of 14.10 I assume it is in the system partition, since it is not seen anywhere else.

I edited fstab as suggested, no difference.

---

### Post by yeshua-1 on 2015-01-20
```

yeshua@ydesk:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
yeshua@ydesk:

```

but
```

yeshua@ydesk:/home$ ls
lost+found  yeshua  ymp
yeshua@ydesk:/home$

```

these two home directories exist under /home in the system directory (plus lost+found)
yeshua is the home directory the new install is displaying
ymp is the home directory in the other partition which the new install is not using

---

### Post by TheFu on 2015-01-21
You can use **df -h . **to see the partition data for the current directory.
It is doubtful (highly unusual) for /home/yeshua and /home/ymp to be in different partitions. I'm not buying that.

The home directory location is usually control by the entry for each userid in the /etc/passwd file. The location specified in there must point to an existing directory for it to work. Normally these are setup properly when a userid is created.

Another interesting part of this is that UNIX/Linux file systems don't know anything about usernames - the file system only knows about the uid - the number.  The first user created during install is uid=1000. If the file system comes from a prior install, the uid might be different and it might not match. The gid needs to match too, in a similar manner.

**ls -al /home** will tell us something about that.

---

### Post by yeshua-1 on 2015-01-21
```

yeshua@ydesk:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda9       239G  4.6G  222G   3% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           787M  1.2M  785M   1% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none            3.9G  532K  3.9G   1% /run/shm
none            100M  116K  100M   1% /run/user
/dev/sda6       787G  271G  477G  37% /home
none            3.9G  2.0M  3.9G   1% /tmp/guest-2IyvCm
yeshua@ydesk:~$

```

and

```

yeshua@ydesk:~$ ls -al /home
total 32
drwxr-xr-x  5 root   root    4096 Oct 15 17:42 .
drwxr-xr-x 25 root   root    4096 Jan 20 15:13 ..
drwx------  2 root   root   16384 Apr  2  2014 lost+found
drwxr-xr-x 24 yeshua yeshua  4096 Jan 21 04:33 yeshua
drwxr-xr-x 67 yeshua yeshua  4096 Jan 19 17:42 ymp
yeshua@ydesk:~$

```

---

### Post by TheFu on 2015-01-21
The **ls -al /home **shows the issue.  Both of those "home directories" are owned by the same userid.  
Look inside the /etc/passwd file to see which points where.  You can just rename the one you want to use to match whatever is in /etc/passwd.  May want to move the other directory under the renamed one first.

If the settings you want to use are in the right place, under the correct HOME, then those will be used.

---

### Post by yeshua-1 on 2015-01-21
here is the contents of passwd
```

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
syslog:x:100:103::/home/syslog:/bin/false
messagebus:x:101:105::/var/run/dbus:/bin/false
uuidd:x:102:107::/run/uuidd:/bin/false
dnsmasq:x:103:65534:dnsmasq,,,:/var/lib/misc:/bin/false
avahi-autoipd:x:104:114:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
speech-dispatcher:x:105:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/false
kernoops:x:106:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
rtkit:x:107:115:RealtimeKit,,,:/proc:/bin/false
saned:x:108:116::/home/saned:/bin/false
usbmux:x:109:46:usbmux daemon,,,:/var/lib/usbmux:/bin/false
whoopsie:x:110:117::/nonexistent:/bin/false
avahi:x:111:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
lightdm:x:112:119:Light Display Manager:/var/lib/lightdm:/bin/false
pulse:x:113:122:PulseAudio daemon,,,:/var/run/pulse:/bin/false
colord:x:114:124:colord colour management daemon,,,:/var/lib/colord:/bin/false
hplip:x:115:7:HPLIP system user,,,:/var/run/hplip:/bin/false
yeshua:x:1000:1000:Yeshua Moser-Puangsuwan,,,:/home/yeshua:/bin/bash

```

I think I understand your suggestion, I should use sudo to do this right?

---

### Post by TheFu on 2015-01-21
No. sudo isn't needed to move those files into ~jeshua/. The  yeshua account owns all the files and that is the home directory being used. If you want the settings from the other directory to be used, there are 5 different ways to accomplish it. Here's one:

```
mv ~ymp/* ~/
mv ~ymp/.* ~/

```
and be done.  Of course, make a backup of both before starting out and it would be best to do this without any GUI running.  I'd logout locally and use ssh to connect from another machine via ssh.

---

### Post by yeshua-1 on 2015-01-21
that did it.

---

