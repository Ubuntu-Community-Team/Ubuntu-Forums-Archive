---
title: "How to setup a second HDD for Owncloud Data"
date: 2017-06-08
forum: Installation &amp; Upgrades
---

### Post by esnrhtx on 2017-06-08
I am kind of new with the Ubuntu/Linux OS. I have been trying to figure out how to setup a second HDD for the data in Owncloud. I have been working with this on and off for 2 years and I can't get it right. I'm using 16.04 LTS with the LAMP server and I'm installing the Owncloud package. If I default install Owncloud everything works fine except I have no more space on my SSD. Basically I just want to put all of the data on the second HDD with a fresh Owncloud install.

   If I try to change the data path during install it says that it can't create the directory. I have been on multiple forums and can't find the answer to fix this. I know my problem is the mount and permissions. I can't possible type all of the stuff that I've done so far. Is there anyone that can give me a step-by-step list as to what to do? I know some of you can do this in your sleep and I would appreciate it and forgive me if I say things in the wrong context. I'm a noob with this.

  My drive automatically goes to /dev/sdb. I name the HDD to ocdata from the disks menu. From what I understand, I have to make a directory next. Do I have to path to the HDD and make a directory on it or just under /media/ocdata? In the past it kept going to /media/compname/ocdata. 

   I think it would be easier if someone can just give me directions because I know I'm screwing this up and it won't be clear. A simple step 1,2 ,3... list would be great with examples. Everything from making a directory,mounting it, permissions and fstab entry would be awesome. In the proper order too please. I know the uuid number isn't here but "uuid" would be fine, if needed.

The HDD name would be "ocdata", the directory would be "storage" and the comp name would be "noob". I'm not really sure but from what I understand the mount cannot be /media/noob/ocdata. This would really help me a bunch and I can finally get this off my plate. I'm not really sure of how all of this stuff works and I'm sorry if some doesn't make sense.

Thank you for your help!

---

### Post by TheFu on 2017-06-08
Welcome to the forums.

2 yrs? Ouch.

I use nextcloud, not owncloud, but it is a fork, so very similar.
a) never mount permanent storage under /media/  That's where the OS places dynamic media, like from USB drives.
b) If you like, you can leave the default locations in the webapp and use symbolic links.
c) The HDD must be formatted with a Linux file system. NTFS is not ok.
d) For mounting, there is an **fstab** how-to here in the help.ubuntu.com site. It is easily found using any search engine.  Changing from NTFS to EXT4 will change the UUID for each partition changed.
 
If you've never used symbolic links, learn. Now. Today. Play around for 2 minutes and everything will be clear.  Use **ln -s** and plain **ln**. Be certain you understand the difference and limitations for each.

Here is my nextcloud data:
```
$ df .
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        19G  6.3G   12G  36% /
```
I don't have a separate mounted disk like you.  I just don't keep much data in Nextcloud (i don't trust php webapps). Plus I don't let php be accessed directly on the internet. It is only available from inside the LAN.

The permissions for the exact directory:
```
$ ls -al
total 16
drwxr-xr-x  4 root     root     4096 Feb 20 08:02 ./
drwxr-xr-x 25 root     root     4096 Jun  7 06:16 ../
drwxrwx---  8 www-data www-data 4096 Jun  4 06:29 nc-data/
```
Your owner and group need to be the same on the mounted storage.
Maybe a clearer view would help?
```
$ pwd ; ls -al
/opt/nc-data

total 88760
drwxrwx--- 8 www-data www-data     4096 Jun  4 06:29 ./
drwxr-xr-x 4 root     root         4096 Feb 20 08:02 ../

```

Hopefully this is all helpful. I am not using symlinks today, but probably would in your situation. At least initially.

---

### Post by esnrhtx on 2017-06-09
Thank you for your input TheFu. I will look into symbolic links. Like I said I'm still a noob and stubborn, lol. So, I have to make the directory first, correct? Do I just put it anywhere or in /home or like /storage? I think this is where I have the issue. I noticed that yours is mounted under /opt? When I mount the 2nd HDD, do I just mount it like /storage? Or does it need to be like /home/storage? I notice the hdd shows as /dev/sdb, I thought it would be sdb1. These are the little things that confuse me. I did the fstab a few times with bad results, typically doesn't boot. I've followed youtube videos and read lots of forums trying to edit fstab but I just can't get it right. I have nothing else on this pc so I just cleanly install Ubuntu, trust me it's getting old. I want to use Nextcloud because it seems to have more options and is constantly improving things. It seems that OC is kind of dying. NC seems to be a bit more complicated to install, at least in their admin manual so I figured since I can't get OC installed then I shouldn't even try. If we can get this working, I may try later. I keep notes and samples of what does work so in case something happens I know what TO do and not to do. The hdd must be owned by www-data and be set at 770, right? If I can get this working properly, I'll get you a giftcard for dinner or something. I really appreciate your time with this!

---

### Post by SeijiSensei on 2017-06-09
1) Create a single partition on the drive and format it for ext4.  You can use gparted for this.

