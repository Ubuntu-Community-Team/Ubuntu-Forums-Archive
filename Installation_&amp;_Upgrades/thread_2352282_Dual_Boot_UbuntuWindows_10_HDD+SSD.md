---
title: "Dual Boot Ubuntu/Windows 10 HDD+SSD"
date: 2017-02-11
forum: Installation &amp; Upgrades
---

### Post by gari2 on 2017-02-11
Hello,

I recently bought a new laptop and I want to install Ubuntu 14.04 on it since Windows 10 is preinstalled. The problem is that I read a lot of threads but each one says a different thing. So, I would like some help cause I never installed two OS in different disks. 
[LIST]
[*]SSD: 128GB
[*]HDD: 1TB
[/LIST]

Thank you all!

---

### Post by oldfred on 2017-02-11
If a new laptop, 16.04.2 (out in a couple days, was supposed to be out already) or 16.10 may be a lot better choices.
If new system, you have new hardware, but newest hardware only had drivers in newest kernel, drivers, support software which then is in newest Ubuntu. Some hardware may be so new as not yet easily supported in Linux as vendors do very little to help. Dell & Intel are better than most.

---

### Post by gari2 on 2017-02-11
OK, thanks for that but what I actually want to know is how to partition both disks and what to do (I read something about symbolic links)


Thanks!

---

### Post by yancek on 2017-02-11
It also depends upon whether you are using an EFI machine.  A pre-installed windows 10 system is probably EFI so you would need to install Ubuntu EFI.  Info on that at the Ubuntu documentation link below.  If you don't have UEFI, post back as the method for installing will somewhat different.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-02-11
Are you planning on booting both systems from SSD & using HDD as data only or have Ubuntu on HDD?

Use only gpt partitioning if Windows 10 pre-installed and UEFI.

If Windows 10 make sure fast start up or always on hibernation is off.

I like to use a separate /mnt/data partition. And back when I still had XP, I had a shared NTFS data partition also. But Windows 10 will keep all the NTFS partitions mounted/hibernated if fast start up is on.

       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) 

I use a /mnt/data partition and have all the standard data folders in /home in my data partition and link those folders into /home. Then folders look like normally /home, but data actually is in data partition on other drive. And since I normally have at least one Ubuntu install on every drive, I can link data into every install and have access to same data no matter what system I boot.

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437) 

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

