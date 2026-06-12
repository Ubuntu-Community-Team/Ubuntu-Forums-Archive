---
title: "Ubuntu install - Single boot 2 HDD's"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by blevault on 2010-02-06
I have been working with 9.10 on an older dell with a 1GHz processor 512Mb ram and 2 IDE HDD's. HDD1 - 120GB, HDD2 - 250Gb. The system will sit alone as a file server for music, photos, video and backup to Windows network running XP.
 
I have installed several times now and I am still not happy with the results. I am not sure how I should partition and configure my two drives.
 
I read somewhere to make the boot partition small (8GB), then make the Swap 2x the ram, then make the home bigger to all applications. 
 
Should I load boot on the 250Gb along with home and swap and use the 120GB as backup to 250GB?
 
I am still unsure if I have to partition my drive as a FAT or NTFS to hold my windows files. 
 
Can someone provide feedback on what is a good method to handle this.

---

### Post by darkod on 2010-02-06
I would recommend NTFS for the shared partitions. Ubuntu can read/write to ntfs just fine and also ntfs would be better option for windows too. Plus FAT32 has a 4GB single file limit if I remember it correctly. Being a video/file server, what if you need to put larger file on it?

For the ubuntu install, when you mentioned 8GB I guess you meant root partition, not boot. Be careful, there is a difference.
/boot partition hold literary just the boot files and is rarely used today, except maybe on servers in corporation networks. And even if you decide to have it, no need to be bigger than 100MB usually.
Your / partition is like C: in windows, holding the OS. By default, ubuntu desktop install is approx 2.7GB, so depending what you want to install on top (and software is linux is not as demanding for space as in windows), 10-15GB is plenty.
Swap is nice to be 150% of ram if you plan to hibernate regularly. Otherwise, depending how much ram you've got, a swap of 2GB is more than enough. Unless you have 1GB or less ram, it rarely even gets used. Hibernation is another question, because it needs to save the ram content there, hence it needs to be slightly bigger.
All the rest can go to /home partition.

But, having said all that.... If linux is your only OS, in fact LVM is perfect solution. Logical Volume Manager. I had one link bookmarked but it doesn't open right now. Google will give you a lot of tutorials for LVM.
The basic is: You create one single partition out of your hdd (or even more hdds if you want), you dedicate the whole partition (whole disk in fact) to the LVM, and you create the linux partitions as logical inside.
That allows you to start with for example 5GB root, 2GB swap, 10GB /home. For what ever partition, if you decide you need more space, you just enlarge it live while ubuntu is still running. No need to shutdown, to repartition, to reformat, nothing. Until you reach the limit, which would be your hdd partition (disk) size, you can enlarge any of the partitions as you like.
It's a beauty. And not complicated to set up too. Once you finish the install there is GUI tool in ubuntu which helps handle the logical partitions easily.
It's worth reading about it, IMHO.

---

### Post by blevault on 2010-02-06
Darko,
Thanks that makes a lot of sense. You are correct that I incorrectly was typing boot but was thinking root.. I am thinking about getting a faster CPU with SATA and RAID and making a better server. For the time being, I am just trying to get a good setup on what I have. One for the experience and two, to give me some time working with Ubuntu / Linux. 
 
I have anothe question on NTFS partitions. I have SAMBA loaded and my 250GB drive partitioned as NTFS (WinMedia)and it mounts /media/WinMedia. What I am finding is that when I share that partition or any folders created under that partition, I cannot write to them from my PC. I get an error "Access Denied" Do you have any ideas. I can share /home/pictures for instance and access it no problem, but not any of the NTFS shares. 
 
Thanks, Bill

---

### Post by darkod on 2010-02-06
Sorry, I'm not familiar that much with ubuntu yet, too. I haven't tried sharing with windows and know almost nothing of samba.

---

### Post by oldfred on 2010-02-06
I did not quite understand. Are you sharing your NTFS partition with another computer or just on your existing one? I have had Samba working with every update for the last 3 years and every update I seemed to have to reset something. I only used it to refresh my portable when traveling so I just gave up, installed Ubuntu and NFS on my portable. I dual boot both and copied all my NTFS data using NFS. But now I find I do not even need windows on my portable.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by blevault on 2010-02-06
Old Fred,
The ubuntu machine will be accessible on my home network to house pics, photos, music, video and serve as a backup for networked PC's running XP. 
 
I assume that I need NTFS to handle the windows files that I will be backing up. However, I think the photos, music and video will sit fine on any partition format from what I can tell. I am thinking that I want a large NTFS share to house everything from my list above. 
 
When I created NTFS shares, I find that I am unable to write from my PC over my home network even when the write permissions are set in SAMBA. 
 
I am currently reducing the sizes of my root and home directories on the ubuntu machine. After I want to set up folders to house my data and have it accessiblel from the home network.

---

### Post by oldfred on 2010-02-06
I am not knowledgeable on Samba but have saved these links.

Howto: Fix Windows share browsing issues 
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
Sharing issues
[http://ubuntuforums.org/showthread.php?t=1374369](http://ubuntuforums.org/showthread.php?t=1374369)

 HOWTO: Setup Samba peer-to-peer with Windows 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
For definitive explanation of SMB (CIFS) and how it works, see here .
[http://ubiqx.org/cifs/SMB.html](http://ubiqx.org/cifs/SMB.html)


[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting)

You may do better with Samba issues in your thread title as there are a few here that can help. They make not look at boot issue issues.

---

