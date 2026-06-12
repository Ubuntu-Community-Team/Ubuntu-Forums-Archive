---
title: "After upgrade to 16.04, missing Documents / Files (Unable to find the requested file)"
date: 2016-07-22
forum: Installation &amp; Upgrades
---

### Post by federicodemaria on 2016-07-22
Hi all, 
I wanted to upgrade from 14.04 to 16.04, but I messed it up badly (explained here: [https://ubuntuforums.org/showthread.php?t=2331176](https://ubuntuforums.org/showthread.php?t=2331176))
so that I decide to re-install from scratch with Live CD. 

First, I tried the option of re-installing only the operating system, but it failed. So, then, I chose the option of erasing everything, but then from the partition I didn't format /Home. 

The laptop works quite well. I had some little problems, like WIFI not working, but I solved unabling Secure boot ([https://ubuntuforums.org/showthread.php?t=2331302](https://ubuntuforums.org/showthread.php?t=2331302)). 

**Now, the last problem I seem to face is that, somehow, my old and new account/use conflict. Said differently, there is some problem with /Home. **

My previous /Home is there with all files (screenshoot attached). I anyway keep all my important files on Dropbox (which works correctly), and I could delete without problems any other folders. I cannot opens the ones below Computer, and before Server (See attached picture)

For example, once I click on Documents or Music or Videos,
I get the following error message (screenshoot attached): 
"Unable to find the requested file. Please check the spelling and try again.
Unhandled error message: Error when getting information for file '/home/jhonny/Documents': No such file or directory"

I get also another problem with Backup, that I had set automatically since Ubuntu 14.04. How I get this error message: 
Backup: "Failed to execute child process "duplicity" (No such file or directory)"

This is my partition, I've not changed it manually 

```

jhonny@Jhonny-Lenovo-B590:~$ df -T
Filesystem     Type     1K-blocks      Used Available Use% Mounted on
udev           devtmpfs   1927960         0   1927960   0% /dev
tmpfs          tmpfs       389448      6268    383180   2% /run
/dev/sda2      ext4     476093488 122388384 329497848  28% /
tmpfs          tmpfs      1947236       772   1946464   1% /dev/shm
tmpfs          tmpfs         5120         4      5116   1% /run/lock
tmpfs          tmpfs      1947236         0   1947236   0% /sys/fs/cgroup
/dev/sda1      vfat        523248      3632    519616   1% /boot/efi
tmpfs          tmpfs       389448        88    389360   1% /run/user/1000
jhonny@Jhonny-Lenovo-B590:~$ 

```

Thank you for your help

---

### Post by TheFu on 2016-07-22
please post the output from 
* ls -al ~/
* id
I'm guessing it is a permissions issue.  Also, above you always say "/Home" ... but "/home" is the normal location and Linux file systems are case sensitive.

Best to deal with the backup issue in a different thread (plus I don't know anything about how the built-in backup tool works). I use a different tool.

---

### Post by federicodemaria on 2016-07-24
Thanks!

I'm not a very expert user. I checked, you are right, it's /home

```

jhonny@Jhonny-Lenovo-B590:~$ ls -al ~/
total 28952228
drwxr-xr-x 35 jhonny jhonny        4096 jul 21 06:01 .
drwxr-xr-x  3 root   root          4096 abr 12 22:14 ..
drwx------  5 jhonny jhonny        4096 dic  7  2015 .adobe
drwxrwxr-x  3 jhonny jhonny        4096 abr 29 18:55 .audacity-data
-rw-------  1 jhonny jhonny        8024 jul 22 12:25 .bash_history
-rw-r--r--  1 jhonny jhonny         220 oct 27  2015 .bash_logout
-rw-r--r--  1 jhonny jhonny        3637 oct 27  2015 .bashrc
drwx------ 29 jhonny jhonny        4096 jul 19 20:59 .cache
-rw-rw-r--  1 jhonny jhonny         438 may  5 17:49 C:\nppdf32Log\debuglog.txt
drwx------  3 jhonny jhonny        4096 nov 14  2015 .compiz
drwx------ 35 jhonny jhonny        4096 may  5 17:49 .config
drwx------  3 root   root          4096 oct 27  2015 .dbus
drwxr-xr-x  4 jhonny jhonny        4096 jul 21 05:35 Desktop
-rw-r--r--  1 jhonny jhonny          25 feb  6 20:52 .dmrc
drwxr-xr-x  3 jhonny jhonny        4096 jul 20 18:41 Downloads
drwx------  5 jhonny jhonny        4096 jul 21 06:30 .dropbox
drwx------ 31 jhonny jhonny        4096 jul 21 06:31 Dropbox
drwxr-xr-x  3 jhonny jhonny        4096 jul 21 06:30 .dropbox-dist
drwxr-xr-x  9 jhonny jhonny        4096 may 27 22:01 .dvdcss
drwx------ 14 jhonny jhonny        4096 abr 14 11:01 FE_DE_OLD DOCUMENTS
drwx------  3 jhonny jhonny        4096 jul 21 06:02 .gconf
drwx------  3 jhonny jhonny        4096 oct 27  2015 .gnome
drwx------  3 jhonny jhonny        4096 jul 21 06:01 .gnupg
-rw-rw-r--  1 jhonny jhonny    49288366 jun 24 02:13 google-chrome-stable_current_amd64.deb
-rw-rw-r--  1 jhonny jhonny    49288366 jun 24 02:13 google-chrome-stable_current_amd64.deb.1
drwxrwxr-x  2 jhonny jhonny        4096 may 26 10:44 Google Drive
drwx------  2 jhonny jhonny        4096 jul 20 09:48 .gphoto
-rw-------  1 jhonny jhonny          86 may 26 10:19 .grive
-rw-rw-r--  1 jhonny jhonny         624 may 26 10:45 .grive-setup.log
drwx------  2 root   root          4096 oct 27  2015 .gvfs
drwxr-----  2 jhonny jhonny        4096 jul 17 14:34 .hplip
drwxrwxr-x  2 jhonny jhonny        4096 abr 28 11:34 hubiC
-rw-------  1 jhonny jhonny       54786 jul 21 06:01 .ICEauthority
drwxrwxr-x 31 jhonny jhonny        4096 mar 31 17:36 Llibres
-rw-------  1 jhonny jhonny 29548226731 may  6 17:15 Llibres.rar
drwx------  3 jhonny jhonny        4096 oct 27  2015 .local
drwx------  3 jhonny jhonny        4096 oct 28  2015 .macromedia
drwxrwxr-x  3 jhonny jhonny        4096 abr 13 10:24 .mono
drwx------  4 jhonny jhonny        4096 oct 27  2015 .mozilla
drwxrwxr-x  2 jhonny jhonny        4096 abr  3 21:45 .mplayer
drwxr-xr-x  2 jhonny jhonny        4096 jul 22 11:05 Pictures
drwx------  3 jhonny jhonny        4096 oct 27  2015 .pki
-rw-r--r--  1 jhonny jhonny         675 oct 27  2015 .profile
drwx------  7 jhonny jhonny        4096 jul 24 08:17 .Skype
-rw-r--r--  1 jhonny jhonny           0 jul 19 12:16 .sudo_as_admin_successful
drwxr-xr-x  2 jhonny jhonny        4096 oct 27  2015 Templates
drwx------  4 jhonny jhonny        4096 ene 28 13:59 .thunderbird
drwxrwxr-x  2 jhonny jhonny        4096 abr 28 11:34 Untitled Folder
-rw-------  1 jhonny jhonny         121 jul 21 06:01 .Xauthority
-rw-------  1 jhonny jhonny         266 jul 21 06:01 .xsession-errors
-rw-------  1 jhonny jhonny        1463 jul 21 06:00 .xsession-errors.old
jhonny@Jhonny-Lenovo-B590:~$ 

```

```

jhonny@Jhonny-Lenovo-B590:~$  id
uid=1000(jhonny) gid=1000(jhonny) groups=1000(jhonny),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),128(sambashare)
jhonny@Jhonny-Lenovo-B590:~$ 

```

---

### Post by TheFu on 2016-07-24
See those directories/files owned by root? That isn't normal and can cause issues.  Running any GUI program with **sudo** is a dangerous thing.   The work-around is to use **sudo -H**, but check the manpage to be certain.  You can safely run **sudo chown -R jhonny.jhonny ~/** to fix the current permissions.  Don't get any of those characters wrong - it could be bad, very bad.

And there doesn't appear to be any ~/Documents directory. If you want know, create it.  I don't have those directories myself, but I don't use file managers much - the shell is much quicker for me.

---

### Post by federicodemaria on 2016-07-29
Thank you. 

I've tried, but the problem persists (I haven't rebooted yet). 

Here what I get: 

```

jhonny@Jhonny-Lenovo-B590:~$ sudo chown -R jhonny.jhonny ~/
[sudo] password for jhonny: 
jhonny@Jhonny-Lenovo-B590:~$ ls -al ~/
total 28952228
drwxr-xr-x 35 jhonny jhonny        4096 jul 29 07:52 .
drwxr-xr-x  3 root   root          4096 abr 12 22:14 ..
drwx------  5 jhonny jhonny        4096 dic  7  2015 .adobe
drwxrwxr-x  3 jhonny jhonny        4096 abr 29 18:55 .audacity-data
-rw-------  1 jhonny jhonny        8034 jul 24 09:14 .bash_history
-rw-r--r--  1 jhonny jhonny         220 oct 27  2015 .bash_logout
-rw-r--r--  1 jhonny jhonny        3637 oct 27  2015 .bashrc
drwx------ 29 jhonny jhonny        4096 jul 19 20:59 .cache
-rw-rw-r--  1 jhonny jhonny         438 may  5 17:49 C:\nppdf32Log\debuglog.txt
drwx------  3 jhonny jhonny        4096 nov 14  2015 .compiz
drwx------ 35 jhonny jhonny        4096 may  5 17:49 .config
drwx------  3 jhonny jhonny        4096 oct 27  2015 .dbus
drwxr-xr-x  4 jhonny jhonny        4096 jul 21 05:35 Desktop
-rw-r--r--  1 jhonny jhonny          25 feb  6 20:52 .dmrc
drwxr-xr-x  3 jhonny jhonny        4096 jul 20 18:41 Downloads
drwx------  5 jhonny jhonny        4096 jul 29 07:52 .dropbox
drwx------ 31 jhonny jhonny        4096 jul 29 07:54 Dropbox
drwxr-xr-x  3 jhonny jhonny        4096 jul 21 06:30 .dropbox-dist
drwxr-xr-x  9 jhonny jhonny        4096 may 27 22:01 .dvdcss
drwx------ 14 jhonny jhonny        4096 abr 14 11:01 FE_DE_OLD DOCUMENTS
drwx------  3 jhonny jhonny        4096 jul 29 07:53 .gconf
drwx------  3 jhonny jhonny        4096 oct 27  2015 .gnome
drwx------  3 jhonny jhonny        4096 jul 29 07:52 .gnupg
-rw-rw-r--  1 jhonny jhonny    49288366 jun 24 02:13 google-chrome-stable_current_amd64.deb
-rw-rw-r--  1 jhonny jhonny    49288366 jun 24 02:13 google-chrome-stable_current_amd64.deb.1
drwxrwxr-x  2 jhonny jhonny        4096 may 26 10:44 Google Drive
drwx------  2 jhonny jhonny        4096 jul 20 09:48 .gphoto
-rw-------  1 jhonny jhonny          86 may 26 10:19 .grive
-rw-rw-r--  1 jhonny jhonny         624 may 26 10:45 .grive-setup.log
drwx------  2 jhonny jhonny        4096 oct 27  2015 .gvfs
drwxr-----  2 jhonny jhonny        4096 jul 17 14:34 .hplip
drwxrwxr-x  2 jhonny jhonny        4096 abr 28 11:34 hubiC
-rw-------  1 jhonny jhonny       55518 jul 29 07:52 .ICEauthority
drwxrwxr-x 31 jhonny jhonny        4096 mar 31 17:36 Llibres
-rw-------  1 jhonny jhonny 29548226731 may  6 17:15 Llibres.rar
drwx------  3 jhonny jhonny        4096 oct 27  2015 .local
drwx------  3 jhonny jhonny        4096 oct 28  2015 .macromedia
drwxrwxr-x  3 jhonny jhonny        4096 abr 13 10:24 .mono
drwx------  4 jhonny jhonny        4096 oct 27  2015 .mozilla
drwxrwxr-x  2 jhonny jhonny        4096 abr  3 21:45 .mplayer
drwxr-xr-x  2 jhonny jhonny        4096 jul 22 11:05 Pictures
drwx------  3 jhonny jhonny        4096 oct 27  2015 .pki
-rw-r--r--  1 jhonny jhonny         675 oct 27  2015 .profile
drwx------  7 jhonny jhonny        4096 jul 29 08:30 .Skype
-rw-r--r--  1 jhonny jhonny           0 jul 19 12:16 .sudo_as_admin_successful
drwxr-xr-x  2 jhonny jhonny        4096 oct 27  2015 Templates
drwx------  4 jhonny jhonny        4096 ene 28  2016 .thunderbird
drwxrwxr-x  2 jhonny jhonny        4096 abr 28 11:34 Untitled Folder
-rw-------  1 jhonny jhonny         121 jul 29 07:51 .Xauthority
-rw-------  1 jhonny jhonny         266 jul 29 07:52 .xsession-errors
-rw-------  1 jhonny jhonny        1332 jul 27 10:12 .xsession-errors.old
jhonny@Jhonny-Lenovo-B590:~$ id
uid=1000(jhonny) gid=1000(jhonny) groups=1000(jhonny),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),128(sambashare)
jhonny@Jhonny-Lenovo-B590:~$ 

```

---

### Post by TheFu on 2016-07-29
Question. Did you mount the old HOME partition using the /etc/fstab under the newly installed OS?
$** df -h**
will show if this happened or not.  If not, that will need to happen.

---

### Post by federicodemaria on 2016-08-12
I don't really know what you mean, so that I haven't done it. 
If you could kindly explain me how to do it, I will. 

Thanks 

```

jhonny@Jhonny-Lenovo-B590:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1,9G     0  1,9G   0% /dev
tmpfs           381M  6,2M  375M   2% /run
/dev/sda2       455G  118G  314G  28% /
tmpfs           1,9G  508K  1,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           1,9G     0  1,9G   0% /sys/fs/cgroup
/dev/sda1       511M  3,6M  508M   1% /boot/efi
tmpfs           381M   56K  381M   1% /run/user/1000
jhonny@Jhonny-Lenovo-B590:~$ 

```

---

### Post by ajgreeny on 2016-08-12
It sounds as if you did have a separate /home partition which you chose to not format when you reinstalled, but I suspect you did not give it the mountpoint of /home when setting up partitions.

Can we check that you used the "Something Else" option when reinstalling because if not you may have wiped out the original /home partition; certainly there is no /home partition showing in your **df -h** output.

There was also a typo in the chown command shown by TheFu and copied by you which I don't think will have caused problems but is worth mentioning.  It should have been ```
sudo chown -R jhonny:jhonny /home/jhonny
```Note the colon between the two instances of the username, not a period.  Also I always think it better and possibly safer to use the full pathway for that command, ie /home/jhonny rather than the tilde shortcut ~/.

What does ```
sudo parted -l
``` show us as output for a start, followed by ```
sudo blkid -c /dev/null && mount
```

---

### Post by federicodemaria on 2016-08-12
Thank you for your help. 

Yes, I think I choose something else and then decided not to format /home. I don't know how to give it a mountpoint.

Shall I run: ```
 sudo chown -R jhonny:jhonny /home/jhonny 
```?

```

jhonny@Jhonny-Lenovo-B590:~$ sudo parted -l
[sudo] password for jhonny: 
Model: ATA HGST HTS545050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  538MB  537MB   fat32                 boot, esp
 2      538MB   496GB  495GB   ext4
 3      496GB   500GB  4140MB  linux-swap(v1)


jhonny@Jhonny-Lenovo-B590:~$ 

```

```

jhonny@Jhonny-Lenovo-B590:~$ sudo blkid -c /dev/null && mount
/dev/sda1: UUID="001B-8D8F" TYPE="vfat" PARTUUID="013ce4f1-1045-42c6-ab7b-fee246b934e9"
/dev/sda2: UUID="fab517da-62f9-4dd3-95e8-44d5a9a9e951" TYPE="ext4" PARTUUID="02c7c2c4-cf35-4489-a3a7-2eb7e54d4cd9"
/dev/sda3: UUID="24009f81-7193-415e-bb85-668885d5cf6d" TYPE="swap" PARTUUID="5adf282e-8a4a-4872-8d22-557abb4e41ca"
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1927960k,nr_inodes=481990,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=389448k,mode=755)
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=389448k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
jhonny@Jhonny-Lenovo-B590:~$ 

```

---

### Post by ajgreeny on 2016-08-12
Oh dear!

It looks as if you used all the disk except for the swap partition as root this time and did not set root to use only the old root partition
```
Number  Start   End    Size    File system     Name  Flags
 1      1049kB  538MB  537MB   fat32                 boot, esp
 2      538MB   496GB  495GB   ext4
 3      496GB   500GB  4140MB  linux-swap(v1)
```
This shows you have a 4GB swap, a 537MB EFI/ESP partition, and that root takes all the rest of the 500GB disk so I think you have wiped all your old /home folders and files, so I hope you have a backup.

It is possible that testdisk may be able to restore the old partiton, but as you have been using the new OS I also fear that you may have damaged some of those old files

Out of interest and hoping it may be your related to the missing Documents folder, what is the **FE_DE_OLD DOCUMENTS** shown in your output from the ls -la command?

---

### Post by federicodemaria on 2016-08-13
Thank you for your help. 

Yes, I think I choose 'something else'[IMG]/home/jhonny/Desktop[/IMG] and then decided not to format /home. I don't know how to give it a mountpoint.

Shall I run: ```
 sudo chown -R jhonny:jhonny /home/jhonny 
```?

Let me say it: What a mess I did!!! :-) 

Home is 337,00 GB
The good news is that I have a backup, plus all my documents are on a cloud. I don't really mind if all files have been deleted. 
I think I can see the old home, and the folder called  FE_DE_OLD DOCUMENTS is a copy of my important files, before I re-installed the system.  
The problem that persists, and I wanted to solve is that when I click on Documents, Videos or Picture, I get an error message, as shown in the screenshot. 

Here two screen shots:

[IMG]/home/jhonny/Desktop/Home.png[/IMG]
[http://uploads.im/MpONG.png](http://uploads.im/MpONG.png)

[IMG]/home/jhonny/Desktop/Screenshot from 2016-08-13 11-46-56.png[/IMG]
[http://uploads.im/dcHtA.png](http://uploads.im/dcHtA.png)

```

jhonny@Jhonny-Lenovo-B590:~$ sudo parted -l
[sudo] password for jhonny: 
Model: ATA HGST HTS545050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  538MB  537MB   fat32                 boot, esp
 2      538MB   496GB  495GB   ext4
 3      496GB   500GB  4140MB  linux-swap(v1)


jhonny@Jhonny-Lenovo-B590:~$ 

```

```

jhonny@Jhonny-Lenovo-B590:~$ sudo blkid -c /dev/null && mount
/dev/sda1: UUID="001B-8D8F" TYPE="vfat" PARTUUID="013ce4f1-1045-42c6-ab7b-fee246b934e9"
/dev/sda2: UUID="fab517da-62f9-4dd3-95e8-44d5a9a9e951" TYPE="ext4" PARTUUID="02c7c2c4-cf35-4489-a3a7-2eb7e54d4cd9"
/dev/sda3: UUID="24009f81-7193-415e-bb85-668885d5cf6d" TYPE="swap" PARTUUID="5adf282e-8a4a-4872-8d22-557abb4e41ca"
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1927960k,nr_inodes=481990,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=389448k,mode=755)
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=389448k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
jhonny@Jhonny-Lenovo-B590:~$ 

```

---

### Post by ajgreeny on 2016-08-13
I am still baffled as to where your /home partition of 337GB is because there is no partition of that size shown assuming you have only the one hard disk.

Do you know that /home was 337GB only from ypour memory of its size or do you know it from some information you have but have not shown here?

Do you have anything in the new home folder that needs backing up?  If so do it now then we can start to deal with shrinking your current huge root partition and making a new separate /home partition for you and restoring all your old files from the backup.

---

### Post by federicodemaria on 2016-08-13
I say home is 337 GB, because when I right click, that it was it shows. It also says I have about 115 GB of files. 

Screenshoot: [http://uploads.im/MpONG.png](http://uploads.im/MpONG.png)

I've now launched a back up, just in case.

Let me remind you what I said in my first post opening this thread (images attached in the first post): 

My previous /Home is there with all files (screenshoot attached). I anyway keep all my important files on Dropbox (which works correctly), and I could delete without problems any other folders. I cannot opens the ones below 'Computer', and before 'Server' (See attached picture)

For example, once I click on Documents or Music or Videos,
I get the following error message (screenshoot attached):
"Unable to find the requested file. Please check the spelling and try again.
Unhandled error message: Error when getting information for file '/home/jhonny/Documents': No such file or directory"


To tell you the truth, since I save all my files on a cloud, this problem doesn't really bother me too much. If it is complicated or risky to attempt solving it, it can remain as it is. Thanks a lot

---

### Post by ajgreeny on 2016-08-13
I think I am still not understanding what has happened, what partitions you had previously, or where you are at the moment.

Do you know whether or not you used to have a separate /home partition or was it just a folder within the root partition?
Can you now show us the output of ```
ls -a /home/jhonny
``` as it looks as if in some way you have managed to move all your old files and folders to another folder, **FE_DE_OLD DOCUMENTS** but if that's the case we can relatively easily move them back to your new and current home, no matter if that is a folder in root or a separate partition.

---

### Post by federicodemaria on 2016-08-13
Apologies, my knowledge is so limited, that I don't really know myself either. I'm sorry 

I don't know whether /home was a separate partition. I've installed several times Ubuntu, some times with manual partitions, other with automatic, so I don't remember what was the case last time. I know that during the last installation I chose 'something else', and chose not to format what I though was /home. I don't think I've lost any files, since in Videos and Music (where I can't access now) I normally don't save anything. I can't really remember whether I had something in Documents. I anyway have a copy of the files elsewhere. 

Now, regarding the root partition, I don't really know what it is. In general, I would prefer to leave the partition as it is (if it is not a problem), because I'm afraid that something might go wrong. It took me already sometime to make it work again. 

Thanks 

```

jhonny@Jhonny-Lenovo-B590:~$ ls -a /home/jhonny
.                                         .gphoto
..                                        .grive
.adobe                                    .grive-setup.log
.audacity-data                            .gvfs
.bash_history                             .hplip
.bash_logout                              hubiC
.bashrc                                   .ICEauthority
.cache                                    Llibres
C:\nppdf32Log\debuglog.txt                Llibres.rar
.compiz                                   .local
.config                                   .macromedia
.dbus                                     .mono
Desktop                                   .mozilla
.dmrc                                     .mplayer
Downloads                                 Pictures
.dropbox                                  .pki
Dropbox                                   .profile
.dropbox-dist                             .Skype
.dvdcss                                   .sudo_as_admin_successful
FE_DE_OLD DOCUMENTS                       Templates
.gconf                                    .thunderbird
.gnome                                    Untitled Folder
.gnupg                                    .Xauthority
google-chrome-stable_current_amd64.deb    .xsession-errors
google-chrome-stable_current_amd64.deb.1  .xsession-errors.old
Google Drive
jhonny@Jhonny-Lenovo-B590:~$ 

```

---

### Post by ajgreeny on 2016-08-13
Right; it looks as if you probably did not have a separate /home partition last time, but now I don't think we need to worry too much about that.

Just to be sure can you now show me the output of ```
ls -a /home/jhonny/FE_DE_OLD DOCUMENTS
``` and also right click on FE_DE_OLD DOCUMENTS go to Properties and see what size that folder is.

---

### Post by federicodemaria on 2016-08-14
Great!

Right click FE_DE_OLD DOCUMENTS: 14.113 items, totalling 17,1 GB
Screenshot: [https://s4.postimg.org/d2aqrgbgt/FE_DE_OLD_DOCUMENTS_Screenshot.png](https://s4.postimg.org/d2aqrgbgt/FE_DE_OLD_DOCUMENTS_Screenshot.png)

Strange: 

```

jhonny@Jhonny-Lenovo-B590:~$ ls -a /home/jhonny/FE_DE_OLD DOCUMENTS
ls: cannot access '/home/jhonny/FE_DE_OLD': No such file or directory
ls: cannot access 'DOCUMENTS': No such file or directory
jhonny@Jhonny-Lenovo-B590:~$ ls -a /home/jhonny/FE_DE_OLD DOCUMENTS
ls: cannot access '/home/jhonny/FE_DE_OLD': No such file or directory
ls: cannot access 'DOCUMENTS': No such file or directory
jhonny@Jhonny-Lenovo-B590:~$

```

---

### Post by ajgreeny on 2016-08-14
Sorry, I didn't notice the space in the foldername so you need to use ```
ls -a "/home/jhonny/FE_DE_OLD DOCUMENTS"
``` which should show us if it contains all the expected folders in your home, ie all those that seem to be missing at the moment.

---

### Post by federicodemaria on 2016-08-14
Thank you

```

jhonny@Jhonny-Lenovo-B590:~$ ls -a "/home/jhonny/FE_DE_OLD DOCUMENTS"
.   Admin     Documents  Images  PEN Vero  Proyects  UAB
..  Degrowth  Foto       Others  Planning  To order  Videos
jhonny@Jhonny-Lenovo-B590:~$ 

```

---

### Post by ajgreeny on 2016-08-14
Does that look right to you; 12 subfolders in that main FE_DE_OLD DOCUMENTS folder?

If so you can simply drag and drop each of those 12 folders from the FE_DE_OLD DOCUMENTS folder back to the root of your new /home/jhonny folder using your file-manager, or if you want to keep the backups in the FE_DE_OLD DOCUMENTS folder copy/paste the subfolders instead.

---

### Post by federicodemaria on 2016-08-15
Yes, it looks right. 

My only remaining doubt regards the Folders 'Documents', 'Music' and 'Videos', that for some reasons don't work. I still get the following error message. 

Unable to find the requested file. Please check the spelling and try again.
Unhandled error message: Error when getting information for file '/home/jhonny/Documents': No such file or directory

Shall I just ignore it? I just hope it doesn't create any problems, or that there is not some partition that I'm not able to access. 

Thank you

---

### Post by ajgreeny on 2016-08-15
That's because at the moment you need to use the correct pathway in your command which would be "/home/jhonny/FE_DE_OLD DOCUMENTS/Documents" as the Documents subfolder is not in /home/jhonny but /home/jhonny/FE_DE_OLD DOCUMENTS

---

### Post by federicodemaria on 2016-08-16
I see, is there anyway I can modify it in "Files" manager? 

On the side, Open Office crashed, and when I launched it again, it was not able to recover the documents. It said: 

Object not accessible.
The object cannot be accessed
due to insufficient user rights

Could it be related with this issue? 

Thank you

---

### Post by ajgreeny on 2016-08-16
> **federicodemaria said:**
> I see, is there anyway I can modify it in "Files" manager? 

On the side, Open Office crashed, and when I launched it again, it was not able to recover the documents. It said: 

Object not accessible.
The object cannot be accessed
due to insufficient user rights

Could it be related with this issue? 

Thank you
Sorry; modify what in Files?  I don't understand what you are asking.  Were you trying to open an OOo file from that /FE_DE_OLD DOCUMENTS folder, and if so was the file owned by someone other than yourself?
Let's see the output of ```
ls -la /home/jhonny/FE_DE_OLD DOCUMENTS/Documents
``` to see who is owner of all the files in that folder, which I assume is where the OOo file came from.

---

### Post by federicodemaria on 2016-08-17
It happened while I was working on a file saved in a Cloud. Open Office collapsed, and when I re-started it was not able to recover the document. 
I don't use anymore FE_DE_OLD DOCUMENTS, in fact I now only work with the Cloud.

```

jhonny@Jhonny-Lenovo-B590:~$ ls -la /home/jhonny/FE_DE_OLD DOCUMENTS/Documents
ls: cannot access '/home/jhonny/FE_DE_OLD': No such file or directory
ls: cannot access 'DOCUMENTS/Documents': No such file or directory
jhonny@Jhonny-Lenovo-B590:~$ 

```

---

### Post by ajgreeny on 2016-08-17
> **federicodemaria said:**
> It happened while I was working on a file saved in a Cloud. Open Office collapsed, and when I re-started it was not able to recover the document. 
I don't use anymore FE_DE_OLD DOCUMENTS, in fact I now only work with the Cloud.

```

jhonny@Jhonny-Lenovo-B590:~$ ls -la /home/jhonny/FE_DE_OLD DOCUMENTS/Documents
ls: cannot access '/home/jhonny/FE_DE_OLD': No such file or directory
ls: cannot access 'DOCUMENTS/Documents': No such file or directory
jhonny@Jhonny-Lenovo-B590:~$ 

```
Silly me!  Once again I forgot about that flipping space in the folder name so we needed the "/home/jhonny/FE_DE_OLD DOCUMENTS/Documents" marks again.

Never mind that though, as the OOo file was in the cloud so we don't need to bother with that again.  As to how you deal with the crashed OOo file that is now not recoverable, I think you might be lucky if your OOo settings have backups enabled in the config folder for OOo.  I do not use OOo but LO instead which has its config in a folder in ~/.config/libreoffice so I imagine OOo will also be in .config in your home.  Look in there for a backup subfolder and you may find the last version of the file you have now lost.

If backups are not saved at the moment I suggest you change your settings to make sure that they are saved in future; it may prove helpful if this happens again.

---

### Post by federicodemaria on 2016-08-18
ajgreeny, thank you very much for all your help. It has been very usefull!

By the way, I've now enabled backups in Libre Office.

---

### Post by mook765 on 2016-08-18
The permissions off the folders in /home had been very correct as shown in fredericomaria's second post.
The folders .dbus and .gvfs and their contents should bee owned by root:root.
This is what I see in my fresh installed and still virgin system.
Kind regards...

---

