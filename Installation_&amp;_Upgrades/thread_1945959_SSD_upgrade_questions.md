---
title: "SSD upgrade questions"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by Balthazar_Droid on 2012-03-23
I recently posted this question on AskUbuntu, but I thought I would post it here too, I figure the more input the better :)

I have recently purchased a 120GB SSD to install in my desktop. I currently have two 2TB HDDs connected via SATA and an older 500GB HDD connected via PATA. My plan is to wait until 12.04 is released and do a fresh install on the SSD. At that point I have a couple of questions as far as the best practices to set up my existing drives.

1) One of the 2TB HDDs is partitioned with 40GB for / and the remainder as /home. My plan was to partition the SSD with 40GB for / and the remainder for /home. Then I would like to erase the / partition on the HDD (and probably the MBR right?) and recoup that space for storage. I would also like to erase everything except my Video and Music folders on the drive and basically use it only for media storage. Is this possible without losing the data already on the hard drive?

2) Is it possible to have my /home/Music and /home/Videos folders mounted on the HDD rather than the SSD? I would prefer to use the SSD only for the OS and programs, not for media.

---

### Post by darkod on 2012-03-24
In that case why don't you simply continue using /home from the hdd?

For example, set up 40GB / on the ssd as you plan, reuse the same /home from the hdd and the rest of the ssd set up as ext4 partition with mount point /data, /data1 or what ever.

Concerning the existing / on the hdd, yes, after you have your new ssd install you can delete that partition on the hdd and expand one of the other partition to use that space. Or simply create a new 40GB partition from that space that you can use how ever you want.

---

### Post by oldfred on 2012-03-24
As Darko suggests you can split your /home so most data is stored on the rotating drive and only the parts of /home you need to boot are on the SSD. That is how I have installed to my SSD. It is 60GB and I installed two / (root) 30GB partitions, so I can alternate installs. I also leave an install on my rotating drives just so they are bootable. I want all necessary files/partitions required for booting on a drive so it can boot without any other drive for reliability. Data then can be anywhere.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

Why I leave an Ubuntu on every hard drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

