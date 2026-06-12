---
title: "hardy upgrade: grub boot error 15"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by kosmos on 2008-06-16
[problem has been solved. My BIOS had an incorrect disk config, changing it from 2,1,3 back to 1,2,3 fixed the problem. I had been unknowingly booting from sdb, but mounting from sda when I really needed to boot from sda]



I just did an upgrade from Gutsy to Hardy. When I rebooted, I got an error 15 from grub as it tried to boot the default kernel ( 2.6.24-18 ). So I tried some other entries in the grub menu and kernel 2.6.22-14 boots up ok. I've googled around and tried to figure this out, but I'm stumped and feeling dunderpated. I've seen plenty of people report error 15 related problems from grub, but it's usually a case of dual boot with Windows, or with a mix of IDE and SATA drives, not when there are 2 very similar kernel entries where one entry works and another doesn't.
(I do have 3 SATA drives, sda, sdb and sdc, but I've elided some entries from the listings below, hoping to be concise).

I have separate boot and root partitions, and use volume labels:

/etc/fstab:
```

LABEL=root	/               ext3    defaults,errors=remount-ro 0       1
LABEL=boot	/boot           ext3    defaults        0       2

```
fdisk -l /dev/sda:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   83  Linux
/dev/sda2              12         985     7823655   83  Linux
/dev/sda3             986       91201   724660020   83  Linux

```
blkid shows:
```
/dev/sda1: LABEL="boot" UUID="9658158b-70ab-4891-9a40-553cd653d2c4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: LABEL="root" UUID="752de295-93d5-496b-b189-031157bc769b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="134991a7-bb16-4327-a678-f88117333e78" TYPE="crypt_LUKS" 
/dev/sdb1: LABEL="boot2" UUID="9658158b-70ab-4891-9a40-553cd653d2c4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: LABEL="root2" UUID="752de295-93d5-496b-b189-031157bc769b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: LABEL="data2" UUID="5f1226f7-8c3d-4413-84ad-8059aabc46eb" SEC_TYPE="ext2" TYPE="ext3" 

```
/boot contains:
```

 -rw-r--r--  1 root root 1052627 Feb 11 22:30 System.map-2.6.22-14-generic
 -rw-r--r--  1 root root 1152174 May 28 18:56 System.map-2.6.24-18-generic
 -rw-r--r--  1 root root  417807 Feb 11 22:30 abi-2.6.22-14-generic
 -rw-r--r--  1 root root  420224 May 28 18:56 abi-2.6.24-18-generic
 -rw-r--r--  1 root root   67666 Feb 11 22:30 config-2.6.22-14-generic
 -rw-r--r--  1 root root   74186 May 28 18:56 config-2.6.24-18-generic
 -rw-r--r--  1 root root 8274005 Jun 15 19:51 initrd.img-2.6.22-14-generic
 -rw-r--r--  1 root root 8709617 Jun 15 22:36 initrd.img-2.6.24-18-generic
 -rw-r--r--  1 root root 1743752 Feb 11 22:30 vmlinuz-2.6.22-14-generic
 -rw-r--r--  1 root root 1903448 May 28 18:56 vmlinuz-2.6.24-18-generic

```
/boot/grub contains:
```

 -rw-r--r-- 1 root root    197 Jun 16 08:00 default
 -rw-r--r-- 1 root root     30 Sep 20  2007 device.map
 -rw-r--r-- 1 root root   8056 Jun 16 08:00 e2fs_stage1_5
 -rw-r--r-- 1 root root   7904 Jun 16 08:00 fat_stage1_5
 -rw-r--r-- 1 root root     16 Jun 16 08:00 installed-version
 -rw-r--r-- 1 root root   8608 Jun 16 08:00 jfs_stage1_5
 -rw-r--r-- 1 root root   5149 Jun 15 22:33 menu.lst
 -rw-r--r-- 1 root root   7324 Jun 16 08:00 minix_stage1_5
 -rw-r--r-- 1 root root   9632 Jun 16 08:00 reiserfs_stage1_5
 -rw-r--r-- 1 root root    512 Jun 16 08:00 stage1
 -rw-r--r-- 1 root root 108356 Jun 16 08:00 stage2
 -rw-r--r-- 1 root root   9276 Jun 16 08:00 xfs_stage1_5

```
The 2 relevant entries from my menu.lst:
```

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-18-generic root=LABEL=root ro 
initrd		/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=LABEL=root ro 
initrd		/initrd.img-2.6.22-14-generic
quiet

```
I don't understand why root is specified as (hd0,0), I would expect it to be (hd0,1), since / is on /dev/sda2. I would also expect booting 2.6.22-14 to fail, because it uses the same specification as 2.6.24-18, but it doesn't fail, it boots fine. I've tried making a test entry in menu.lst, changing hd0,0 to hd0,1:
```

title		TEST Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-18-generic root=LABEL=root ro 
initrd		/initrd.img-2.6.24-18-generic
quiet

```
But this also gives a grub error 15.

I do vaguely remember some boot issues with past upgrades, and perhaps I confused things by dd'ing my /dev/sda1, /dev/sda2 to /dev/sdb1, /dev/sdb2 (respectively, for backup) in the past, but I thought I had straightened those issues out a long time ago, and I had fixed things up the way I like with a simple partitoning and volume labels.

So, I'm stuck and I really need some enlightenment. Please help I'm going nuts! Thanks.

---

### Post by meierfra. on 2008-06-16
Is your /boot partition mounted correctly? Post the output of

```
mount
```

Also you might mount sda1 directly and look at its content:


```
mkdir sda1
sudo mount /dev/sda1 sda1
ls sda1 
```

---

### Post by kosmos on 2008-06-16
Okey dokey, here's mount:
```
% mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /boot type ext3 (rw)
/dev/mapper/vgcrypt-home on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

And here's a direct look at what's there:
```

# mkdir sda1
# mount /dev/sda1 sda1
# ls -al sda1
total 58227
drwxr-xr-x  4 root root    1024 Jun 16 11:48 .
drwxrwxrwt 12 root root    4096 Jun 16 13:01 ..
-rw-r--r--  1 root root 1033618 Sep 23  2007 System.map-2.6.20-16-generic
-rw-r--r--  1 root root 1052627 Feb 11 22:30 System.map-2.6.22-14-generic
-rw-r--r--  1 root root 1152174 May 28 18:56 System.map-2.6.24-18-generic
-rw-r--r--  1 root root  407163 Sep 23  2007 abi-2.6.20-16-generic
-rw-r--r--  1 root root  417807 Feb 11 22:30 abi-2.6.22-14-generic
-rw-r--r--  1 root root  420224 May 28 18:56 abi-2.6.24-18-generic
-rw-r--r--  1 root root   75332 Sep 23  2007 config-2.6.20-16-generic
-rw-r--r--  1 root root   67666 Feb 11 22:30 config-2.6.22-14-generic
-rw-r--r--  1 root root   74186 May 28 18:56 config-2.6.24-18-generic
drwxr-xr-x  2 root root    1024 Jun 16 12:11 grub
-rw-r--r--  1 root root 7720481 Oct  3  2007 initrd.img-2.6.20-16-generic
-rw-r--r--  1 root root 7720772 Oct  3  2007 initrd.img-2.6.20-16-generic.bak
-rw-r--r--  1 root root 8274005 Jun 15 19:51 initrd.img-2.6.22-14-generic
-rw-r--r--  1 root root 8028734 May 28 17:21 initrd.img-2.6.22-14-generic.bak
-rw-r--r--  1 root root 8709657 Jun 16 11:48 initrd.img-2.6.24-18-generic
-rw-r--r--  1 root root 8709824 Jun 15 22:33 initrd.img-2.6.24-18-generic.bak
drwx------  2 root root   12288 Sep 20  2007 lost+found
-rw-r--r--  1 root root  103204 Sep 28  2007 memtest86+.bin
-rw-r--r--  1 root root 1725110 Sep 23  2007 vmlinuz-2.6.20-16-generic
-rw-r--r--  1 root root 1743752 Feb 11 22:30 vmlinuz-2.6.22-14-generic
-rw-r--r--  1 root root 1903448 May 28 18:56 vmlinuz-2.6.24-18-generic

```

It all looks as expected, doesn't it?

---

### Post by meierfra. on 2008-06-16
Everything looks perfect (It has to be "root (hd0,0)" since that's where the kernel is stored)

Couple of things to try:

1) File system check

```
sudo umount /dev/sda1
sudo e2fsck -C0  -fvy /dev/sda1
```

2)  Reinstall the new kernel.