2) Create an empty directory on the main filesystem, lets call it /media/owncloud, where the new drive's filesystem will be mounted:
```

sudo mkdir /media/owncloud
sudo mount /dev/sdb1 /media/owncloud

```

3) Copy the files to /media/owncloud.  You may need to do this as root with sudo.

4) Make sure you can read and write files there:
```
sudo chown -R yourusername:yourusername /media/owncloud
sudo chmod u+rw -R /media/owncloud

```
replacing "yourusename" with your login name.

4) Edit /etc/fstab as root with sudo (e.g., "sudo nano /etc/fstab") and add the line
```

/dev/sdb1     /media/owncloud     ext4     defaults     0 0

```
so it will be mounted automatically at boot.

---

### Post by oldfred on 2017-06-09
If your owncloud needs a specific mount point and/or link, you need to use that.
Make sure you have partitioned & formatted drives, not just formatted a drive like sdb, you format partitions like sdb1.

To see UUID.
             sudo blkid -c /dev/null -o list 
         [URL="http://ubuntuforums.org/showthread.php?t=1983336"]
http://ubuntuforums.org/showthread.php?t=1983336[/URL]
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 
fstab entry For ext4, copy & paste into fstab with your correct UUID & previously created mount point, Example template:
```
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /mnt/data ext4 defaults,noatime 0 2 
```
Always run this to confirm no errors, it it just returns then it mounted ok.
sudo mount -a

