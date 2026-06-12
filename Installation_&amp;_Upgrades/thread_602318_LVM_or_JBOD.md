---
title: "LVM or JBOD?"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by oxygen on 2007-11-04
Hi all,

My current ubuntu server has a single HDD - with a directory:

/data

This is shared using samba. Now I'm running out of space on the drive so I want to add some more to the machine. However I **don't** want to mount them as an additional folder for each drive inside data.

Basically if someone copies a file in to /data (or it's subfolders) and there's no room on the first disk - then it puts it on the second disk, or if no space on that drive then the third, etc.

I understand that if I use JBOD - and one of the disks die - then I lose everything on all the drives... does LVM suffer the same problem?

This is how the system is setup at the moment (obtained by running *df*):

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            238134500 138325720  87712240  62% /
varrun                  387824       232    387592   1% /var/run
varlock                 387824         0    387824   0% /var/lock
procbususb              387824        64    387760   1% /proc/bus/usb
udev                    387824        64    387760   1% /dev
devshm                  387824         0    387824   0% /dev/shm
```

Can I plug in my extra drives (3 x IDE) and then just changed some settings - or will I need to do a re-install to get it working properly?

Thanks in advance!

---

### Post by dcstar on 2007-11-04
> **oxygen said:**
> Hi all,

My current ubuntu server has a single HDD - with a directory:

/data

This is shared using samba. Now I'm running out of space on the drive so I want to add some more to the machine. However I **don't** want to mount them as an additional folder for each drive inside data.

Basically if someone copies a file in to /data (or it's subfolders) and there's no room on the first disk - then it puts it on the second disk, or if no space on that drive then the third, etc.

I understand that if I use JBOD - and one of the disks die - then I lose everything on all the drives... does LVM suffer the same problem?

This is how the system is setup at the moment (obtained by running *df*):

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            238134500 138325720  87712240  62% /
varrun                  387824       232    387592   1% /var/run
varlock                 387824         0    387824   0% /var/lock
procbususb              387824        64    387760   1% /proc/bus/usb
udev                    387824        64    387760   1% /dev
devshm                  387824         0    387824   0% /dev/shm
```

Can I plug in my extra drives (3 x IDE) and then just changed some settings - or will I need to do a re-install to get it working properly?

Thanks in advance!

If you set up the three extra drives as a single RAID-5 array, then you will have total space equal to two of the drives and you will be totally protected if one of the three drives fail.

You should be able to then copy all data off the existing /data partition, mount the RAID array as /data, and copy it all back.

---

### Post by oxygen on 2007-11-04
Thanks David!

However in doing that - do I lose ~250GB of storage on the existing drive?

I want to the server to be like this:

[http://img257.imageshack.us/my.php?image=hddbf0.jpg]("http://img257.imageshack.us/my.php?image=hddbf0.jpg")

---