---

### Post by kosmos on 2008-06-16
> **meierfra. said:**
> 
2)  Reinstall the new kernel.

What is the standard Ubuntu way to do this?

(apt-get --reinstall install linux-image-2.6.24-18-generic) ?

Thanks

---

### Post by meierfra. on 2008-06-16
I would do:

```
apt-get purge  linux-image-2.6.24-18-generic
apt-get install  linux-image-2.6.24-18-generic
```

(this way the packages will be downloaded again)

---

### Post by kosmos on 2008-06-16
Well, I did the fsck on /dev/sda1. No problems.

I did the apt-get purge and install.
I reboot, grub gives the same story:

Kernel 2.6.24-18 fails with error 15.
Kernel 2.6.22-14 boots ok.

Something is subtly wrong with my system, and my eyeballs are spinning around from looking for it but not finding it.

---

### Post by meierfra. on 2008-06-16
Do you know  which file is not found?

Try this:

At the grub menu  at boot up press "c".  

Then type

 ```
root (hd0,0)

find /initrd.img-2.6.24-18-generic

find /vmlinuz-2.6.24-18-generic 
```

---

### Post by kosmos on 2008-06-16
> **meierfra. said:**
> Do you know  which file is not found?

Try this:


Aha! Neat trick. I didn't know that.
The plot thickens:

