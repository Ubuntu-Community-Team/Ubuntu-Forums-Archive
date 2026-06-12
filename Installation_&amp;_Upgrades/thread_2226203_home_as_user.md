---
title: "/home as user"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by fadyfadlallah on 2014-05-26
Hello,

I will be installing ubuntu on my new laptop. I am going to dual boot it with windows.

My question is, will it be possible to bind a partition's root directory to a user e.g:
Instead of having /home/user I would have /home or just /user.

The reason I want this is becaus I intend to share that partition with windows while adding ext4 support on my windows setup.

So instead of having that partition in a subfolder of the username I just want it to be in the partition's root folder. So instead of accessing a song through x:\user\music it would be x:\music

Thanks

---

### Post by vanadium on 2014-05-26
You can put your user home directory on a separate partition, then mount that partition during startup, using /etc/fstab, to your user folder under /home.

---

### Post by oldfred on 2014-05-26
Better to just create another shared NTFS data partition and link Music in /home to a Music folder in the shared NTFS partition. I have both a Shared NTFS from when using XP and a shared Linux formatted partition as I have several installs of Ubuntu. Both get mounted in each install.  Since not using Windows anymore I will evenually migrate my shared NTFS to Linux.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

