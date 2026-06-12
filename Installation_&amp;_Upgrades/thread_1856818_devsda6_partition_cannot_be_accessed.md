---
title: "/dev/sda6 partition cannot be accessed"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by csagar on 2011-10-09
Hello everyone,

I have just installed 11.04 and had partitioned by drive with:
/home - 100 GB (Partition 1)
& another partition which got named as /media/c5700b55-64cc-49e2-a02d-6cc40501291b
with another 100 GB (Partition 2)

Now I have two issues here,
1. I am not able to create, delete, move files/folders in Partition 2 drive. The drive is mounted and I tried changing the permissions with chmod 777 (not sure whether works here). But, unfortunately I am still not able to access my HUGE 100 gigs Partition 2 which just contains a single folder called 'lost+found'.

2. How can I change the weird name the partition has got by default. (I think I will be able to do that once my Issue 1 is resolved)

So, any views on how I can change my access permissions to the Partition 2 drive (with or w/o terminal).

Regards,
Sagar

---

### Post by matt_symes on 2011-10-09
Hi

> 
1. I am not able to create, delete, move files/folders in Partition 2 drive. The drive is mounted and I tried changing the permissions with chmod 777 (not sure whether works here). But, unfortunately I am still not able to access my HUGE 100 gigs Partition 2 which just contains a single folder called 'lost+found'.Open a terminal and type these two commands (with the partition mounted)

```
mount
ls -l /media

```Post the results back here between code tags.

> 2. How can I change the weird name the partition has got by default. (I think I will be able to do that once my Issue 1 is resolved)Give the partition a label.

Kind regards

---

### Post by csagar on 2011-10-09
thanks for the reply! 

after:
mount
ls -l /media

output: 
```

total 4
drwxr-xr-x 3 root root 4096 2011-10-06 16:17 c5700b55-64cc-49e2-a02d-6cc40501291b

```

---

### Post by matt_symes on 2011-10-09
Hi

First things first. Give the partition a label. 

You can do this using gparted or disc utility. If you prefer the command line then you can use tune2fs with the -L switch. Whatever you call it will become its mount point at /media so if you call it drive_2 it will be auto-mounted at /media/drive_2/

Kind regards

---

### Post by csagar on 2011-10-09
Hi there!

Well, I had initially changed the name with e2label <device> <label>, but then I tried doing it again with tune2fs which results the same. Cool, now I know 2 ways to label a drive!! 

Having said that, it does show me the new label 'MyDrive' on the graphic display but when I

```
df -h
```it still shows me /media/c5700b55-64cc-49e2-a02d-6cc40501291b as its name.

The partition is already mounted on /mnt/drive.

Can we jump to access thing now?? Please correct me if I seem lost!

---

### Post by matt_symes on 2011-10-09
Hi

> Can we jump to access thing now?? Please correct me if I seem lost!

You should be able to chown and chmod the mount point.

> Having said that, it does show me the new label 'MyDrive' on the graphic display but when I
 	df -h
it still shows me /media/c5700b55-64cc-49e2-a02d-6cc40501291b as its name.

The partition is already mounted on /mnt/drive.

I am really confused about these statements. How is the partition mounted under /mnt/drive and /media.

Can you post the entire output of all these commands with the drive plugged in.

```
df -h
mount
sudo blkid
groups
```

Kind regards

---

### Post by csagar on 2011-10-09
Ahh, I am sorry for the confusion. There just cannot be two mount points like /mnt & /media for the same drive right?

```
df -h
```

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              19G  4.7G   13G  27% /
none                  1.9G  684K  1.9G   1% /dev
none                  1.9G  456K  1.9G   1% /dev/shm
none                  1.9G  272K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
/dev/sda5              92G  1.6G   86G   2% /home
/dev/sda6              91G  188M   86G   1% /media/c5700b55-64cc-49e2-a02d-6cc40501291b
/dev/sda6              91G  188M   86G   1% /mnt/drive


```
mount
```

> 
/dev/sda7 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda5 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sagar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sagar)
/dev/sda6 on /media/c5700b55-64cc-49e2-a02d-6cc40501291b type ext4 (rw,nosuid,nodev,uhelper=udisks,commit=600,commit=0,commit=600,commit=0,commit=600,commit=0,commit=0,commit=600,commit=0,commit=0,commit=0,commit=0,commit=0)
/dev/sda6 on /mnt/drive type ext4 (rw,commit=600,commit=0,commit=600,commit=0,commit=600,commit=0,commit=0,commit=600,commit=0,commit=0,commit=0,commit=0,commit=0)


```

sudo blkid
```

> 
/dev/sda1: SEC_TYPE="msdos" LABEL="DELLUTILITY" UUID="3030-3030" TYPE="vfat" 
/dev/sda5: UUID="9ba29b4a-eeeb-41fc-9577-15e45d014c00" TYPE="ext4" 
/dev/sda6: LABEL="MyDrive" UUID="c5700b55-64cc-49e2-a02d-6cc40501291b" TYPE="ext4" 
/dev/sda7: UUID="81c87458-8827-4349-9143-efc34008d848" TYPE="ext4" 
/dev/sda8: UUID="dca06d50-08f1-47ae-831f-53e6e8106c40" TYPE="swap" 


```

groups
```

> 
sagar adm dialout cdrom plugdev lpadmin admin sambashare



Bingo! I confused you because I was myself confused in assuming /mnt/drive as the mount point of the /MyDrive partition. By, CHMODing the /media/c5700b55-64cc-49e2-a02d-6cc40501291b drive I finally got an access inside!

Thanks Matt, for pointing that out! Any tips to conclude this thread are MOST welcomed! 
:guitar:

---

### Post by matt_symes on 2011-10-09
Hi

You have it mounted at two places. Just let it auto mount under /media.

Did you edited your /etc/fstab file to mount it under /mnt. If so remove that entry.

If you post your /etc/fstab file then i will take a look for you

Kind regards

---

### Post by csagar on 2011-10-09
> 
You have it mounted at two places. Just let it auto mount under /media.


I have UNMOUNTed & removed the /mnt/drive point having just one auto mount point under /media.

> 
Did you edited your /etc/fstab file to mount it under /mnt. If so remove that entry.

If you post your /etc/fstab file then i will take a look for you


I haven't modified the /etc/fstab file, the output is

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=81c87458-8827-4349-9143-efc34008d848 /               ext4    errors=remount-ro 0       1
/dev/sda5       /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=dca06d50-08f1-47ae-831f-53e6e8106c40 none            swap    sw              0       0

```

Doesn't seem to have changed right? Thanks Again!! :)

---

### Post by matt_symes on 2011-10-09
Hi

It looks like you are good to go.

Kind regards

---

