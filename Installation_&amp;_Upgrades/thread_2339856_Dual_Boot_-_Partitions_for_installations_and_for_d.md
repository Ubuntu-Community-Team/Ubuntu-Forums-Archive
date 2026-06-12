---
title: "Dual Boot - Partitions for installations and for data separately"
date: 2016-10-13
forum: Installation &amp; Upgrades
---

### Post by tonma on 2016-10-13
i am using Windows 10 and Ubuntu in dual boot, does it make sense to make small partitions for Windows installation and Ubuntu, including enough for updates, (with all the necessary system reserved partitions), and then share the rest with the data / program files / home folders so that they will dynamically change from the physical beginning of the hard drive?
(Example: 50GB for Windows, 50GB for Ubuntu, 900GB for rest together)

The reason is I've had a problem since I installed Ubuntu alongside Windows(I have created a separate topic on that issue), which makes the hard drive much noisier when using Ubuntu
I tried some solutions, and non worked. But someone suggested that it might be caused due to the Ubuntu partition is physically located deeper in the hard drive, making the needle move more
It does make sense, because I am using 1TB hdd, and first thing that was installed is Windows on a 700GB partition, so Ubuntu is the last 300GB
I am not an engineer, but maybe the way I partitioned the hdd, means that Ubuntu is really located physically deeper making the needle move more?

---

### Post by oldfred on 2016-10-13
My one Windows system, which I did not plan on using Windows (but now just to watch Comcast DVR) is now 100GB for Windows, 25GB for Ubuntu, 25GB for another Ubuntu, a smallish shared NTFS partition, and a larger ext4 shared data partition.
Windows 10 with fast start on, also keeps shared NTFS mounted, so I cannot see it from Ubuntu.

My Windows system is a Dell/Haswell system with just HDD, I have had no issues with it. And it boots pretty fast to Linux as my other systems have SSD and are very fast booting.

---

### Post by tonma on 2016-10-13
I'd like to get some directions on what to choose in the installation in order to have separate partitions just like you? when I get to the partitioniong part of Ubuntu installation: There are choices like "/" or "/boot" or "/home" and also Primary/Logical, How should I do that in order? Because currently I only did small swap partition and rest is everything (Ubuntu and the data together), Or I can do that even now using GParted or something without reinstalling?

---

### Post by oldfred on 2016-10-13
If a new user the default install of / (root) and swap is all you really need.
I normally fully partition in advance with gparted using gpt since Ubuntu 10.10 with BIOS. But only with UEFI for about 2 years.

For my Dell I made many backups. It came with Windows 8, so I did a Dell backup (and they still nag me on online backup), a Windows backup and a full backup with Macrium Reflect.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp) 

I also then made a Windows Repair flash drive. I think I need to update that to my Windows 10 version.

I used Windows to shrink the NTFS partition originally down to 50GB, but then when it wanted to install Windows 10 and other updates had used a lot of the 50GB, I knew I had to increase it. I made sure fast boot in UEFI and fast start up was off in Windows. And after any NTFS partition change booted Windows just so it can run chkdsk.
Then I used gparted to create the partitions I wanted. I typically do not use all the hard drive, so I can move or add partitions later. Swap is usually at end of drive to keep it out of the way.
Then I use Something Else to install Ubuntu. 
I have more details on typical UEFI install procedures in link in my signature.

---

### Post by tonma on 2016-10-14
Thanks! But if I want to separate the installation from the files? just like you did: 25GB for Ubuntu installation and large ext4?

---

### Post by oldfred on 2016-10-14
I found once I moved all my data folders and some hidden folders with lots of data like Firefox & Thunderbird profiles, my /home was only about 250MB. So I keep /home inside my / (root).

To easily use shared data partition, you need to permanently mount using an fstab entry. You have to create a mount point, like /mnt/data, edit fstab, and give yourself ownership & permissions.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 

When you edit fstab as above and run mount -a, it must not be mounted elsewhere.

If you want to manually mount

 sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data

And then set ownership & permissions, use your mount if not the same as my example.
sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data


 [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

