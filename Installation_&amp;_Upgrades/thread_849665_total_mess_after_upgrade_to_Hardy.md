---
title: "total mess after upgrade to Hardy"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by monstruil on 2008-07-04
Hi, 

I've upgrade to Hardy on my laptop but after reboot all is a total chaos. I just can access in low graphics mode. I've edit the xorg.conf file a million times but nothing (even with the parameters working for me in old editions). Trying to configure and reconfigure xserver-xorg did'nt work. Gnome just don't start, can't find any screen. 
Now it's even worse, after doing a lot of desperate things I just can't access the console to sudo nothing, all is stopped at: "running local boot scripts....". 

I think he's dying guys... :(

The real problem is that I did'nt backup /home!
I want to do a fresh install but I know /home will be cancelled. My question is if I can perform a fresh install preserving or moving my /home stuff to some safe place :confused:

Please Help, 
Thanks

---

### Post by Pumalite on 2008-07-04
Backup your data and home>
[http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan](http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan)
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
you could try sbackup - in the repos
DAR
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

---

### Post by cespinal on 2008-07-04
there is NO WAY im updating my system...why on earth do i need to reainstall an OS every time it gets updated????? 

im sorry.. but this kinda things really piss me off

---

### Post by louieb on 2008-07-04
Try 
boot to recovery mode
select xfix
select resume normal boot
the above should ge you a GUI it may be alright but if low res then

```
gksudo displayconfig-gtk
```Did not have a problem with my laptop but had to go through the above on a couple of desktops to get my display back to normal.

---

### Post by louieb on 2008-07-04
> **cespinal said:**
> ...why on earth do i need to reinstall an OS every time it gets updated????? ...im sorry.. but this kinda things really piss me off

There has been a lot radical changes in Linux since I started using it a couple of years ago. With change come bugs. This time around the way X get configured is completely different  I run Ubuntu on 4 computers. Only one - my laptop upgraded without a problem.  

I now use partimage to backup before upgrading. I've also partitions my computers so that /home and my data are on separate partitions.  

But if I needed  stable I'd go with some other distro  or still be using Ubuntu 6.06 (Dapper).  
Ubuntu takes as its base Debian unstable. (Down side is some of those stable distros still come with FF 1.5) Not the latest and greatest but it works.

As far as getting your data off to a safe place you can just use a live CD such as Ubuntu or    [Knoppix Linux]("http://www.knoppix.net/")  or  [Puppy Linux]("http://www.puppylinux.com/")  and use the file manager to copy it off to some external drive.

---

### Post by monstruil on 2008-07-05
> As far as getting your data off to a safe place you can just use a live CD such as Ubuntu or Knoppix Linux or Puppy Linux and use the file manager to copy it off to some external drive.

I can't boot in recovery mode so xfix seems not an option. I've abandoned any hope to start server X or find some screens.
I'm trying to use my old 6.06 live cd and copy the old files from the file manager but seems I can't mount my drive. 
Did the other distros will work?
Did a fresh install or live cd of any other distro will permit me to save old data in a safe place or partition?

---

### Post by louieb on 2008-07-05
> **monstruil said:**
> ]...I'm trying to use my old 6.06 live cd and copy the old files from the file manager but seems I can't mount my drive.

Linux has come along way since 6..06. Lots easier to copy with either of the 2 live CD's I mentioned basically in Knoppix just click on the icon for a partition  and it will open the file manager. In Puppy you click on the drives icon. Then you will see a list of partitions just click on one to mount it and it opens  up the file manager.

With the 6.06 CD you have to use the terminal to create a couple of directories one for the source and one for the target.  
Then you use the fdisk -l command to find the /dev/@@@# of the partitions.
 Then you use the mount command to mount the partition on there directory.  Then you can use the file manager to navigate to the directories you made.

Something like this. ( may have to prefix the commands with sudo )
```
mkdir /tocopy
mkdir /copyto
mount -t ext3  /dev/@@@# /tocopy
mount -t <to partition type>  /dev/@@@#  /copyto

```Now you should be able use the file manager to navagate to /tocopy and /copyto. and get your file over.

---

### Post by monstruil on 2008-07-06
thanks louieb, thanks all
I did it with the knoppix live cd, easy as a pie!
:guitar:

---

### Post by bilijoe on 2008-07-06
> **cespinal said:**
> there is NO WAY im updating my system...why on earth do i need to reainstall an OS every time it gets updated????? 

im sorry.. but this kinda things really piss me off You don't _*need*_ to upgrade (reinstall?) an OS every time it gets updated, the point is you _*can*_.  This allows you to take advantages of all the [little] improvements, fixes, additions, added hardware support, etc., etc., etc.  I know lots of people who run Windows 98, because it still does everything they need.  Obviously 'to upgrade, or not to upgrade' is a personal decision, not some kind of requirement or mandate.  It's a choice, which you, and you alone are privileged to be able to make.

---

### Post by monstruil on 2008-07-07
> **bilijoe said:**
> You don't _*need*_ to upgrade (reinstall?) an OS every time it gets updated, the point is you _*can*_.  
Yes, it's your choice. But I think every one of us want an updated computer if the OS gives this chance. Personally, when something is available in the update manager, I run it, I can't resist to it. You always think your computer will be safer, improved, with less bugs more features and stability. But, to be honest, with ubuntu is not like this and I'm not the only observer of this. I love Ubuntu, but why a six month release cycle? Some novice users can get dissapointed with their first look at ubuntu for this. Maybe ubuntu must consider to better advice download of test releases until get a a stable working state.

---

