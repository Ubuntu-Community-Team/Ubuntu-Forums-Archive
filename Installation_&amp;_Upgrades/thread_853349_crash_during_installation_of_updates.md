---
title: "crash during installation of updates"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by groundnut on 2008-07-08
During installation of updates my computer crashed. The files were already downloaded. 
As a result there is no network/internet connection anymore. Also the update-manager is not accessible.

Once I try to start the update-manager or the network I get the following message:

* the configuration could not be loaded
* you are not allowed to access the system configuration

How do I tackle this problem?

kind regards,
Tony

---

### Post by Pumalite on 2008-07-08
If you are IN Ubuntu; run:
sudo dpkg --configure -a

---

### Post by Rohbart on 2008-07-08
It does not work.
I installed Ubuntu today (my first Linux system) and did an upgrade. Afterwards I was not able to start firefox and I had no rights to do anything. I have just formatted my pc because I was going to go mad and reinstalled Ubuntu. 
Does someone know which upgrade caused the problems?
And how can I Backup my system and let it become like before some updates in order to undo some possible mistakes. What I have in mind is something like the windows disaster recovery. I know "Linux is not Windows" but maybe there is such an tool.

---

### Post by Pumalite on 2008-07-08
You might want to try one of these:
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

### Post by Rohbart on 2008-07-08
Thanks for the links but unforunately I do not know which folders are changed by updating applications or Ubuntu. Which one do I have to save before updating Ubuntu?

---

### Post by Pumalite on 2008-07-08
I would save data and /home.

---

### Post by groundnut on 2008-07-08
mant thanks Pumalite,

My problem has been solved. It worked

kind regards,
Tony

---

### Post by Pumalite on 2008-07-08
You are welcome. Good luck!

---

### Post by Rohbart on 2008-07-08
where can I find them? 
I save them on an external hard disc or whatever and if there are problems I just change them with the current one?
Can I do the same before updating an application?

---

### Post by Pumalite on 2008-07-08
If you read the links I gave you; you are going to find a lot of neat ways of saving and restoring your system. You can take a whole picture or partial pictures. /home is hanging from root ('/'). Your data should also be in your /home because it is the folder with most space. Don't forget to also backup 'Hidden Files' in /home.

---

### Post by Rohbart on 2008-07-08
I tried this one: I opened file system and I am now copying all on another hard disc. It is about 3GB. I think this is, if it works the easiest solution. But does it work when I need it or did I forget something?

---

