---
title: "Cannot find second hard drive on server 12.04"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by Proberts042 on 2012-07-19
I am new user of Ubuntu and have just installed server 12.04 for use in the school that I am running in Honduras. I have a second hard drive installed for use by the school and teachers. I want to use this second hard drive for file storage. When I type in lshw I can see the drive; logical name: /dev/sdb. The hard drive is formated to NTFS. How do I mount this hard drive and then create and identify directories on this hard drive for individual and group use?

I have looked far and wide and cannot seem to find this information anywhere. Thank You

---

### Post by rukiaEnix on 2012-07-19
Please post the result of this command:

```

sudo fdisk -l

```

---

### Post by darkod on 2012-07-19
Note that a disk formatted ntfs will not give you full linux permission control on the directories, etc. You can use it, write to it and read data, but having a linux filesystem gives more options.

If there is no data on it, it would be better to reformat it as ext4, either as a single partition on the whole disk, or split in several partitions, depending how you want to use it.

In any case, to have it mount permanently on boot, you will have to create an entry in /etc/fstab which will mount it at a specific mount point.

If that mount point doesn't exist, you will have to create it first. Something like:
sudo mkdir /media/hdd2

Then you can mount it at /media/hdd2.

---

### Post by Proberts042 on 2012-07-19
My users are going to be storing and accessing a lot of windows files on the hard drive. As far as I know this is the only machine in use here with Linux. Will ext4 be the correct format for this drive?

---

### Post by Proberts042 on 2012-07-19
I am using the server edition. Not sure how to copy and paste this information. I can get to it, however. Posting to you using my Windoze machine.

---

### Post by darkod on 2012-07-19
If this will be a server, users will probably be accessing something like Samba shares. In that case, the users don't really see what is the filesystem and it makes no difference, they only see the share.
From aspect of Samba permissions etc, it's better to be ext4, a linux filesystem.

As for accessing the server, how did you plan to do it?
You need to either connect a monitor and keyboard to it, or do it through SSH, if you installed the role SSH Server during installation. From windows you can access ssh using Putty, google for it. It's free and you can use it to connect to ssh.

If you didn't install the SSH Server during installation, you will need to connect a monitor and keyboard, log in and install it with:
```
sudo apt-get install openssh-server
```

After that you can access it from anywhere on the LAN with Putty and the IP of the server. You did set up manual (static) IP instead of dynamic right? Don't leave servers with dynamic IP since usually they would need a static IP that doesn't change.

---

### Post by Proberts042 on 2012-07-20
I did install SSH and plan for my users to access the files through it. I did set up a static IP address on the server. Can I not just have users access the files on the second hard drive though Samba server?

---

### Post by rukiaEnix on 2012-07-20
Do you have samba installed? If yes, please post your configuration for samba.

---

### Post by darkod on 2012-07-20
> **Proberts042 said:**
> I did install SSH and plan for my users to access the files through it. I did set up a static IP address on the server. Can I not just have users access the files on the second hard drive though Samba server?

Yes, file sharing is usually done with Samba shares. But in any case you will need all hdds/partitions to be mounted somewhere. Linux works with mount points in format /path/folder.

So, you can't tell Samba to share /dev/sdb1, but instead you can mount /dev/sdb1 as /data1 for example, and tell samba to share /data1.

Good that you installed SSH but you would use that usually for administering. I don't see why you are planning the users to use SSH, they would simply get the ubuntu server CLI. Is that what you want them to do?

For opening the samba shares, they don't need to use ssh.

---

### Post by Proberts042 on 2012-07-20
I do have samba installed, but do not know how to capture the configuration and post it here. I am using the command line server version of Ubuntu. Can you help me to somehow capture the information in the file?

---

### Post by rukiaEnix on 2012-07-20
You have SSH installed, so you can access the server from other computer with putty and just copy paste the contents.

---

### Post by Proberts042 on 2012-07-20
I still can't seem to be able to mount this hard drive identified as Disk /dev/sdb and /dev/sdb1.

---

### Post by darkod on 2012-07-20
That's why I asked about ssh. Instead of running the command on the server itself, and then you can't "move" it to your dekstop to post it, simply install Putty (if your desktop is windows machine).

In fact, you don't install Putty, you just copy it and it can be used.

Open Putty and select to connect to the IP of the server.

It will ask for the username and password, enter them.

Then you can work on the server but from your desktop which allows you to easily make screenshots and post them here.

The samba cinfig file is /etc/samba/smb.conf so you can view the content for example with:
cat /etc/samba/smb.conf

---

### Post by darkod on 2012-07-20
> **Proberts042 said:**
> I still can't seem to be able to mount this hard drive identified as Disk /dev/sdb and /dev/sdb1.

How did you try it?

---

### Post by darkod on 2012-07-20
If you want help with the exact commands, I think we better start step by step. Connect with Putty to your server and post the output of these commands:
```
sudo parted -l
df -h
```

