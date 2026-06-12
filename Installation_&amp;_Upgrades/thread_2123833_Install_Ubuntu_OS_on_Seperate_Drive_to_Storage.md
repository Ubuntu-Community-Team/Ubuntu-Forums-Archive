---
title: "Install Ubuntu OS on Seperate Drive to Storage?"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by TheTechnoTux on 2013-03-09
Hi,
I was thinking about installing Ubuntu onto a small SSD, giving me quicker boot up times, but store all my data (my documents etc.) on a larger HDD. My question: How would I go about this? How could I move the /home folder onto my other disk, if even possible?

Thanks, I will be very grateful for your responses!

---

### Post by sudodus on 2013-03-09
Welcome to the Ubuntu Forums :-)

Do you have a system, that you want to move (without changing anything else)?

Do you have the hardware where you want to run it?

0. It is important to ***backup*** your system before such an operation (backup to a separate external drive)

A - automatically

I think it will be easiest to simply copy the current /home (preserving the permissions and ownership) to a new partition (on the HDD to be used for it), and then install a fresh Ubuntu system with the root partition on the SSD and the home partition on this new partition.

Prepare the partitions before installing the new system. Then during installation at the partitioning page, select 'Something else' and select the proper partitions of root and home and the proper drive for grub (the drive for example /dev/sda, not a partition /dev/sda1)
--
B - manually

1. Perform the changes when booted from another drive, for example an Ubuntu install drive.

2. the root partition /

Let us assume the source is mounted on /mnt. Create a partition on the SSD and use
```
sudo rsync -Hav --exclude=/mnt/home ...
```
to copy the content of your present root partition except /home

3. /home

If to a new drive: Create the partition to become your new /home and use 
```
sudo rsync -Hav ...
```
to copy the content of your present /home to it.

If on the same drive: Let us assume it is mounted on /mnt. Keep it until you have copied the root file system to the SSD drive, then remove 'everything else' from /mnt
and finally move /mnt/home to /mnt.

3. You need to edit the file **[FONT=courier new]/etc/fstab[/FONT]** to reflect the changes of the UUID of the root partition and add a new line to mount the /home partition, and maybe also a new swap partition. I recommend also that you add the following options to the root partition (because of the SSD hardware) **[FONT=courier new]discard,noatime[/FONT]** in the fourth field (it often starts with defaults)

---

### Post by oldfred on 2013-03-09
+1 on sudodus suggestions.

I do it differently but it is a bit more advanced as you split /home. My requirement is every drive must be bootable without any other drive. So entire system including /home must be on same drive. But data can be anywhere and linked into /home and it data drive fails, it should still be able to boot with mounting errors. And my data drive has another install, either an old one or testing or something bootable, in case my main drive fails.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by fantab on 2013-03-09
> **oldfred said:**
> I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

I haven't had any issues sharing /data partition between Ubuntu, Arch and Fedora. With Fedora I had a problem when they did not use UID=1000 as default, but since it has become their default I have had no issues whatsoever. And I don't use Separate /home anyway. 

Like it has been pointed out by oldfred, user data leaves a small foot print on the HDD. Just a / partition of about 10-15 GB on SSD should do for Ubuntu.

My two cents...

---

