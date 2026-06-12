---
title: "Hardware RAID not accessible post reinstall"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by shimmip on 2010-08-16
I have a hardware RAID (3ware 9500S) on a dedicated file server running Ubuntu server 10.04. This has been working excellently, but for some reason I decided to reinstall the OS. Don't ask me why, but I'd actually done this before and had no issues at all - the RAID array showed up fine again afterwards that time.
 
This time, i really wish I hadn't done it because something strange is happening. The 2 partitions on the RAID are both showing up as ext4 partitions during the install, and I set them up to mount as /srv and /backup as I did during the initial install and the last reinstall.
 
This time around, when I try to access the /srv directory (using sudo cd /srv) it tells me that permission is denied. Same with /backup. I have a dual boot on the machine with a desktop version of Ubuntu 10.04, so I thought I'd boot that up and see what that looked like. That can also "see" the drives and reports the free space on them accurately, but when I open the /srv drive I see nothing and when I try to create a directory, I get "Permission denied".
 
I'm not very linux experienced, so just about the only thing I could think to try was a chmod 666 on the directories just in case, but no joy. 
 
Does anyone have any suggestions? My family photos and vids are on the drive and I REALLY need to get access to it again for the sake of marital harmony!
 
Thanks
 
Phil

---

### Post by shimmip on 2010-08-25
I have no idea why it worked when I did it again, but a chmod seems to have sorted this out now. This time I tried 

chmod -R 0777 /srv

and it just worked, thank goodness. I know 0777 is going to open things up quite a bit, but it's a family fileserver and I WILL be taking backups from now, so I don't care.

Phil

---

