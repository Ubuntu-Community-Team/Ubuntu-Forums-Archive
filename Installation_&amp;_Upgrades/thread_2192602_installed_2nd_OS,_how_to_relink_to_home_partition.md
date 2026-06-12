---
title: "installed 2nd OS, how to relink to /home partition?"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by Razmear on 2013-12-08
The system was 12.4 32 bit, with /home in it's own partition and mounted as /home
I just installed 13.10 64 bit into a new partition and need to relink /home so my wife can get all her settings and data back. 
The 500 gig drive is currently partitioned as:
/home 350+gig
12.4 install 50gig
13.10 install 50gig
swap 6gig
The user names and passwords are the same for both installs. 
Braincramping on how to get this done so a pointer to some instructions would be awesome. 
Also will there be any issues with data in her /home folder between the 32 and 64bit OSs that I should be aware of. 
Thanks,
eb

---

### Post by Razmear on 2013-12-08
OK, I see my error.
From: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Telling Ubuntu to use an existing home partition can be done by selecting "Manual Partitioning" during the installation of Ubuntu and specifying that you want your home partitions mount point to be /home,...
Which I did not do. 
Would it be easier to reinstall and let the installer take care of this or is there a post install edit that would be quicker. 
Thanks again.
eb

---

### Post by electrohandyman501 on 2013-12-08
Not totally sure about redirecting the new install to the old /home as the current /home. 
With differences between old/new versions and such and not knowing what files are in the old /home directory, I'd be leary of using all of the old /home in the new system.
What you could do is to creat an individual(new) mount point(folder) for the old /home partition so that you can copy(save) document files and such to the new /home directory location. 
It does sound kind of time consuming, but in the end it may be safer/cleaner for you.
When you are all done transfering all that you want you can just remove the mount point and have a partition to reuse for something else.

---

### Post by oldfred on 2013-12-09
Some say it works, but I do not suggest sharing /home.
Programs and settings in /home are designed so you can upgrade, but not really downgrade. So a new version may overwrite settings that old version does not understand.

But I have many Ubuntu installs and share all my data from a data partition. My /home is only 2GB and that is because of .wine with the Windows version of Picasa. Since it is small and easily backed up, I just keep /home inside /. I may copy some settings to a new install but do not always copy all of /home to my new install.

I also move some larger hidden data folders in /home like Firefox & Thunderbird profiles. Then I have the same email & bookmarks in all systems. 

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

   Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

