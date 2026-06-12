---
title: "Trying to set up multiple partitions"
date: 2018-03-17
forum: Installation &amp; Upgrades
---

### Post by spokeydokey on 2018-03-17
Hello

I have two drives, a 120GB SSD (sdb) and a 1TB HHD (sda).  I boot from a 50GB partition on the SSD.  I have the HHD divided into two partitions, one of which is mounted to /home (for all my pictures, video, music, etc).  I would like to mount the free space on the SSD to /home (for more storage), and mount the other portion of the HHD somewhere where I can encrypt it.  I think I would prefer to mount it to a directory in /home (not /mnt or /media).  Right now, I have things set up like this:

/dev/sda1   ext4   /home
/dev/sda2   ext4   /home/john/other
/dev/sdb2   ext4   /
/dev/sdb1   extended
/dev/sdb5   linux-swap
/dev/sdb3 ext4  (not mounted)


I would like Other to be permanently mounted like my /home folder.  When I look at my file system using Caja, "Other" is listed under Devices with other removable media.  Maybe this isn't a problem but it seems like it should be integrated into the file system under Computer.  Is there a way to do this? And where should I mount sdb3 to include it in my home directory?

Thank you!!!

---

### Post by Dennis N on 2018-03-17
Seems like you could just add an entry into your /etc/fstab to have that file system on sda2 mounted at startup.

Something like
```
UUID=d97e2feb-1bf6-429b-bba5-943264ec1474 /home/john/other ext4 defaults 0 2

```
but, or course, change the UUID to the correct one. **lsblk -o name,uuid** will tell you what the UUID should be.

---

### Post by spokeydokey on 2018-03-17
Thanks for the help Dennis.  I added entries for those two partitions in fstab and they mount automatically on startup.  But they are still listed under Devices with an eject button next to them (using File Manager or Caja).  Ideally, they would be listed under Computer just like Documents, Downloads, Music, etc. with no button to unmount them.

---

### Post by oldfred on 2018-03-20
I copy folders normally in /home (and a few others) into another partition.
Then mount partition at /mnt/data. That mount does not show in /home.
But then I link all the folders in /mnt/data into /home.

I do this primarily as I have more than one install and want same data in each install. But do not necessarily want settings from /home. So no shared /home.
Since so little data is left in /home I leave it in / (root). I even move some large hidden folders with data like Filefox & Thunderbird profiles.

        [https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting](https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting) 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by spokeydokey on 2018-03-20
Thanks oldfred.  I read though all those links.  I think I'll try playing around with the -bind option.  That might get me to what I'm looking for but I'm not really sure.

Right now using File Manager, the extra partitions I have set up on the HHD (/home/john/OtherDocs) and the SSD (/home/john/Data) are listed under Devices.  They work fine that way, but I was hoping to:

1. Access the HHD partition as its own directory under Computer right next to Documents, Downloads, Music, Pictures, etc. 

2. Integrate the SSD partition into /home to increase the storage there with the extra GB I have on the SSD.  I don't really want a directory called Data.  When I save a photo or document, I don't really care if it ends up on the HHD or the SSD.

---

### Post by oldfred on 2018-03-20
Using links, I do not have a normally visible Data directory. Occassionly I use it, and have to drill down from computer to /mnt to /mnt/data.
But links provide direct access to all the folders in my data partition as folders in /home. I cannot tell difference with use.
I used to have two data partitions, one NTFS for sharing with my XP install. But that is now long gone.

Note all the folders are links:

---

### Post by Dennis N on 2018-03-20
>  I added entries for those two partitions in fstab and they mount automatically on startup. But they are still listed under Devices with an eject button next to them (using File Manager or Caja)

Well, that's interesting. It's been my understanding that any file system mounted in /etc/fstab would not show in the file manager side pane.

As one test here, using Caja, I restored a previous bind mount of my data partition to a subfolder of my home folder and that bind mounted folder does show in the side pane. That seems to confirm your observation. I think I must have known this, but since I haven't used the bind mount access to my data for some time (I went back to using bookmarks), just forgot that this happens.

If you don't want the mounted folder to show there, use bookmarks or symbolic links to access your other partition. I generally bookmark the folders I frequently use on my data partition (it is actually mounted as a subfolder of /mnt, so the data partition does not show in the side pane).

---