I use links for all my data as I keep smaller / (root) partition and larger data partition with all user files & folders normally in /home and some larger hidden folders that have lots of data like Firefox profile & Thunderbird profile.
But the way I use links, is assuming the location I want link is where I run it and I always run in /home. So it defaults. Full command can have from & to.
So if you need link elsewhere you either need to change to that location or use full command. see man link
      
 [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

### Post by esnrhtx on 2017-06-10
Thank you for your reply SeijiSensei! 
[COLOR=#000000]
4) Make sure you can read and write files there:[/COLOR]
[COLOR=#000000]Code:
sudo chown -R yourusername:yourusername /media/owncloud
sudo chmod u+rw -R /media/owncloud
[/COLOR]
Doesn't the mount need to be owned by www-data:www-data? The install I'm doing is a fresh install of OC and during the install I want to change the default data folder to this mount. Do I have to leave the owner as the login name to do this? Then after the install is done, chown it to www-data:www-data so OC can rw? During step 3 you say to copy the files, are you saying to install OC? This may be the issue of OC not being able to rw that mount during the install(if what I'm saying is right), I think I have the owner of the mount as www-data when I try to install OC. It needs to be owned by me, right? I'm going to work on this a little later today and see. I'll let y'all know a little later. Thank you for your help!

---

### Post by esnrhtx on 2017-06-10
Thank you for your reply oldfred. 

[COLOR=#000000]Make sure you have partitioned & formatted drives, not just formatted a drive like sdb, you format partitions like sdb1.[/COLOR]

I think that what you're saying is that I formatted but didn't make a partition. Yep, I didn't do that. Easy solution for that! Is it better to use the UUID in fstab than just the mount point? TheFu also mentioned using links. That sounds like a good idea but I fell I would mess that up pretty bad. Correct me if I'm wrong, so you would keep the default install but you would link the new data folder to the default data folder and the link would basically route the data from the default data folder to the new data folder so it goes to the bigger storage but in OC's "mind" it thinks it's all in the default data folder? I know that is confusing,lol. This whole thing with trying to install OC that way I want it has been a big experience. I know some of y'all could have this done in 5-10 minutes because you've used Ubuntu so much. Thanks again!

---

### Post by oldfred on 2017-06-10
The entry in fstab has both the unique partition info like UUID & the mount point.
You can use labels, but I see few users using the labels and you can use device like /dev/sdb1, but when I plug in a flash drive and reboot the device changes. On one system my sdf flash drive became sdb and every drive become one letter more.

I do label all partitions either with gparted when I partition. Or sometimes with disks when I forget or change something. Some partitions I do not auto mount in fstab, so the labels help me know which partition it really is rather than some long UUID.

Because I am just using links to link my data back into /home I use myself for ownership.
Do not know then whether you need owncloud or www-data, or something else?
Does installing owncloud add itself as a user?
use id to see users.
fred@Z170N:~$ id
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),122(lpadmin),127(sambashare)

---

### Post by cc1984 on 2017-06-10
[COLOR=#000000]> Doesn't the mount need to be owned by www-data:www-data?
[/COLOR]
Once you have drive mounted the system is going to look at it just like it is any other directory. So, if you mount the drive at /media/owncloud that is your data directory. If it were me I would name it something other than owncloud (maybe ocdata or something) to prevent confusion with /var/www/owncloud.

Yes, the data directory that you set up needs to be owned by www-data:www-data.

> [COLOR=#000000]The install I'm doing is a fresh install of OC and during the install I want to change the default data folder to this mount. Do I have to leave the owner as the login name to do this? Then after the install is done, chown it to www-data:www-data so OC can rw? During step 3 you say to copy the files, are you saying to install OC?[/COLOR]

The data directory will only contain "data" that you store in OC not the install files or the files that OC needs to run. Since you haven't installed OC yet you probably don't have anything to put in this directory.

Once you have the drive mounted use chown to set the owner of the directory then follow the OC install instructions and tell it where you want the data directory to be (/media/owncloud or whatever you use). I use Nextcloud as well but I think the OC instructions should have a sample script to set all the ownership/permissions properly. I recommend you use that script and edit it with your new data directory. That will allow you to quickly ensure that all the permissions are set properly.

> [COLOR=#000000]I'm going to work on this a little later today and see. I'll let y'all know a little later. Thank you for your help![/COLOR]

Give it a go and let us know the results.

---

### Post by TheFu on 2017-06-12
> **esnrhtx said:**
> 
Doesn't the mount need to be owned by www-data:www-data? 

Yes it does.

With most things Unix related, there are often 50 different methods to solve an issue. You can certainly mount the other partition exactly where you want it. Be certain to shutdown the web server and move any existing data to the new storage BEFORE mounting it to the permanent location.  
You can certainly create another new group and put both OC and yourself into that group, then setup g+s on the directory with g+rwx and have that work for your needs, but since you are very new, I didn't want to push non-trivial file and directory permissions. But ... it could work.

The only real requirement for storage is that data/directories need to appear where it was on the old storage in the directory structure after the relocation to the new storage, if you don't want to change any config files too.

Really need to have at least 1 partition on the disk and mount it. Storage without partitions can confuse humans in the future. We will think it is an empty disk if there isn't at least 1 partition.  There are old discussions about this in the RAID groups, because RAID disks do not need partitions and many old-school teams never bothered creating any partitions. 
/dev/sdb is the whole drive.
/dev/sdb1 is the 1st partition, provided it exists (fdisk/parted/gparted)
/dev/sdb2 is the 2nd partition and so forth.
Partitions can be mounted by multiple methods.  Using the device name (sdb1) is to be avoided for permanent mounts. Sometimes device names change at boot as different devices are found in different order.  UUID, Labels, and "by-path" prevent that issue.  Most home users would use the UUID, probably because that has the most examples and running 'blkid' shows the mapping.
There are other generated-at-boot links - /dev/disk/ has those.
```
$ ls -F
by-id/  by-label/  by-partlabel/  by-partuuid/  by-path/  by-uuid/
```
Many enterprises use the 'by-path' which is really by a connection path and how Unix systems have worked for 40+ yrs. As long at the storage connection patch doesn't change, this will be stable from boot-to-boot.  You can look an see the links from those back into the device names. It is well-worth the 3 minutes to look at long-listings inside each of those directories to see how they are connected.
I use *Labels* for mounts for portable devices. It is a convenience thing, just have to manually ensure all those storage devices have unique Labels. In the mount command, use LABEL= instead of UUID=.  Handy, since we can set a reasonable label "name" that makes sense.

Switching gears, I never mount storage under /media/, but I see some others are suggesting that.  /media/ is where linux automatically mounts stuff and I'd rather NOT have that confusion (and occasional bugs) to cause issues.

I used  /opt/nc-data/ for the data storage.  /opt/ because I'm lazy and use /D and /Data for NFS storage.  /opt/ means it is local. BTW, Nextclound supports NFS data access. I use it for media files - read-only exports to the nextcloud server. I don't trust php webapps and don't want to have any chance of the NC webapp to wiping those files. But that is just me. Many, many, many, people/orgs trust it. India has a country-wide owncloud setup for 1B+ people when they deal with their citizens. They certainly are NOT stupid people, but I wouldn't have made the same decision.

Sorry for the delay in my reply. Travel.

---

