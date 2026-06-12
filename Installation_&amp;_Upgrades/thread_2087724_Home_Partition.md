---
title: "Home Partition"
date: 2012-11-24
forum: Installation &amp; Upgrades
---

### Post by offgridguy on 2012-11-24
Hello;  Does the separate home partition, allow sharing of the home folder between
Different OS , IE:  ubuntu, kubuntu, xubuntu ?
    If so i am assuming it needs to be an nfts partition?   I have allocated 25gb for each
system,  what would be appropriate for home , size wise ? :)  TIA.

edit; I was looking at this quote from oldfred,  i am not sure how to do this?
> 
I would not try to share /home although since so closely related it  might work. Better to just create a /mnt/data partition and you can  store data in that and mount it in all three partitions. 

---

### Post by darkod on 2012-11-24
If sharing /home between linux distros it doesn't need to be ntfs. ntfs is so that windows can read it.

But I agree that sharing /home can create issues, even when the distros belong to the same "family".

As suggested, one option is not to create a separate /home (leave it inside /) of small size, and create one bigger partition for sharing all big data files, videos, photos, etc.

Use manual partitioning when installing the first OS, but instead of creating a bigger partition with mount point /home, use the mount point /data for example. It will be created and present in the OS filesystem as /data.

For the next OS installs, you only create the standard / and swap partitions. Once the OS is running, you can add an entry in /etc/fstab to mount and use the /data partition.

---

### Post by 2F4U on 2012-11-24
> Different OS , IE:  ubuntu, kubuntu, xubuntu ?

Technically, these are not different OS's. They share the same base but have different desktop environments. You can even have all these desktops in the same install, i. e. you install, for example, Ubuntu, then add through the software center the desktops from Kubuntu and Xubuntu. At the login screen of Ubuntu you will then be able to select the different desktops.

Back to topic. With different Linux distributions it can indeed cause problems to have a share home folder, because every distro stores configuration settings in the home folder. It may be a better idea to have a separate data partition instead, that is accessible from all distributions, but keep a small home folder for each distribution.

---

### Post by oldfred on 2012-11-24
All Linux system partitions including /home have to be Linux formats.

Shared data can be Linux format or NTFS, I have both still. I shut down XP and should remove my NTFS shared as now I cannot run chkdsk easily. Best to only use NTFS if you have a Windows install and can run chkdsk periodically. Ubuntu runs file checks on Linux formats every 40 or 60 reboots, but cannot run chkdsk.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

    
       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

    
If not in Debian family with UID of 1000, then you may have issues unless you change UID.
       Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by offgridguy on 2012-11-24
Thanks to everyone for the input, I appreciate it.

---

### Post by offgridguy on 2012-11-25
> **2F4U said:**
> Technically, these are not different OS's. They share the same base but have different desktop environments. You can even have all these desktops in the same install, i. e. you install, for example, Ubuntu, then add through the software center the desktops from Kubuntu and Xubuntu. At the login screen of Ubuntu you will then be able to select the different desktops.

.
Probably a better choice of words would have been "separate" OS.  Actually one
reason i went this way is to stay with the default apps. that come with each 
version.

---

