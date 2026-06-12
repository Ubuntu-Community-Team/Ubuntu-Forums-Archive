---
title: "Can't find 2nd hard drive."
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by Florida Roadkill on 2008-08-07
I recently installed Ubuntu and am trying to find my data. I understand drives are not assigned letters. My hard drive has one partition. The drive which has XP on it and my "core" programs was recognized. I am trying to find the other drive which contains all of my documents and media.

I have found "Home" and it is not there. So I have done some searches for finding your hard drives. I haven't found anything that applies well or that I understand.

I ran some codes but I don't understand what I am doing to a) feel entirely comfortably typing in something that could ruin everything 2) understand the results.

Thank you to all in advance and even if you can't help the problem maybe you can tell me how to not sound like a such a noob.

---

### Post by iaculallad on 2008-08-07
Try posting whatever displays when you issue the following command in your terminal so we could locate of what drives needs to be mounted in order for you to access your files:
```

sudo fdisk -l
```

and

```
sudo blkid
```

---

### Post by Florida Roadkill on 2008-08-09
Sorry I didn't respond sooner. Thank you for your help.

Here are my results from the first command, sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe150e150

And here is what came up after the second command, sudo blkid

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19457   135805477+   7  HPFS/NTFS


/dev/sda1: UUID="3C2C9BA62C9B5A2A" TYPE="ntfs" 
/dev/sda2: UUID="6A34398034395075" TYPE="ntfs" 
/dev/loop0: UUID="d45d36e8-411b-4df3-913b-3b3cda2a2f41" TYPE="ext3" 

While I don't know what everything means, do the results form the second command mean that because it sees 2 starts and 2 ends, it knows there is a partition?

---

### Post by |Eric| on 2008-08-09
you are running from CD ? 

also post a "lshw -C disk"

---

### Post by Florida Roadkill on 2008-08-11
I installed from the Live CD. I ran your command and this is what I came up with:

  *-disk                  
       description: ATA Disk
       product: ST3160815A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 9RA1F5YL
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=e150e150
  *-cdrom:0
       description: DVD reader
       product: DVD-ROM DDU1612
       vendor: SONY
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: DYS3
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD writer
       product: DVDRW SOHW-812S
       vendor: LITE-ON
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: US0F
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open

Hopefully, we are getting somewhere. I have some done some more searches and I can't find anything thats in basic enough language to understand the consequences of what I am doing or to interpret the output. I am so new to Ubuntu I still have the afterbirth on me. Thanks again.

---

### Post by Florida Roadkill on 2008-08-15
I am still struggling with this issue as all the files I use on a daily basis cannot be found in Ubuntu, so <gasp> I continue to use Windows. 

In all other respects I have been impressed with this OS so much. It's free, support is everywhere, and I think the elitist status for programmer people only has been removed and it has become much more accessible and friendly to the average user. Well Done!!

---

### Post by iaculallad on 2008-08-15
You're problem seems like you cannot access your NTFS drives in Ubuntu? To solve that problem, we will have to edit your fstab file and configure those drives to automount at startup. From there, you could start searching for your files.

-Enter your terminal and issue the following commands below-

Create your mount points:

```
sudo mkdir /media/NTFSDrive_1
sudo mkdir /media/NTFSDrive_2

```

Next, open and edit the contents of the fstab file:

```
gksudo gedit /etc/fstab
```

When opened, append the line of texts below on the last part of the file.

```
UUID=3C2C9BA62C9B5A2A /media/NTFSDrive_1     ntfs    defaults,umask=007,gid=46 0
UUID=6A34398034395075 /media/NTFSDrive_2     ntfs    defaults,umask=007,gid=46 0

```

And lastly, Save and Close the file. On your terminal again:

```
sudo mount -a
```

Then try searching for your files from the mounted NTFS drives.

---

### Post by Florida Roadkill on 2008-08-16
Wow, thank you so much! I am going to go ahead and try that now and I will get back to everyone with the results.

---

### Post by |Eric| on 2008-08-16
do a "df" it will show mounted partitions(HD as you call them)


i would agree with the fellow above your second partition is most likely not mounted

the / entry of df comand is where your linux is at 
for example:

~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             38345904  15654868  20743160  44% /
varrun                 1031556        96   1031460   1% /var/run
varlock                1031556         0   1031556   0% /var/lock
udev                   1031556        96   1031460   1% /dev
devshm                 1031556         0   1031556   0% /dev/shm


here you can see that my / (linux) is mounted from the partition /dev/sda1
you will also see your second partition if its mounted.

---

### Post by Florida Roadkill on 2008-08-16
OK, So I went ahead and successfully entered all the codes from iaculallad post. When I went back into Places > Desktop I was still presented with the same information on the left-hand side. Only one hard drive. So, maybe I am having a brain fart, but is there somewhere else to look for mounted drives? I'm thinking there has to be, but I am too dense to find it.

And in response to Eric's post, I found the following output with the df command:

Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      13563852   2664564  10215696  21% /
varrun                  517684       104    517580   1% /var/run
varlock                 517684         0    517684   0% /var/lock
udev                    517684        44    517640   1% /dev
devshm                  517684        48    517636   1% /dev/shm
lrm                     517684     39760    477924   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      13563852   2664564  10215696  21% /home/blue/.gvfs
/dev/sda1             20482840   7728772  12754068  38% /media/disk
/dev/sda1             20482840   7728772  12754068  38% /media/NTFSDrive_1
/dev/sda2            135805476  31575728 104229748  24% /media/NTFSDrive_2


So, I'm not quite sure where this leaves me, but I am going to look into more. Now that I am starting to use and I think understand some commands, I might get somewhere with this. Thanks again!

---

### Post by |Eric| on 2008-08-17
ok so your drives are mouted correcly (yes!)

you will find your stuff in the "file system" drive in the media -> NTFS_DRIVE2 

you dont have the location on your desktop that is ok its just a shortcut

---

### Post by Florida Roadkill on 2008-08-17
Problem Solved! I found everything I have been looking for. 

Now, that I got it, what's the best way to make a shortcut that will appear on my desktop or at least, (but hopefully both) appear on the left-hand side of my file browser under Places?

Thank you so much.

---

### Post by Florida Roadkill on 2008-08-17
Got a link just below my places now, so that will save me a few steps. Still a little confused about making a "short-cut" or launcher on the desktop, but there are other threads to learn about that.

---

