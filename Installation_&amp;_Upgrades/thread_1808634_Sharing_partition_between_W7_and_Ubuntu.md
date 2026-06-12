---
title: "Sharing partition between W7 and Ubuntu"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by swimon on 2011-07-20
Hello,

I've just, for the first time, set up a dual boot system. 

My 320GB HDD is partitioned as follows:

1- 105 MB NTFS - System reserved (partition created during windows installation)

2- 17 GB  NTFS - Contains Windows 7 OS

3- 303 GB Extended Partition
 -> 300 GB EXT4 - Contains Ubuntu OS
 -> 3 GB - SWAP


So I was thinking to divide the extended partition. And make a new NTFS partition (so both Ubuntu and Windows can acces that one). 

Just a couple of questions:

- How big should the ubuntu partition be at minimum? I'm planning to move all my personal documents/pictures/movies/data to the new partition

- Should the new NTFS partition come before or after the extended linux partition?

Grtz!

---

### Post by Quackers on 2011-07-20
If everything of any size is moved to the new data partition I would say 15GB would be big enough for Ubuntu.
The position of the NTFS partition shouldn't matter.

---

### Post by swimon on 2011-07-20
Okay, thanks for the advice again ;)

Yes I plan to move all my data to this new partition. 

Except maybe for applications, I'm not sure if it's possible (or recommended) to install apps in a different partition in Ubuntu?

I'm a bit new to all this, all my previous experience in Ubuntu I just had one partition an no dual boot or anything.

Grtz!

---

### Post by Quackers on 2011-07-20
Apps will go in your root partition, so unless you intend to install thousands of apps you should be fine, afaik.
Maybe someone else will chime in with further views :-)

---

### Post by swimon on 2011-07-20
Thanks,

just another quick question:
Should I repartition the extended partition or the linux partition within that extended partition?

I thought it was supposed to be the first option. But the app 'Disk Utility' wont let me. Or should I use another app like Gparted?

Secondly, should I boot into a LiveCD Ubuntu to do this? Since I'll be accessing the same partition as the one I want to divide.

Grtz!

---

### Post by Quackers on 2011-07-20
You should do it with gparted from the live cd. It won't let you do it to a mounted file system. You may need to right-click on the swap partition and select "swapoff" first - even from the live cd.
You need to shrink the ext4 partition then create the new NTFS partition as a logical partition in that released free space.

---

### Post by swimon on 2011-07-20
Okay, thanks again, you've been very helpful to me today :)

Too bad I left my Docking station (with my only CD drive) at my mothers house... so can't run LiveCD until tomorrow, but I think I'll be able to figure it out now!

Grtz!

---

### Post by Quackers on 2011-07-20
You're welcome. Have fun :-)

---

### Post by swimon on 2011-07-21
It worked like you said. 

My linux partition is now +/- 16 GB
And created a partition for my data of about 283 GB.

I made this last partition NTFS, because I wanted to share this between W7 and Ubuntu.

So now I wanted to move my /home to this new partition, but then I read this was not a good idea and I wouldn't be able to log in again if I did this. (NTFS can't handle the permissions used by Linux, or something like that...)

What might be another way of doing this? I've found that there is and EXT2 driver for windows ([www.fs-driver.org](www.fs-driver.org)) but it doesn't seem to work for windows 7. If there's another driver that works for W7, I might repartition the NFTS partition as EXT2 and move /home to there without any issues.

Another solution I read about was making a symlink, but I not to sure about how that would work.

I might just leave the /home were it is and manually create the folders I need on the new partition. It's just not that 'clean', 'cause I'll have double home folders sort of speak... 

What do you guys think is the best solution?

Grtz!

---

### Post by swimon on 2011-07-21
Is it possible, by creating symlinks, to have for example a folder 'Downloads' on the NTFS partition to be symlinked with the folder in /home/simon/Downloads (on the linux partition) ?

So when I download something, I'll choose destination /home/simon/Downloads, but it will actually be physically downloaded to the NTFS partition? So I can acces it when I'm on windows?

(I'm pretty much still figuring out how symlinks work, where is the data saved? On both locations? Or only on the location to where it's linked?)

Grtz!

---

### Post by oldfred on 2011-07-21
The symlink is just that, that data only exists in the NTFS partition. I symlink my shared NTFS partition and from an data (ext3) partition all my folders normally in /home. My /home now is about 1GB with most of that my .wine with Picasa.

You can also move your Firefox & Thunderbird profiles without the symlinks just by changing the profile.ini to the new location.

You have to permanently mount the NTFS partition for the symlinks to work.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by swimon on 2011-07-21
Thanks for the info, 

I've been trying on my own a little bit too and came up with this solution. You mind telling me if this is a good solution?

(btw I don't use thunderbird)

Example:

I make a folder called Pictures on my NTFS partition -> /media/23C125F41A90FDB0/Pictures[SIZE="2"] (btw, what does that long string of random numbers/letters stand for? can't I change this to something more readable?)[/SIZE]

I remove the folder Pictures from /home/<username>

I make a symlink in /home/ like this ->
ln -s /media/23C125F41A90FDB0/Pictures/ /home/<username>/

So now I have a symlink in /home/<username>/, every picture I save there, is actually physically saved on the NTFS partition. So I can access it in Windows aswell as in Linux.

What do you think of this solution? 

Grtz and thanks again.

---

### Post by swimon on 2011-07-21
another question about symlinks

For example, I have a symlink on one partition, this symlink points to a location on another partition. 

If I save let's say a 1000MB file while using the location of the symlink. Will that file first be saved on that partition and then copied to the final partition. Or will it be directly saved in the final location?

---

### Post by oldfred on 2011-07-21
A link is not a location just a link to the real location.

The long number is the UUID. A unique ID for each partition. 

You can directly mount each folder without the link the way you are doing it. I prefer the links, but there are several ways to do things.

With NTFS you do not have control over ownership & permissions since that is not part of NTFS. So you set ownership & permissions at time of mounting.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by swimon on 2011-07-27
Finally fixed this. I decided not to use a NTFS partition after all. (although I think it's possible). I found it was easier just to reinstall Ubuntu from scratch and choose custom partitioning during the installation. 

There I created a 15GB Ext4 partition for the Ubuntu OS and a 280 Gb Ext3 partition and mounted it to /home. 

On windows 7 I downloaded another Ext2/3 driver called Ext2Fsd ([http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)) 'cause I couldn't get the other one to work properly on windows 7 ([www.fs-driver.org](www.fs-driver.org))

It all seems to be working great so far.

Grtz

---

