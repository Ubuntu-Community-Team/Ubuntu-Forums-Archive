---
title: "Server 7.04 SW-RAID help"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by Gooorn on 2007-05-25
This is my first post here and I would like to give my best to this community.

I migrated from Windows Server to Ubuntu 7.04 Server-i386. I have SataRAID (fakeRAID, ULi chipset 1573) with two disks configured as RAID1 (mirror only) with NTFS file system and these are not system disks but data only disks. Ubuntu Server, needless to say, sees them as two drives with same content. 

Is there a _non-destructive_ way to build SW RAID1 with this two drives?

Thanx in advance.

---

### Post by ikonia on 2007-05-25
The quick and simple answer is - your out of luck on this


The long and tedious answer is yes.

First - fake raid, forget about it under linux, I won't start the debate, so just pretend that technology doesn't exist.

Now what you need to do is in ubuntu mount both the NTFS partitions and check that the data is exactly the same.

Assuming it is lets continue.

First we destory one of the disks in the mirror. For the purpose of this example we'll assume your two sata disks are sda and sdb.

We are going to destory /dev/sdb

```

sudo fdisk /dev/sdb

```

hitting "d" and then the partition number will delete the partition. Then pres "w" to write the changes to disk.

Now your disk is dead.

Now recreate the partition, again 
```

sudo fdisk /dev/sdb

```

press "n" for a new partition, select your partition number and size and create say /dev/sdb1
. Now change the partition type to software raid. Press "t" for toggle parition type and set it to type "fd" which is sofrware raid. Pressing "p" will print the partition table to show this is correct. You should see something like this.

> 
/dev/sdb1   *           1          32      257008+  fd  Linux raid autodetect


Now press "w" to write the changes to disk.


Now we need to create a 2 disk mirror (yes I know there is only one disk). To get around this we create a degraded raid array which means disk array with one failed.

to do this as you currently have no raid meta devices, you'll need to create one in the /dev files system for the purpose of building the array. 

```

sudo mknod /dev/md0 c 9 0 

```

Now we'll create the array
```

sudo mdadm --create /dev/md0 --level=1 missing /dev/sdb1

```

this will create and start the meta device /dev/md0 based on /dev/sdb1 and the missing /dev/sda1 which still has your ntfs partition.

Now put a file system on it.

```

sudo mke2fs -j /dev/md0

```

Now our meta device has an ext3 file system on it.

Now lets mount it.

```

sudo mkdir /mnt/meta
sudo mount /dev/md0 /mnt/meta

```

Now we mount your ntfs partition

```

sudo mkdir /mnt/ntfs
sudo mount /dev/sda1 /mnt/ntfs

```

Now copy all the data off the ntfs disk onto the meta device.

```

cp -Rp /mnt/ntfs /mnt/meta

```

once this is done unmount both your disks and clean up

```

sudo umount /mnt/ntfs
sudo umount /mnt/meta
sudo rm -rf /mnt/ntfs
sudo rm -rf /mnt/meta

```

Now we need to destroy the old ntfs disk as your data is safe on the meta disk.

Follow the fdisk steps you did at the start creating the partition, but this time do it on /dev/sda.

Once this is done you need to add the new /dev/sda1 raid disk to the meta device.

```

sudo mdadm --manage /dev/md0 --add /dev/sda1

```

you should now see your disk join the array and start syncing data.
you can verify and watch the progress with

```

cat /proc/mdstat

```


once that data has synced you will have a fully functional software raid partition that you can mount as a normal disk and enjoy fault tolleraence.

hope this helps.

---

### Post by Gooorn on 2007-05-28
Dear ikonia, and let me say friend.

I was never hoping to see such elaborate and fast answer and I cannot thank you enough. I can just hope that I will be able one day to serve this community in such manner.

BR.

---

### Post by twinax on 2007-05-28
Hello
I am hoping you can help with raid 1 followup.  I have installed 6.06 to desktop with 40GB drives( hda). After installation I shutdown computer and connected 2 (750 GB sata ) drives.They show up as sda1/sda2 and sdb1/sdb2  The plan is to have the two sata's where I keep only data.  I didn't want anything to be carried forward on the drives so I did:
sudo fdisk  /dev/sda
d
partiton 1
 
sudo fdisk /dev/sda
partiton 2

then "w" for write changes

then
sudo fdisk /dev/sdb1
d 
partiton 1

sudo fdisk  /dev/sdb2
d
partion 2

I have restarted 
I have run sudo fdisk -l now and see:

Disk /dev/sda = 750 GB

and

disk /dev/sdb = 750 GB

Now I want one partition on the 750 hdd in raid 5.
Thanks for your help

---

### Post by ikonia on 2007-05-31
you need 3 disks for raid 5 - I belive your looking for raid 0 which I would not advise on your root file systems.

---

### Post by twinax on 2007-05-31
Oops , my msitake. That was a type.  I am setup using raid 1 not raid 5.  I have 3 drives. One for OS and the two sata drives in mirror.  Here is question:
I believe I have to mount the drive , what do I use for command?  (no
> directories created yet)
> I would like to create a main directory there called  data. from this I
> will break down departments. What is the command for this?
Thanks

---

### Post by ikonia on 2007-06-01
I think you need to sit down and thing about what your saying

1.) your using raid 0 - but you've got one drive for the OS and 2 drives mirrored - this is not raid 0
2.) you need to mount the drives - but you've given us no information on the drives or devices you want to mount

---

### Post by twinax on 2007-06-05
Hello Ikonia,

Well , my motive is to have available as much as the 750 GB drive as possible.  So I am protecting the data with Raid 1 , I have successffuly done this. I insalled the OS to the 40 GB drive and raid 1, the two 750 gb drives.  I have several 40 and 60 GB drives that I am going to install 6.06 on and if something happens to the OS , I can just slip in the other OS drive, mount the md0 and ready to go.I have the data physically seperated from the OS too.  Plus I am hoping I can easily move over the raid  drives to another computer if need be.  Right now this is only a desktop, with three drives,  I would like eventually get a server with hardware raid 5.
  But, after reading your post, I am worried about this line of thought. Is it going to be easy to just install another drive with the OS loaded and see the other drives?  Perhaps I should be only using the two 750GB drives and raid 1 them?  On the other servers both windows and AS400 , I am running raid 5. That would be my best practice, but I don't have the ok to get a new server for Linux. 
Appreciate your thoughts
Regards
RS

---

### Post by ksd on 2007-06-05
> **ikonia said:**
> 
once that data has synced you will have a fully functional software raid partition that you can mount as a normal disk and enjoy fault tolleraence.
Hello!
Does this explanation work for to make software RAID-1 for the bootable disk? I mean I have the same problem as the author -- ubuntu trusts my hardware RAID as 2 separate disk. But they are the only disk in my system and must be bootable then.

---

