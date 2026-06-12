---
title: "Formatting external drive in ext3"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by sven 22 on 2011-08-01
Hello,

As a user with modest skills, I'm trying to format a 500 GB external drive with gparted in ubuntu 10.10 (I searched & didn't see this issue in the forum).

I set up and formatted two partitions, one for fat32, and the other with ext3, which appears to format ok, but I can't use it.

Both partitions show up and appear to mount, but the ext3 partition won't accept activity (make new folder, copy in files), while the fat32 partition works fine.

Both partitions show up ok when I query in terminal "sudo fdisk -l"

Can someone explain the problem? It must be something simple. I had the same results trying to partition and format as ext4. 

Thanks in advance!

Sven

---

### Post by karlson on 2011-08-01
> **sven 22 said:**
> 
Can someone explain the problem?

Can you post output of
```

mount

```

Did you you even mount it?

---

### Post by tsucol11 on 2011-08-01
# Sven 22 please read the follow page 

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive).

# I used it to set up an external drive, then use:

sudo chown -R USERNAME:USERNAME /media/yourmynewdrive

# you also need to have a your my new drive folder under  

 /media/yourmynewdrive  so it will auto mount

Brian



> **sven 22 said:**
> Hello,

As a user with modest skills, I'm trying to format a 500 GB external drive with gparted in ubuntu 10.10 (I searched & didn't see this issue in the forum).

I set up and formatted two partitions, one for fat32, and the other with ext3, which appears to format ok, but I can't use it.

Both partitions show up and appear to mount, but the ext3 partition won't accept activity (make new folder, copy in files), while the fat32 partition works fine.

Both partitions show up ok when I query in terminal "sudo fdisk -l"

Can someone explain the problem? It must be something simple. I had the same results trying to partition and format as ext4. 

Thanks in advance!

Sven

---

### Post by sven 22 on 2011-08-01
> **karlson said:**
> Can you post output of
```

mount

```

Did you you even mount it?

Oh! does one need to mount it specially, as one does with a CD player, similar to 

sudo mkdir /media/CD
sudo mount /dev/cdrom /media/CD

here's the output. The partition in question is /dev/sdb2

/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda6 on /tmp type ext4 (rw,commit=0)
/dev/sda1 on /boot type ext4 (rw,commit=0)
/dev/sda3 on /usr type ext4 (rw,commit=0)
/dev/sda5 on /var type ext4 (rw,commit=0)
/dev/sda7 on /home type ext4 (rw,commit=0)
/dev/sda8 on /data type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/sven/.Private on /home/sven type ecryptfs (ecryptfs_sig=394b4c3aa138984b,ecryptfs_fnek_sig=1e7b8dbb7c7765e7,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/sven/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sven)
/dev/sdb1 on /media/9C36-5723 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb2 on /media/da2f0a71-c925-4a04-b28d-1e03a73b9698 type ext3 (rw,nosuid,nodev,uhelper=udisks)

---

### Post by sven 22 on 2011-08-01
> **tsucol11 said:**
> # Sven 22 please read the follow page 

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive).

# I used it to set up an external drive, then use:

sudo chown -R USERNAME:USERNAME /media/yourmynewdrive

# you also need to have a your my new drive folder under  

 /media/yourmynewdrive  so it will auto mount

Brian

OK thanks, Brian.
I'll try that.

I tried to set it up manually but that didn't work.
Hmmm...I'll try to "have the new drive folder under /media/yourmynewdrive" but I don't quite know how to do that. Anyway, I'll give it a go.

sven


I

---

