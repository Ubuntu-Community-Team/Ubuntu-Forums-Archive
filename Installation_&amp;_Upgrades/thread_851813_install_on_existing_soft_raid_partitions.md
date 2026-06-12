---
title: "install on existing soft raid partitions"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by jpkotta on 2008-07-07
I have a rather complicated setup.  My disks are partitioned and the partitions are combined into either raid0 or raid1 arrays (software raid).  I am not using dmraid or any sort of BIOS fakeraid.  I would like to install Gutsy (yes, it must be Gutsy) on exactly one of these arrays (/dev/md3), without touching the others.  AFAIK, I need the alternate CD, but it doesn't seem possible without nuking the whole disk.  The live CDs (alternate or desktop + some additional fiddling) both see the raid arrays, but the installers refuse to let me install to them.  Is this a known limitation?  Is there a workaround?  I think when I installed, I just used the (Xubuntu Gutsy) alternate CD, and I didn't care about nuking the drives because they were blank.

```
[jpkotta@gauss][~][0]
$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md4 : active raid1 sda9[0] sdb9[1]
      196233856 blocks [2/2] [UU]
      
md3 : active raid1 sda8[0] sdb8[1]
      15623104 blocks [2/2] [UU]
      
md2 : active raid0 sda7[0] sdb7[1]
      31245824 blocks 256k chunks
      
md5 : active raid0 sda6[0] sdb6[1]
      15614976 blocks 64k chunks
      
md1 : active raid0 sda5[0] sdb5[1]
      15630976 blocks 64k chunks
      
md0 : active raid1 sda1[0] sdb1[1]
      96256 blocks [2/2] [UU]
      
unused devices: <none>

```

```
[jpkotta@gauss][~][0]
$ mount
/dev/md1 on / type ext3 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/md3 on /archive type ext3 (rw,noatime)
/dev/md0 on /boot type ext3 (rw,noatime)
/dev/md4 on /home type ext3 (rw,noatime)
/dev/md2 on /virtual type ext3 (rw,noatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

---

### Post by jpkotta on 2008-07-11
nudge

---

### Post by Nero147 on 2008-07-11
When you say that you aren't using dmraid or any type of softraid do you mean that you're using hardware raid controllers? and if so what are you using?

---

### Post by Nero147 on 2008-07-11
I only ask because I used to use a PCI raid card for my raid 0 setup. I used the fakeraid setup for it, and it let me see it and not alter my other installs, the walkthrough I used was this one. [http://ubuntuforums.org/showthread.php?t=630644](http://ubuntuforums.org/showthread.php?t=630644)
It also fits your needs of Gutsy.

---

### Post by jpkotta on 2008-07-13
> **Nero147 said:**
> When you say that you aren't using dmraid or any type of softraid do you mean that you're using hardware raid controllers? and if so what are you using?

No, I'm using Linux softraid (md_mod, mdadm, etc.).  My BIOS is capable of fakeraid, but I opted not to use it, because I don't have a Windows installation (and as I understand it, fakeraid is mainly for compatibility amongst different OSes).  Anyway, I tried installing dmraid and letting it detect my devices, and it didn't work.

---

