---
title: "dual boot ubuntu"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by doja on 2013-03-15
Dear friends I've question,

I've dual boot (windows and ubuntu), but I would like to try additionally a new Ubuntu.
An additionaly OS should not be a problem. But how is it if I've /home in one separated
partition. Can I use one /home for two Ubuntu installations or every installation needs one.
In /home are (hidden) directories assigned with the names of programs that are already
 installed and that may be a problem.

Maybe you know some links where I can find an answer.

---

### Post by oldfred on 2013-03-15
Some say a shared /home works. But they usually use two different user names so nothing is shared except the partition. A few have used same name but then eventually run into conflicts.

I leave /home inside my / (root) but relocate all data in Documents, Videos, Music etc that is just data into a data partition. That is easily shared. I have two data partitions, one NTFS from when I still booted XP, and all my new data goes into a Linux formatted shared data partition.

       I prefer a separate /mnt/data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by doja on 2013-03-16
Thanks oldfred,
you didn't only answered my question with your first sentence, you also understood what I want to do and proposed a quit good solution.

For my dual booting with windows I have also a separated partition for data (which is NTFS so I can reach it from both OS).
The /home or My Documents (in windows) are not good solutions for saving data, because you are not the only one who manage the directory. Many programs create some crap in your /home and mess the data. So I use /home only for temporarily working before a I decide to shift the data to data partition.

The extra /mnt/data partition and leaving /home in OS partition seems to be a good solution, especially if you have multiple booting.

---

### Post by oldfred on 2013-03-16
Glad I could help. :)

---

### Post by doja on 2013-03-16
oldfred or anyone else,

maybe you can help me once more. I mess up my system little bit.

As I wrote my /home is in a separated partition.
I was trying to move my /home in the OS partition, but I did it in wrong order.
I commented out the link for my /home in fstab, without moving it before in the OS partition.
After restart I can't log in and change the fstab back because now my PC has no /home
 and therefor don't know my passwort which is actually in /home that is not linked. ;)


And without login I can't make any sudo action.
Maybe there is some trick to create a new /home and then replace it with the old one.
I tried the recovery modus with mkdir /home but I have only reading rights that I can't change.
I could login also as a guest.

I've already a second Ubuntu installed and can see my old /home, but I would like to recover
 my old system because of all the settings and istallations of programs.

Thanks

---

### Post by oldfred on 2013-03-16
I do not know details of password, userID issues. I always use the same for every install so I do not get confused. 

But you should be able to mount your old fstab and restore the old entry from any other install or liveCD. If you may need sudo, and from liveCD there is no password.
And it normally just creates a new empty /home if you comment out a separate /home in fstab. It will have same user & login as that is in system, not /home. But all user data is in /home.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by doja on 2013-03-16
Dear oldfred, I restored my /home again. Thanks.

The point was that I didn't know how to reach my old_ubuntu when I couldn't login into the system.
I opened in the new_ubuntu nautilus but couldn't copy the /home from the partition where it was
 in my old_ubuntu OS partition.

So I used the link you sent me
[https://help.ubuntu.com/community/Pa...ng/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

I operated from new_ubuntu where at first I went in terminal
into /root of my old_ubuntu. Then used the command

sudo rsync -aXS --exclude='/*/.gvfs' /hdd_partition_with_home/.  /root_old_ubuntu/home/.

which copied my lost /home in the OS partition and after restart everything worked.

Now I'm curious to try the new OS without overwriting my 12.04 lts. :)
________________________
But before I couldn't start the old system with any password I usually use (for user or system),
even withouth password it didn't worked. Even if I saw in the nautilus that my old_ubuntu created
one empty directory /home.

---

### Post by doja on 2013-03-16
In addition I copied the /home also in my new_ubuntu installation and have it all configured. This is really good.

---

