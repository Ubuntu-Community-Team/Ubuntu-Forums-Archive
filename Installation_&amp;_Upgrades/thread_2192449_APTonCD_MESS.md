---
title: "APTonCD MESS"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2013-12-07
Today, following the instructions ["How to Back Up & Restore Your Installed Ubuntu Packages With APTonCD"]("http://www.howtogeek.com/110034/how-to-back-up-restore-your-installed-ubuntu-packages-with-aptoncd/")

I have re-formatted my drive with ext4 as /sda1 is / and about 20gig, /sda2 is /home and about 360gig and /swap which is 8gig. 

I have re-installed Ubuntu 12.04 LTS (Precise Pangolin) and performed all the updates, restricted drivers)

and

I have tried to use the DVD created with APTonCD to Restore the packages it backed up. It will not "find" the optical drive.

I receive the following after being told to put the DVD in the drive.

E: Unable to stat the mount point /media/cdrom/ - stat (2: No such file or directory)
E: Unable to stat the mount point /media/cdrom/ - stat (2: No such file or directory)
E: Failed to mount the cdrom.

W: Unable to read /etc/apt/sources.list.d/apt.conf.d/ - DirectoryExists (2: No such file or directory)

I then tried following these post about the foregoing stat - mount error.

[http://forums.linuxmint.com/viewtopic.php?f=90&t=122982](http://forums.linuxmint.com/viewtopic.php?f=90&t=122982)

and

[http://www.zyxware.com/articles/2656/solved-how-to-fix-unable-to-stat-the-mount-point-media-cdrom-while-installing-from-ubuntu-repository-cd-dvds](http://www.zyxware.com/articles/2656/solved-how-to-fix-unable-to-stat-the-mount-point-media-cdrom-while-installing-from-ubuntu-repository-cd-dvds)

I added the cd-rom to the fstab, etc etc -- nothing worked. I added and then removed the cd from the Synaptic Repos, trying to get my work together.

I'm at my wits end. I have posted the packages that aptoncd burned to a dvd, [here]("http://paste.ubuntu.com/6538229/").

---

### Post by bashiergui on 2013-12-09
Verify that the DVD you made is good. Is the DVD recognized in other computers? Does your computer mount other DVDs?

---

### Post by codenine75a on 2013-12-09
Some people use the burnable cd in a store drive mode.  This means a user piles up the data on the cd and closes the cd when it is full or they want to distribute it.   I think it was called UDF file format.

---

