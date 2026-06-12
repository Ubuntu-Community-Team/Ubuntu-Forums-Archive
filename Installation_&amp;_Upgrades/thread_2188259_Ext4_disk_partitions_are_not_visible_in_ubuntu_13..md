---
title: "Ext4 disk partitions are not visible in ubuntu 13.10"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by gokulsurendiran on 2013-11-16
I was using 12.10 earlier(single OS), trying to get it updated to 13.04 & it got crashed due to power failure.

So I decided to do a fresh installation of 13.10 and formatted to 2 partitions 
/home - 50 GB
/ - 200 GB 

thinking I can use /home to install OS & other partition for other files like in Windows.

/ folder shows 180 GB but I'm not able to save any files!

Could some one explain whether my thinking was right or wrong? & where do I save my files now.

Thanks in advance!

---

### Post by coffeecat on 2013-11-16
"/home" refers to either a separate home partition or the home folder within your root partition if you have no separate home partition. It sounds as though you have installed your system to the 50GB partition which would make it your root or '/' partition, so calling it /home is a misnomer.

Anyway - if the 200GB partition is intended as a data partition, this is a simple ownership/permissions issue which is easily fixed. Make sure the 200GB partition is mounted, and then post the output of these terminal commands:

```
sudo fdisk -lu
blkid
mount
```

Please include the full terminal prompt with your output - that way I can give you the exact command to take ownership of the partition. Also - how are you mounting the 200GB partition, from the file manager or Uniity launcher, or have you added a line to /etc/fstab?

---

### Post by gokulsurendiran on 2013-11-16
this was the output.

```
bannu@Daffo:~$ sudo fdisk -lu
[sudo] password for bannu: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000516b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3999743     1998848   82  Linux swap / Solaris
/dev/sda2         3999744   101656575    48828416   83  Linux
/dev/sda3       101658622   488396799   193369089    5  Extended
/dev/sda5       101658624   488396799   193369088   83  Linux
```
```
bannu@Daffo:~$ blkid
```
```
bannu@Daffo:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda2 on /home type ext4 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=bannu)
```

for the second part - didn't know to mount!

---

### Post by coffeecat on 2013-11-16
I've enclosed your three outputs in code tags. They're difficult to read and you lose formatting otherwise. When asked to post terminal output, you can use code tags by highlighting the output in the advanced message editor, and then clicking on the icon that looks like a # in the message toolbar.

My apologies &#8211; I should have asked for &#8220;sudo blkid&#8221; instead of blkid, but not to worry. I think we have enough information to be going on with.

Don't worry about the how did you mount question &#8211; I can work out the answer from your posted output.

Your system is as follows:

sda2 &#8211; 50GB (46.6 GiB, gibibytes) &#8211; this is your home partition.

sda5 &#8211; 198GB (184.4 GiB,  gibibytes) &#8211; this is your root (/) partition.

You do have a separate home partition and you were right to say the 50GB partition was /home, but what threw me was the relative sizes for the two partitions, and that you said the OS was in /home. The partition sizes are not a good choice. Your /home partition needs to be much larger than your root partition because you are likely to have to store large files in your /home. Your root really only needs to be about 20GB (or possibly less) when you have a separate /home partition.

In your original post you say that you cannot store any files in your 198GB partition, which is the root partition. You shouldn't be having to &#8211; that's where all the system files are. What are you trying to save?

Perhaps more importantly: before you spend much more time on this installation, it might be a good idea to think about repartitioning and reinstalling. You have an inefficient use of your available hard drive space which you may find limiting with a 50GB home partition.

---

### Post by gokulsurendiran on 2013-11-16
> **coffeecat said:**
> 

In your original post you say that you cannot store any files in your 198GB partition, which is the root partition. You shouldn't be having to – that's where all the system files are. What are you trying to save?

Perhaps more importantly: before you spend much more time on this installation, it might be a good idea to think about repartitioning and reinstalling. You have an inefficient use of your available hard drive space which you may find limiting with a 50GB home partition.

I was actually trying to save outside the home folder.

So should I make the home partition 230 GB & root partition 20 GB?

---

### Post by heir4c on 2013-11-16
As you see the bootflag (the * you see below) is on the swap partition and that is a strange situation:
> /dev/sda1   *        2048     3999743     1998848   82  Linux swap / Solaris
So make a new install.

In a 'normal' install you have 2 partitions. One for the root (the / partition) and one for a swap.
If you want a separated partition for your data than you can name it /DATA when you make the partitions via GParted (PartitionManager) in the live-session before you run the Ubuntu-Installation.
Create a / partition of 25GB
a swap partition size: RAM+500MB
and a /DATA partition of the rest of the Disk.(You can create a /home partition instead of a /DATA partition to set your documents, downloads, photo's etc in. Than you have your Personal folder on that partition)
Create your swap partition at the end of the disk.

---

### Post by fantab on 2013-11-16
Have you succeded in 'SAVING' your data? Before you do anything with your partitions **BACKUP All your important data**.

'boot' flags don't really matter with Linux/Grub. However, you don' t need put your SWAP partition upfront, like heir4c suggests put it at the end of the disk.
Also I don't think you need an Extended Partition, if you keep yourself to only FOUR primary partitions.
If I were you, I would  partition my 250GB HDD, which will have only Ubuntu, in the following manner:
> 20GB Primary Ext4 '/' (to keep Ubuntu system files).
20GB Primary Ext4     (Noting installed, Free in case I want to install another version or flavor of Ubuntu or any other distro)
4GB Primary SWAP (The Size of SWAP can be smaller if you don't use 'Hibernate', if you do then RAMGB+500mb, heir4c suggest is good).
206GB Primary Ext4 [either /home or just a simple data partition, that is, no mountpoint used.]


---

### Post by coffeecat on 2013-11-17
> **gokulsurendiran said:**
> I was actually trying to save outside the home folder.

Again, why? With your setup, that would have been in the root partition and, unless you were trying to do some re-configuration of system files, that's not the place to save things.

> **heir4c said:**
> As you see the bootflag (the * you see below) is on the swap partition and that is a strange situation:

And one that doesn't matter. Linux booting with grub does not use the boot flag and with a system that doesn't have Windows, the boot flag is an irrelevance and can be ignored.

---

### Post by heir4c on 2013-11-17
ThanX for the Grub info!!! 
I did not know. I'm using Ubuntu for 5 years now but I'm not a expert and that is a more technical issue.

---

### Post by gokulsurendiran on 2013-11-20
> **heir4c said:**
> As you see the bootflag (the * you see below) is on the swap partition and that is a strange situation:

So make a new install.

In a 'normal' install you have 2 partitions. One for the root (the / partition) and one for a swap.
If you want a separated partition for your data than you can name it /DATA when you make the partitions via GParted (PartitionManager) in the live-session before you run the Ubuntu-Installation.
Create a / partition of 25GB
a swap partition size: RAM+500MB
and a /DATA partition of the rest of the Disk.(You can create a /home partition instead of a /DATA partition to set your documents, downloads, photo's etc in. Than you have your Personal folder on that partition)
Create your swap partition at the end of the disk.


Thanks guys guys, followed this & it worked!

---

