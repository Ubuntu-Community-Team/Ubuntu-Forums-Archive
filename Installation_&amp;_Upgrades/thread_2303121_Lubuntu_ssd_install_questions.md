---
title: "Lubuntu ssd install questions"
date: 2015-11-16
forum: Installation &amp; Upgrades
---

### Post by robinvdberg21 on 2015-11-16
hey guys,

I'm a linux (lubuntu) newbie and have some questions.

I'm currently running windows 7 on my laptop. I've just bought a ssd (sandisk ultra 2 250gb). 
I'm planning to install lubuntu on this ssd. 

I have the following questions: 

1. The newest lubuntu V is 15.10. I'd like to install this version. when the next lts releases can I simply upgrade then? or do I need to backup all my files and do a complete reinstall? I don't want to go through the hassle of reistalling all my programs. 
In this case I will stick with the lts version so I won't have to do that for a while. I think u can simply upgrade now correct?

2. During the install do I need to allocate a few Gigs as free space? I read something online that this would help the ssd performance. But I don't know if this is still required.

3. Will trim be enabled by default or do I need to set it up after the install?

thanks a ton guys! :)

---

### Post by oldfred on 2015-11-16
You can upgrade.

But, you should always be backing up anyway.
My backup is so I can easily do a new install and restore all my data & programs easily. I typically put new install on same drive and relink to may data partition(s). And reinstall all applications from a backup list of installed apps.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

My new SSD is 125GB, but I do not know what to do with all the space. My normal install is to a 25GB / (root) partition and I have two root partitions on my SSD. But have all data on my HDD linked back to SSD. I do copy come most critical data from one drive to the other, but mostly backup to DVD and flash drives.

Some models of SSD will auto run the trim command. But I was not sure it was working with my model, so I added my own script which adds a log file to show it at least ran.
I do have unallocated space and change fstab setting to noatime.

 Make sure BIOS is in AHCI mode for TRIM to work.

 [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

    My daily script is a copy of this:
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

---

### Post by robinvdberg21 on 2015-11-16
Thanks a lot for your reply! Great to hear u can simply upgrade to the next version.

All the partition/back-up stuff goes above my skill level :P I will simply back-up the files/pictures to a external hdd when I upgrade.

I've read your links. Can I just start the install, create 1 big partition of around 110gb, and then leave the few gb left over as unallocated space? I think that will work right.
I won't create multiple partitions to complicated tbh ;P The trim tweaks from your article I will def apply!

thanks a lot man

---

### Post by yancek on 2015-11-16
If you have 110 GB of unallocated space on the drive you want to use for Lubuntu, use most of it for the root (/) partition and the last few GB for swap.  Best to use the manual install method referred to as "Something Else" in Ubuntu as you will be able to have some control over the installation and make these selections.  I'd also suggest that if you haven't installed and Linux system before, that you read through the tutorial at the link below.  Pay special attention to the Step by Step further down on the page.  The first part of the tutorial has a lot of very useful information on using Linux.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by robinvdberg21 on 2015-11-17
Thanks a lot for your reply, will be installing tomorrow so let's hope it works out, and thanks for the link!

---

