---
title: "How to actually use sbackup to reinstall a system."
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by shoki on 2006-08-01
Hello All,
****Adamkane has recommend sbackup. I'd like to use sbackup to do a full back up. Then restore my install from the back up I made with sback up.

The reason is I'd like to have a base install with back up. A custom working back up and then an experimental back up. Then I can swap them in and out as needed.

Other than hearing how it's a great tool I have never seen an example of how to use it.

1)back up system
2)reformat drive or wipe directories
3)restore from back up = system restored and running as it was in step 1.

I want to start tweaking my system but not untill I know I can restore it myself.

Getting ready to bust out the old Ghost disks :cry:

Thank you,
--Shoki

---

### Post by adamkane on 2006-08-01
Do you have it installed?

sbackup is available through Automatix or from sourceforge.net.

---

### Post by shoki on 2006-08-01
Yes I have installed it. I also understand it's operation in theory. Does anybody actually have experience backing up and **then restoring a system in its entirety**?

I keep very little data on my computer. It's about getting all my drivers working and checking out all the cool software. Once I install what I consider a perfect suite of applications and have everything working... sound, printer, microphone, videocard, tv out, pod-catching software, bookmarks, extensions, etc. I want to capture a image so that if I totally screw something up I** can reinstall the image** and continue building the perfect install for myself.

I have botched things up many times to the point where I "feel" the need to reinstall. So backing up my music collection and then restoring it would be easy. (I don't keep any music on my system by the way) But being able to reformat the drive and **then restoring a fully functioning** (all my programs and their settings etc) **system** would be a god send.

So far I have been recommended to use tar, sbackup, rsync, grsync, mondo, partimage, rdiff, g4l, and others. But no information on **how to actually restore a system from scratch**. If there is a how-to guide that works for ubuntu 6.06 I would happily test it over and over till it works.

Mondo seemed like it had the most promise but I could not get it to work with my DVD drive...

I want to do it with free Linux software if at all possible but I can understand why somebody would buy turbo-backup or whatever it is called for 50 bucks and just be through with it.

Anyway if anybody has some ideas I will be watching and searching the forums.

Thank you very much,
--Shoki

---

### Post by shoki on 2006-08-03
Well Ghost 2003 did the trick. Kind of lame I know, but until I can find a solid how-to on using tar or sbackup for a complete restore this will have to do.

If anybody can point one out that would be great. But no problem... since i have a ghost image of the drive I can experiment with the other backup and restore options.

Thank you,
--Shoki

---

### Post by orb9220 on 2006-08-03
Howto: Backup and restore your system!

[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

---

### Post by DamonChyld on 2008-03-04
[QUOTE1] 
1)back up system
2)reformat drive or wipe directories
3)restore from back up = system restored and running as it was in step
[/QUOTE]

I am also interested in discovering the best way to do this. In my week of ubuntu experience I have had to reload a few times after adding a package and breaking something even after removing the offending package ;) I would love to be able to just back up a step!!

I have looked at the
Howto: Backup and restore your system ([http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)) thread but am more comfortable using a GUI than the command line and I like the additional functionality built in to sbackup (like scheduled backups). 

What directories should I include (and exclude) in order to best accomplish this and is there anything else I need to watch out for (a few pages found through google-searching mentioned that permissions may be reset but I could not find more on this). 

Thanks y'all!

---

