---
title: "Question regarding data partition for ubuntu/windows dual"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by flyingsilverfin on 2014-08-04
Hello all, I feel like this is a relatively simple question but I'm not sure what is the best way to go about it:

I'm planning to have a dual boot windows 8.1 and ubuntu (on separate sata m.2 ssd's, but that's irrelevant I think), with a separate data partition (technically this is a separate hdd but also irrelevant). The overall goal is to have all my data unified on the data partition from both windows and ubuntu.

I like to have my data partition usable as a simple folder on my OS. I know on Windows there's a way to configure a drive to show up as a folder, lets say I like is showing up next to the Desktop (call it 'data'). However, in order to have something like that, I believe I need to use ntfs or fat32 for the data partition, correct?
On ubuntu I'd like to have the same thing, but I also like to have the /home partition separate. So I think what I want to do is install ubuntu with a separate /home partition, and have a folder say /home/flyingsilverfin/data where I mount the data partition. However, is it a problem if data is nfts? I know ntfs does not support file permissions, but is that all I would lose out on?

Thanks

As an aside, does anyone have a knowledge towards using RAID with my dual ssd's to get a speed boost/make the two appear as a single 256gb drive?

---

### Post by Bucky Ball on 2014-08-04
Welcome. Use NTFS, not FAT. 

On the data partition, you can put all the regular /home directories - documents, videos, music, etc. - then create symlinks from your /home partition to the directories on your NTFS data partition. (You either move or delete the directories in /home existing currently inside /.)

Symlinks in the Win install to the same directories and you're done.

No idea about creating symlinks in Windows, but in Ubuntu is easy. 

I have a number of Ubuntu installs and all their /home directories contain symlinks to the same directories inside the data partition/drive. I have no 'actual' directories in any of the /home(s).

---

### Post by flyingsilverfin on 2014-08-04
Thanks for the quick reply!

I'm actually an old user but haven't been here in a while; returned to find the forum using ubuntu one logins and stuff, mistyped my name and I guess my old account didn't get connected or something. No big deal.

Symlinks seem like a good solution. I might just do one for a documents folder then to make it easier with windows.

---

### Post by oldfred on 2014-08-04
I have sim links for folders in both my old NTFS partition (still) and Linux formatted data partitions.

 I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

      
 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)


 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mout to.
[http://ubuntuforums.org/showthread.php?t=2227574](http://ubuntuforums.org/showthread.php?t=2227574)

---