After that we can continue.

---

### Post by Proberts042 on 2012-07-20
I figured out how to do this.

sudo fdisk -l


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cfee5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   488396799   243947521    5  Extended
/dev/sda5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008ccb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  1953525167   976762552+   7  HPFS/NTFS/exFAT

Disk /dev/mapper/sandy--server-root: 241.5 GB, 241499635712 bytes
255 heads, 63 sectors/track, 29360 cylinders, total 471678976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sandy--server-root doesn't contain a valid partition table

Disk /dev/mapper/sandy--server-swap_1: 8296 MB, 8296333312 bytes
255 heads, 63 sectors/track, 1008 cylinders, total 16203776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

---

### Post by Proberts042 on 2012-07-20
paul@sandy-server:~$ sudo parted -l
Model: ATA WDC WD2500AAJS-0 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   250GB  250GB  extended
 5      257MB   250GB  250GB  logical                lvm


Model: ATA ST1000DM005 HD10 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ntfs         boot


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/sandy--server-swap_1: 8296MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  8296MB  8296MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/sandy--server-root: 241GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  241GB  241GB  ext4




paul@sandy-server:~$ df -h
Filesystem                      Size  Used Avail Use% Mounted on
/dev/mapper/sandy--server-root  225G  5.3G  209G   3% /
udev                            3.8G  4.0K  3.8G   1% /dev
tmpfs                           1.6G  740K  1.6G   1% /run
none                            5.0M     0  5.0M   0% /run/lock
none                            3.8G     0  3.8G   0% /run/shm
cgroup                          3.8G     0  3.8G   0% /sys/fs/cgroup
/dev/sda1                       228M   27M  189M  13% /boot
paul@sandy-server:~$

---

### Post by darkod on 2012-07-20
OK. I assume the 1TB disk is still empty, right?

In that case, if there is no important data on it, you can reformat it as ext4 so you can use it.
```
sudo mkfs.ext4 /dev/sdb1
```

That will format the sdb1 partition as ext4.
After that, lets make a mount point (folder) for it:
```
sudo mkdir /media/hdd2
```

Then, open /etc/fstab and make an entry to mount sdb1 at that mount point, but using the UUDI instead of sdb1. You can list the UUIDs of all partitions with:
```
sudo blkid
```

Note down the UUID string for sdb1. Then open fstab with nano editor:
```
sudo nano /etc/fstab
```

At the end of fstab add an entry like:
```
UUID=<put the UUID string here>   /media/hdd2   ext4   defaults   0   0
```

Save the changes in nano with Ctrl+O, Enter, then exit nano with Ctrl+X.

After that, check if it will mount OK with:
```
sudo mount -a
```

If there are no errors reported, it should be fine. Check again the mounted partitions with:
```
df -h
```

If all went well, now you should see a changed output from the previous time you ran it. Now you should also see something like:
/dev/sdb1   size   used   percentage   /media/hdd2

That means it's mounted at /media/hdd2 and since you made an entry in fstab it will mount there at every boot.

That part of the job is finished.

Now, about the samba shares. Do you want to have a single share for all users, and all of them can write and read, or you want some sort of controls, and that some users can only view some folders and not others, etc?

---

### Post by Proberts042 on 2012-07-21
Was able to mount hdb1 as shown:

paul@sandy-server:~$ df -h
Filesystem                      Size  Used Avail Use% Mounted on
/dev/mapper/sandy--server-root  225G  5.6G  208G   3% /
udev                            3.8G   12K  3.8G   1% /dev
tmpfs                           1.6G  560K  1.6G   1% /run
none                            5.0M     0  5.0M   0% /run/lock
none                            3.8G     0  3.8G   0% /run/shm
cgroup                          3.8G     0  3.8G   0% /sys/fs/cgroup
/dev/sda1                       228M   50M  167M  23% /boot
/dev/sdb1                       931G   14G  871G   2% /media/hdd2

Thank you

I would like to set up a common share and additional shares for each user so that they have restricted access to stored documents.

---

### Post by darkod on 2012-07-21
Unfortunately I don't know samba in details when we are talking about limiting access. You might be better opening a new thread in the Server section, titled Setting up samba shares or similar.

But you still need to do one thing before that. For every samba share that you want with different permissions or share name, you will need to create a separate folder in /media/hdd2. This is because samba shares are defined on the folder level, so if you want more than one share, you need more than one folder.

Something like:
sudo mkdir /media/hdd2/share1
sudo mkdir /media/hdd2/share2
etc

You also might need to set some permissions on these folders, but you can ask that too in the samba thread. I only set open for all permissions, which doesn't seem to be what you want.

I suggest a new samba thread because most people that know samba wouldn't look too much in this thread titled about the hdd. You are getting there step by step. There are also many good tutorials on samba on google, that can help you too. They cover all possibilities you might want.

---

### Post by Proberts042 on 2012-07-23
OK I have done this. Thanks again for all your help.

---

