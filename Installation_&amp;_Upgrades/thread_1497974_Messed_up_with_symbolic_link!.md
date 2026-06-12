---
title: "Messed up with symbolic link!"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by emaloli on 2010-05-31
Hi!

I've installed easy peasy 1.5 on an asus-eeepc. I'm quite new to linux
I've got two hard disk (4 and 8 gb), and my home was installed on the 4gb one, while the other was mounted as an external drive.

Since I had almost used all the space on the 4gb drive I decided to try and move the home folder to the 8gb drive, doing a symbolic link.

```
cp -r /home/loli /media/disk/loli
```

```
mv /home/loli /home/lolibackup
```

```
ln -s /media/disk/loli /home/loli
```

everything was working fine so I deleted the back up...
I tried to reboot and it can't find the /home/name directory.. looks like I screwed something and the disk is not being mounted when the computer starts!

i can get in with ctrl+alt+f1 with my usual 'loli' account, but I don't know what to do...

Anybody knows how to help me? thanks!

(yes the whole thing was stupid.. I know! but i like to learn from my own mistakes!)

---

### Post by lechien73 on 2010-05-31
You need to edit /etc/fstab so that the external disk is mounted on startup.

I would do the following:

[LIST]
[*]Log in at the terminal, plug in your external disk, mount it and make another backup of your "loli" directory.
[*]Then type:
```
unlink /home/loli
ls /dev/disk/by-uuid
```
[*]Note down the UUID of your external drive, then type:
```
sudo nano /etc/fstab
```
[*]And enter the line:
```
UUID=<enter UUID here>    /home    ext3    defaults    0    2
```
[*]Press CTRL+X to exit, and answer "Y" to Save.
[*]Now reboot your computer.[/LIST]

NOTE: I'm presuming you're using ext3 for the file system on your external drive. If you're not, then change the reference to "ext3" in my example above to whatever file system you have on the external drive.

EDIT: Also, you cannot use an NTFS or FAT partition as your /home partition.

Unless I've missed a step, that should do it.

---

### Post by emaloli on 2010-05-31
thanx a lot for the answer!
I've got 2 problems, though..

1) my second hard-disk is not actually external.. It's inside the pc.. it's just that I've used it like an optional drive. I cannot plug it in or plug it out, so I don't know how to mount it!

2) ```
ls /dev/disk/by-uuid
```

gives back 3 addresses like

7418c3ff-865e- ... .... .... ...

It doesn't say anything about what address belongs to what drive..

Is there maybe an option in the ls to understand that?

thanks!

ema

---

### Post by Morbius1 on 2010-05-31
```
sudo blkid -c /dev/null
```This will list your partitions by legacy ( i.e., sdxy.. ), UUID, LABEL, and Type ( ext3, ntfs, etc..)

---

### Post by Paul Crawford on 2010-05-31
Try the command:
sudo blkid

You should get something like this:
```

/dev/sda1: LABEL="windows" UUID="B6B4F484B4F4487F" TYPE="ntfs" 
/dev/sda5: LABEL="root-8.10" UUID="fc0ce86c-5e2f-49bb-8bf2-9445535234a8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="home" UUID="c526c1cd-b861-47fc-ac91-068f723ac376" TYPE="ext3" 
/dev/sda7: LABEL="root-10.04" UUID="10fe7c39-801d-412d-964d-a82f10cc03ee" TYPE="ext4" 
/dev/sdb1: LABEL="backup_hdd" UUID="9363cb3e-f974-4573-9af4-ebf1dffe8461" TYPE="ext3" 

```

In my case I have set lables on the partitions to make it easier. If not, use the 'mount' command with nothing else and you should get something like this:

```

/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6 on /home type ext3 (rw,relatime)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/backup_hdd type ext3 (rw,nosuid,nodev,uhelper=udisks)

```

From the two, you can link a mount point (such as '/' or '/home' etc) to a partition (such as '/dev/sda7') and hence to a UUID (such as "10fe7c39-801d-412d-964d-a82f10cc03ee").

Of course, your results **will** be different!

---

### Post by Paul Crawford on 2010-05-31
Yes, as Morbius1 said, better to use -c /dev/null so you don't get any cached results of previous partitions.

---

### Post by lechien73 on 2010-05-31
> **emaloli said:**
> ```
ls /dev/disk/by-uuid
```

gives back 3 addresses like

7418c3ff-865e- ... .... .... ...

It doesn't say anything about what address belongs to what drive..

Is there maybe an option in the ls to understand that?



Sorry - what I should have said was:

```
ls -l /dev/disk/by-uuid
```

The options mentioned by other posters will work just as well :)

---

### Post by emaloli on 2010-06-02
thanks you all, but I couldn't solve my problem (the outputs it gave were quite dissimilar to yours), so I just installed easypeasy back..

---