root (hd0,0)
find /initrd.img-2.6.24-18-generic
Returns: (hd1,0)

find /vmlinuz-2.6.24-18-generic
Returns: (hd1,0)

Not what I expected. hd1 is my /dev/sdb isn't it?

---

### Post by meierfra. on 2008-06-16
> Not what I expected. hd1 is my /dev/sdb isn't it?


Yes. Are you using any kind of raid?

Also sda1 and sdb1 have the same UUID. You can assign a random UUID via

```
sudo tune2fs -U random /dev/sdb1
```

But I don't see how the UUID's  could  cause your problem.


You might also mount /dev/sdb1 and see what is on there.

---

### Post by meierfra. on 2008-06-16
((Edit: forget about this post. I misread post #9)

Just another thought:  Try

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		(hd1,0)/vmlinuz-2.6.24-18-generic root=LABEL=root ro 
initrd		(hd0,0)/initrd.img-2.6.24-18-generic
quiet


(But even if this works, you  should still try  to find the real cause of the problem, rather than cheat your way around it)

---

### Post by kosmos on 2008-06-16
> **meierfra. said:**
> Yes. Are you using any kind of raid?
I don't believe so. I did a long time ago, but turned it off, as it didn't fit my needs.

> Also sda1 and sdb1 have the same UUID. You can assign a random UUID via

Thanks. I'll reset the UUID on /dev/sdb1. 

> You might also mount /dev/sdb1 and see what is on there.
The stuff there and the duplicate UUID are, I believe, due to my long ago dd'ing a copy of sda1 to sdb1, for backup purposes. Maybe it has caused some confusion to do it that way.

---

### Post by meierfra. on 2008-06-16
> The stuff there and the duplicate UUID are,

But is the new kernel on there?


> don't believe so. I did a long time ago, but turned it off, as it didn't fit my needs.


Check the setting in your bios and see whether there is  anything which might cause the problem.

Did you see my post #11?

---

### Post by kosmos on 2008-06-16
> **meierfra. said:**
> But is the new kernel on there?
[...]
Did you see my post #11?

I mounted /dev/sdb2 on /mnt/foo and 

```
% ls -al /mnt/foo
total 37611
drwxr-xr-x  4 root root    1024 Oct 29  2007 .
drwxr-xr-x 13 root root    4096 Apr 10 22:15 ..
-rw-r--r--  1 root root 1033618 Sep 23  2007 System.map-2.6.20-16-generic
-rw-r--r--  1 root root 1052596 Oct 14  2007 System.map-2.6.22-14-generic
-rw-r--r--  1 root root  407163 Sep 23  2007 abi-2.6.20-16-generic
-rw-r--r--  1 root root  417807 Oct 14  2007 abi-2.6.22-14-generic
-rw-r--r--  1 root root   75332 Sep 23  2007 config-2.6.20-16-generic
-rw-r--r--  1 root root   67666 Oct 14  2007 config-2.6.22-14-generic
drwxr-xr-x  2 root root    1024 Oct 29  2007 grub
-rw-r--r--  1 root root 7720481 Oct  3  2007 initrd.img-2.6.20-16-generic
-rw-r--r--  1 root root 7720772 Oct  3  2007 initrd.img-2.6.20-16-generic.bak
-rw-r--r--  1 root root 8219311 Oct 29  2007 initrd.img-2.6.22-14-generic
-rw-r--r--  1 root root 8037314 Oct 29  2007 initrd.img-2.6.22-14-generic.bak
drwx------  2 root root   12288 Sep 20  2007 lost+found
-rw-r--r--  1 root root  103204 Sep 28  2007 memtest86+.bin
-rw-r--r--  1 root root 1725110 Sep 23  2007 vmlinuz-2.6.20-16-generic
-rw-r--r--  1 root root 1743368 Oct 14  2007 vmlinuz-2.6.22-14-generic

```

So, no, the new kernel is not there. But the one I can succesfully boot is there.

Yes, I just tried your new kernel stanza in my menu.lst. I put a unique title to make sure I was seeing the right one. I selected it at boot, and I still get the error 15.

I will go check my BIOS.

I must admit I am very confused at this point. I hope I have not made a mistake and mis-reported my system. I'll start double checking things.

---

### Post by meierfra. on 2008-06-16
I think you are booting from /dev/sdb.

Try changing the boot order in the bios.

( I had misread your post #9, somehow I thought one of the output was "(hd0,0)" and the other (hd1,0)").  But since they both are (hd1,0),  you are almost certainly booting from /dev/sdb)

---

### Post by kosmos on 2008-06-16
GAH!

It was the bloody BIOS. Somehow, back in the past, the disks were set to 2,1,3. I reset them to 1,2,3 and now everything works as expected.

The thing that prevented me from ever really seeing a problem in the past was the duplicate copy I'd made on sdb, of course. So all along I've been booting from sdb, and mounting from sda. It was all cool up until an upgrade changed the kernel grub was looking for.

As Homer Simpson would say: D'oh!

Many thanks, meierfra.

---

### Post by meierfra. on 2008-06-16
>  Somehow, back in the past, the disks were set to 2,1,3. I reset them to 1,2,3 and now everything works as expected.

Glad you got it to work. I  did enjoy  solving this little mystery.

> 
So all along I've been booting from sdb, 
As you can see from my previous post I had come to the same conclusion :)

---

### Post by kosmos on 2008-06-16
> **meierfra. said:**
> Glad you got it to work. I  did enjoy  solving this little mystery.

 
As you can see from my previuos post I had come to the same conclusion :)
I owe you a beer or 12.

---

