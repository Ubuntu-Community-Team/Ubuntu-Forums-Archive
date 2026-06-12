---
title: "Copying to a new partition"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by nflp1999 on 2007-03-02
Strange question.  I have Ubuntu almost exactly the way I want to start with.  It has all the various packages and such I need all installed and I can do most of what I want to (watch DVDs, listen to music, ect).  Now I want to try a few things but don't want to mess up what I already have done.  So, can I copy my entire linux setup to another partition so I can mess with partition 2 and leave partition 1 undisturbed?  I don't want to to through the headache of installing the whole thing over again and have to track down all the pieces I need.  If I could just copy what I have to another partition then I would have a really good starting point.  I read about partimage but I didn't know if that would work or if there was another way?
Thanks.

---

### Post by nereid on 2007-03-03
Just zip the whole root partition and move the zipped (or otherwise compressed file) to the other harddrive. To revert the whole process, unzip this file on the target drive and run *grub-install* to get a working GRUB boot manager.

---

### Post by warjowuch on 2007-03-03
Partimage should do the job, but has disadvantages, like the destined partition should at least be as big as your original partition, as it 'images' the original partition. While linux can also be copied and pasted to another partition, this needs severe knowledge about how to do this. It's not just cntrl c and cntrl v... So, I think partimage should work.

I use sbackup (from automatix, the simple backup solution or something) to do backups. But default is has too little parameters on what to backup, and it hasn't got any indication as how far the process is in its progress.

But it might work if you configure it like this:
include: /var /etc /boot /home /bin /sbin /usr and /lib
exclude: /proc /tmp /dev /var/cache /var/tmp /sys
And select your destination. But know it's not a copy and pastejob, as it saves the backup in an archive. But you might restore the backup with a livecd to the desired partition... And don't forget to select 'manual backups' when you start the thing, when you like to do it manual of course... :-)
Good luck!

---

### Post by warjowuch on 2007-03-03
@nereid, are you sure, have you tested this??

Because when I read this it is different... but maybe zip does a better job (allthough I really doubt it)
[http://www.halfgaar.net/backing-up-unix](http://www.halfgaar.net/backing-up-unix)

---

### Post by nereid on 2007-03-03
@warjowuch
My post was the crude and dirty version on how to do it. The reference you're mentioning is far better. And yes, the dirty version works, I've tested this already. You could use every other compression application, like rar, tar (with gzip or bzip2) or any other tool around. I just mentioned zip, because most people know what I mean if I talk about zipping instead of creating a tarball or something like that ;)

---

### Post by nflp1999 on 2007-03-03
Is there a way I could install a fresh copy of Ubuntu then copy over my settings?  All the various things I've downloaded and such so instead of copying the OS and such, I'm just copying my enhancements I've made?  I want to put Kubuntu on my other partition so I'm wondering if I should install a fresh copy of Kubuntu on the partition but then I'm back to my original problem of having to download everything to get it all working again.  After three days of messing with this stuff, it doesn't fill me with glee to think I have to do it all again.  
   Also, on the topic of backups, what should I run to do the standard disaster recovery backup?  I have an external drive that I use for my Windows XP backups.  I'm thinking that should work for this too since it's so large.  What is "best practice" for weekly backups in Linux?

---

### Post by nereid on 2007-03-03
You can save the packages which you have downloaded already, they reside in /var/cache/apt/archives/. Your config settings reside in your home directory. Create a backup of your home folder and copy it to the new location.

---

### Post by louieb on 2007-03-03
Look at the backup and restore threads in the howto section. with the right flags set tar can copy permissions, symbolic links and ownership creating an exact copy for you to play with. 
By doing it this way or with partimage, about the only thing you will have to tweak by hand are the files /etc/fstab and /boot/grub/menu.lst. They have to be tweaked to reflect that the / (root file system) is now on a different partition.

---

### Post by nflp1999 on 2007-03-04
OK.  Thanks for all the info.  I'll start poking around. :)

---

