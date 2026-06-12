---
title: "Splitting Home Directory"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by daksai3 on 2010-08-24
Is it possible to split the home directory into 2, 1 for the personal files (documents, images, videos, music, etc.) and another for the setting files (config, temp, etc.)

---

### Post by brr872002 on 2010-08-24
> **daksai3 said:**
> Is it possible to split the home directory into 2, 1 for the personal files (documents, images, videos, music, etc.) and another for the setting files (config, temp, etc.)

Configuration files are stored in hidden folders ,you can make additional directories in /home and edit permissions

sudo nautilus

---

### Post by daksai3 on 2010-08-24
actually what im intending to do is divide the directory in 2. one for personal file and another for setting files such as config and tmp files. 

and then i want to place the personal files in another partition which will have the NTFS file system. the setting files will reside in another partition which will have the ext4 file partition. 

pls dont ask why, but im sure most of u know what im trying to do.

---

### Post by deanjm1963 on 2010-08-24
What you are trying to do is best done when installing Ubuntu.

I have a partition scheme as follows

/
/home
/documents
/multimedia
/scratch
swap

My home partition is basically empty, and everything else is on the other partitions.

Hope this helps.

---

### Post by daksai3 on 2010-08-24
ok, so say if i do a clean install with ur partitioning scheme, will ubuntu automatically understand that it has to save media files to that partition? and will ubuntu recreate that directory or will it know that there already is one on another diirectory? and will there be any problems since im using two diff file systems. 

ntfs for personal files and ext4 for config and whatnot files.  

and im assuming i have to mount "/home", "/multimedia" "/documents" with a line in fstab right?

---

### Post by deanjm1963 on 2010-08-24
> **daksai3 said:**
> ok, so say if i do a clean install with ur partitioning scheme, will ubuntu automatically understand that it has to save media files to that partition? and will ubuntu recreate that directory or will it know that there already is one on another diirectory? and will there be any problems since im using two diff file systems. 

ntfs for personal files and ext4 for config and whatnot files.  

and im assuming i have to mount "/home", "/multimedia" "/documents" with a line in fstab right?

Ubuntu won't do that automatically for you. I use Ubuntu-Tweak to specify which folders are default, e.g. for downloads it is /scratch/downloads.

Unless you are using windows, I wouldn't use NTFS as a default, I would use ext4.

And those partitions are automatically mounted when ubuntu boots. The only thing you need to do is give them permissions for you to use, e.g.

open a terminal

```
sudo chown -R dean:users /documents
sudo chmod -R 755 /documents
sudo tune2fs -m 0 /dev/sda6
```

you would need to replace "dean:users" with your log in name, and if you wish to remove ext4 "reserved space" which is 5% of your drive (tune2fs), you need to specify where it's mounted, my documents partition is mounted as /dev/sda6

---

### Post by louieb on 2010-08-24
You create symbolic links. Using code something like this. 
```

rm -rIv ~/Documents
ln -s /media/stuff/Documents ~/Documents

```The above removes/deletes the Documents folder in user home directory and replaces it with a symbolic link to a folder on a different partition. 

And yes in this case there is a line in /etc/fstab  mounting the other partition on /media/stuff.

---

### Post by daksai3 on 2010-08-24
> Ubuntu won't do that automatically for you. I use Ubuntu-Tweak to specify which folders are default, e.g. for downloads it is /scratch/downloads.



before i make the home partition containg the config files default will the ubuntu installation make another home directory? and if it does will i have to point it towards the home partition with ubuntu tweak and then delete the directory created by the installation disk?

> Unless you are using windows, I wouldn't use NTFS as a default, I would use ext4.


im using windows 7 thats why i need the personal files to be ntsf, so that i can access them from both places. 



btw does ubuntu have any problems identifying logical partitions?

---

### Post by deanjm1963 on 2010-08-24
You only have one home directory/partition, where the config files are stored. 

Do not delete a partition unless you really know what you are doing, it can bork an entire setup.

On a fresh install of ubuntu, I delete all folders in my home folder except for "Desktop" - it is possible to change the location, but it can cause problems so I leave it as is. Do not delete the hidden " .files "

Once I've set up permissions for my other partitions, I create folders, e.g. on /multimedia I make a folder for "music", "pictures" and "videos", and use Ubuntu-Tweak to set those as the default folders for those kinds of files.

Note: You don't need to set permissions on an NTFS partition, but I think you need to use ntfs-config to make it writable. It's been a long time since I've needed to use NTFS.

Ubuntu has no problems with logical partitions. Any partition number above 4 e.g. /dev/sda5 etc. is a logical partition.

Hope this helps.

---

### Post by daksai3 on 2010-08-24
Ok thanks. This thread was just to account for a small problem i was facing but the bigger picture was to be for thinking of a partitioning scheme. 

the big picture is at this forum thread. 

[http://ubuntuforums.org/showthread.php?p=9759972#post9759972]("http://ubuntuforums.org/showthread.php?p=9759972#post9759972")

pls look at the last post and tell me if it is ok and if thee are ways to improve it. give me ur thoughts pls. 

im marking this as solved, so pls just go to the link i put up.

---

