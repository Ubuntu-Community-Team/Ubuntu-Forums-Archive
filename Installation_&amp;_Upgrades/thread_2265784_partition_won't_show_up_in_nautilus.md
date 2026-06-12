---
title: "partition won't show up in nautilus"
date: 2015-02-17
forum: Installation &amp; Upgrades
---

### Post by Hamburgian on 2015-02-17
I recently gave up trying to fix a number of problems - dodgy wifi - Virtual Box interfering with Nvidia among others. I guessed it was due to a complicated setup with two OSes each with it's own home 'folder' on one partition and a shared 'home' folder for documents, downloads and other files both OSes could use.
So I got a new hard drive, cloned my existing drive (my current Hard rive is nearing the end of it's life), then set about changing the partiton table and doing a clean install...perhaps here was my error...I set the fresh install to NOT FORMAT the / partition or the /home partition...but everything worked fine while both disks were installed.

Now I've disconnected the new 'clone' and one of my partitions (sda4...that was sdb4 during the installation) is not showing up anywhere and I cannot access it apart from opening 'disks' and clicking on the mount point /STORAGE

I've checked the /etc/fstab and /etc/mtab and everything seems to be in order....I'm attaching them in case I've missed something

sudo blkid returns
```
/dev/sda1: UUID="d1b5e6b6-8d96-4993-9fb2-ed1f0dcbfea2" TYPE="ext4" 
/dev/sda2: UUID="f87bb51b-bbcf-4249-898e-dc98cc0e10a3" TYPE="ext4" 
/dev/sda3: UUID="df258937-6764-4da2-a48b-a2139282d7b6" TYPE="swap" 
/dev/sda4: LABEL="STORAGE" UUID="487dcf18-abea-4072-a7bd-bb594223f490" TYPE="ext4" 

```

my /etc/fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=d1b5e6b6-8d96-4993-9fb2-ed1f0dcbfea2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=f87bb51b-bbcf-4249-898e-dc98cc0e10a3 /home           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=df258937-6764-4da2-a48b-a2139282d7b6 none            swap    sw              0       0
# /STORAGE was on /dev/sdb4 during installation
UUID=487dcf18-abea-4072-a7bd-bb594223f490 /STORAGE        ext4    defaults        0       2
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

my /etc/mtab
```
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
none /sys/fs/pstore pstore rw 0 0
/dev/sda4 /STORAGE ext4 rw 0 0
/dev/sda2 /home ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=mark 0 0
gvfsd-fuse /home/mark/.gvfs fuse.gvfsd-fuse rw,nosuid,nodev 0 0
```


One thing that makes me think the problem arises from the installation method is my /media  directory shows all the partitions from the 'old' installation.../home /WORK and /STORAGE...but each with a size of 36.7 Gb and each empty.

I've not really got much idea of mtab settings, so perhaps there's something I'm missing there, but fstab looks ok to me.....where have I gone wrong? And is there any way to sort this out or do I need to do a whole fresh install?

---

### Post by nerdtron on 2015-02-18
Reading the first paragraphs seems a lot was wrong for me. Sorry no offense. Just that it would seem complicated when two linux OS shared ANY default system folder, including /home.
Especially this one, which could cause a lot of problems on reinstalling the new OS.
> I set the fresh install to NOT FORMAT the / partition or the /home  partition...but everything worked fine while both disks were installed.


I can't comment on how to fix your problem but I have a suggestion on your future builds. 
Based from my experience (and lots of thread here on dual booting problems), the best way to share data on two linux OS is to not share any system folder at all.

I mean don't create separate /home partition and share it on both. /home folder contains hidden files and settings specific to user and the OS. This can cause conflict on two OS setup.

The best way to approach this is to share a folder that is not owned by the system. Just install you two OS on their own / partitions. Now create another partition and name it DATA partition. You will mount this partition on /mnt/data or just /data. This is not a system folder and any file you put there can be shared by the two OS happily. 
This type of setup has always worked for me to both windows linux dual boots. even triple boot linux.

Remember, separate (dedicate) a DATA partition that you can share on all OSes. Then forget about /, /home or other partitions, you can just FORMAT those partitions and all your data is still on a separate partition /data.

---

### Post by Hamburgian on 2015-02-18
Thanks for the info Nerdtron...but it wasn't quite as hare-brained as it seems from what I've written. I simply followed posts to move a home partition..apparently you can also set a /home partition as a "/home" folder within another partition. 
[URL="http://askubuntu.com/questions/473916/moving-home-to-an-existing-directory"]
http://askubuntu.com/questions/473916/moving-home-to-an-existing-directory[/URL]
I did this twice, one as /home64 for the 64 bit OS and another for a 32bit OS../home32. I then made another folder /home and put all my documents, pdfs, pictures, videos downloads etc. there and used Tweak to point the two /homes to these folders. This worked perfectly well for 6 months or so until I installed Virtual Manager...then came an update which threw everything out of kilter..so I obviously didn't do it perfectly :(.

The whole point of doing this was to 'protect' my /home folders in case of having to do a fresh install. The fresh install deleted EVERYTHING in the /home folders...in fact everything on the partition...luckily I had a current backup thanks to the clone...but managed to leave some files in the / partition. I guess a fresh install with formatting is the way I'll have to go...but this will have to wait until next month when I get more internet allowance...the updates took over 5GB.

I have found some odd settings in my /lib/udev/rules.d...with UUIDs from the clone and not the current disk...so I need to find a way to edit these and perhaps that will sort this mess out.

---

### Post by Hamburgian on 2015-02-19
Simple....I did 
> sudo rmdir /media/home 
sudo rmdir /media/WORK
sudo rmdir /media/STORAGE
to remove the 'old' directories from my /media folder
This removed the line 
> gvfsd-fuse /home/mark/.gvfs fuse.gvfsd-fuse rw,nosuid,nodev 0 0
from my /etc/mtab I have no idea if this was any way important

Then changed the mount point for the current /STORAGE  to /media/STORAGE in my /etc/fstab....et voila...the partition shows up in nautilus and I can access and edit data

---

