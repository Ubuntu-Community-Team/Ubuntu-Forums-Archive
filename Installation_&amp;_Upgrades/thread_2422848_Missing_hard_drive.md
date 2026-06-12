---
title: "Missing hard drive"
date: 2019-07-13
forum: Installation &amp; Upgrades
---

### Post by dtree46 on 2019-07-13
Installed Ubuntu 18.04 LTS.
During installation, the system did not find 2 - 1tb hard drives; only one.
How is the second drive installed?

---

### Post by TheFu on 2019-07-13
If you have a specific purpose for the other storage, that would be helpful.  Also, how you've setup the current disk would be helpful.  There are multiple posts on "the ideal disk layout" in these forums.  It is easy to make less-than-great choices, since the defaults are pretty terrible.  The default layout is meant to be easy, not EXCELLENT.  

If you'd like suggestions for making it all better than the defaults, ask.

You partition it, then
you format the partition(s) with the file system you want, then
you find the UUID of that partition using **blkid**, then 
you create an empty directory, called a "mount point" for where you want to mount the partition device, then
you manually edit the /etc/fstab file to mount the partition where you want it, providing the needed mount options.

So, there's a GUI tool called gparted which will handle all the parts up to and including the file system formatting. It may not be installed, so 
```
sudo apt install gparted
sudo -H gparted
```

For how to do the fstab, there's this guide: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

A few tips:
* Use a Linux native file system like ext4 if you are new.
* If you chose LVM during the install process - stop and let us know. Some of the instructions are different.
* If you chose LUKS encryption during the install process - stop and let us know. 
* If you think you need to use a non-Linux file system - STOP. Let's talk about why and the issues with doing that.

Coming from Windows, many people don't understand that there are a few choices made when a new HDD is being added which can really make your life easier later.  
a) use GPT for the partition layout if you can. Not MBR/MSDOS.  Many reasons for this.
b) don't use the entire disk, leave 10% for needs later.  20% if it is an SSD.
c) If you have any interest in file systems, leaving a little extra for play storage will make it much less risky to try things out.
d) If you have **any** interest in using LVM, when starting with a new HDD, that is the best time besides during the installation.

In Unix, the power to add storage is the power to overwrite/destroy existing storage. Be very, very, careful when doing these things. A mistake might wipe your install and all those files.  If you mount the new partition(s) somewhere incorrectly, existing storage might become unavailable until you remove that mount.

And please, please, make a 100% know-you-can-restore backup before starting any of this.  Partitioning is a dangerous thing, especially for people who aren't used to doing it.  It is pretty common to accidentally wipe an installed OS and all the files because of a tiny mistake.  Linux will do what you tell it to do.  It usually won't try to stop mistakes. It does what you say, not what you meant to say.

---

