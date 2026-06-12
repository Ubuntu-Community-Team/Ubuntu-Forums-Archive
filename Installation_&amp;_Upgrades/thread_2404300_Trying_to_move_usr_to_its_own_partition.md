---
title: "Trying to move /usr to its own partition"
date: 2018-10-22
forum: Installation &amp; Upgrades
---

### Post by mnealbarrett on 2018-10-22
I installed Ubuntu 18.10 on a Surface Pro with a 64GB SSD. It was working beautifully, so I decided to tweak it a bit. I have a 128GB high-speed SD card, and I would like to use the SD card to get Ubuntu's "footprint" on the SSD as small as possible. I moved /home to a partition on the SD card, and it worked fine. Just a tiny bit slow, but more than acceptable. So, I got the bright idea to move /usr to a separate partition on the SD card. I proceeded carefully, creating the partition, copying /usr to the partition with rsync, and adding the partition to fstab. To minimize the chances of something going wrong, I just mounted over the old /usr instead of renaming it. Something like this:  

UUID="????????"    /usr       ext4             defaults         0         2

(Yes, I did properly replace "????????" with the UUID for that partition from the blkid command)

I rebooted, and it worked fine. No problems at all. The slowdown was not as bad as I expected. Probably because /usr isn't written to very much. It is mostly read from, and the SD card has acceptable read speeds.

So, I boot from the live "CD" that I used to install Ubuntu (I had written it to a flash drive), mounted my root partition, and did "mv usr usr_old".

I rebooted, and Ubuntu crashed and burned while booting.

So I booted from my live "CD" again, mounted the root directory, and did "mv usr_old usr". Rebooted, and my system was working again.

Eventually, I would like to free up some space by deleting the contents of the old /usr directory and replacing it with an empty directory that I can use as a mount point for the /usr partition. But I can't do that, because the system will crash and burn while booting. 

So, I am theorizing that something in the boot process needs something in /usr before the /usr partition on the SD card can be properly mounted. Anyone have any ideas what that could be? It could be something from /usr/bin, I don't know.  I'd like to delete as much as possible from the old /usr directory, leaving just enough to get the system booted to the point where the partition can be mounted over it.

---

### Post by TheFu on 2018-10-23
If there isn't a /usr directory existing at mount time, then the SDHC card mount will fail.  A "mount point" is usually just an empty directory.

---

### Post by Impavidus on 2018-10-23
Have you considered```
mv usr usr_old
mkdir usr
```?
The /usr directory has to exist. Without an existing mountpoint, the usr partition can't be mounted.

---

### Post by mnealbarrett on 2018-10-28
> **Impavidus said:**
> Have you considered```
mv usr usr_old
mkdir usr
```?
The /usr directory has to exist. Without an existing mountpoint, the usr partition can't be mounted.

I wish people would READ MY MESSAGE.

If I do that, the system CRASHES AND BURNS during the boot process.

If I leave the old /usr directory, with its contents, in place and mount over it (you CAN mount over a directory that has stuff in it), the system works fine. If I make an empty /usr directory, the system crashes during boot.

I followed this:

[https://askubuntu.com/questions/656/how-to-move-usr-to-a-new-partition](https://askubuntu.com/questions/656/how-to-move-usr-to-a-new-partition)

My theory is that the system needs *something* in /usr until the /usr **partition** is mounted. Maybe /usr/bin, I don't know.

---

### Post by TheFu on 2018-10-29
I've moved /usr to different disks probably 5 times in my life.  Never had the issue you claim.  If this is still an issue and you'd like help, please post the output from 
```
lsblk
more /etc/fstab
ls -ld /usr
```
using *code tags*.  Real data, not ???????  since some detail is being lost in the translation to the posts here.

---

### Post by Impavidus on 2018-10-29
I did read your original post. You stated that you renamed the old /usr directory, not that you created a new, empty /usr directory. If the system crashes and burns, does it give an error message, or just a lot of noise, smoke and flames? An error message might be useful. Any errors listed in /var/log/*?

/usr is supposed to contain only stuff that isn't needed to boot into single user mode. Everything that's vital for booting should be somewhere else, in the /lib, /lib64 and/or /lib32, /bin, /sbin and /etc directories (and /root, which is not needed for booting, but may be needed for fixing a broken system so that other partitions can be mounted). Those directories must be present on the root partition, everything else may be moved. I know that on some Unix systems /bin, /sbin and /lib have been replaced with symlinks to directories in /usr. If that's the case, /usr can't be moved to a different partition, but this shouldn't be the case on Ubuntu. Maybe that's worth to check anyway.

I don't know Surface Pros. If they can boot from the sd card, you can put the entire system on the sd card. If they can't, it should still be possible to put the entire system except a small /boot partition on the sd card. But I fail to see why you'd want that. And of course, /var does see a lot of writes, so you want that on a device with good write performance.

---

