---
title: "How to restore /home from backup? How to copy ALL files?"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by Elzigzag on 2010-01-11
Hi guys! I was testing how to separate my /home folder putting it in a different partition. Well I made a backup, a Live DVD backup. There I can see my /home folder, with all my precious personal settings. But when I try to install from Live DVD something happens and graphical problems pop up, and _I've finally decided to quit re-installing from that Live DVD backup. _
I've made a clean installation, with a separate partition for /home. And I'd like to copy all my /home folder from that malicious Live DVD. So I've thinking to load the disc and just copy the folder from it to its final destination. But I've been told that when you "just copy" not every file is really copied, some of them are skipped for many different obscure (to me) reasons. So MY QUESTION IS: **How to copy ALL /home files backed up to my newly-created /home partition?** (In case there were many ways, I prefer GUI, you know, the graphical way)

I hope I was clear enough.

---

### Post by J V on 2010-01-11
open it up, press ctrl h so its showing the hidden ones, and copy and paste...

---

### Post by SecretCode on 2010-01-11
How did you make the backup? Is "Live DVD" a method of backup (I'm not familiar with it)?

---

### Post by Elzigzag on 2010-01-11
> **J V said:**
> open it up, press ctrl h so its showing the hidden ones, and copy and paste...

Well, that's easy. But I've been told that still some files/links are skipped. May be I should give a try.


> **SecretCode said:**
> How did you make the backup? Is "Live DVD" a method of backup (I'm not familiar with it)?

Sorry didn't mention it. I made the backup with Remastersys > option > Backup. The Live DVD runs fine, I can see there all my /home folder settings. But my intention is to **copy each and everyone of all the files to the newly created /home partition**. I guess it shouldn't be too difficult. Hope so. ;)

---

### Post by darkod on 2010-01-11
For copying the files, what JV suggested would work fine. It will allow to copy all files including hidden.
But I've never tried that before (never needed it), and I'm not sure if the permissions of the files will be OK and working OK. And that's the most important thing in linux, with wrong file permissions that file is useless.

---

### Post by Elzigzag on 2010-01-11
> **darkod said:**
> For copying the files, what JV suggested would work fine. It will allow to copy all files including hidden.... I'm not sure if the permissions of the files will be OK and working OK. And that's the most important thing in linux, with wrong file permissions that file is useless.
That's my constant source of worry.
That's why I'm looking for a a secure method for copying ALL. My new installation was configured pretty much the same, the same user, the same password, the only difference being that of the /home folder in a different partition.

**Has anyone managed to copy'em all?**

---

### Post by SecretCode on 2010-01-11
I would suggest booting a live CD, so that you can be sure no files in /home are currently in use. Then copy again.

If you can bear to go the command line, cp with the -a parameter should give good results. Assuming your backup is on /media/cdrom and your hard disk installation is at /media/sda1:
```
sudo cp -ar /media/cdrom/home/ /media/sda1/home/
```

---

### Post by Elzigzag on 2010-01-11
> **J V said:**
> open it up, press ctrl h so its showing the hidden ones, and copy and paste...
Hey, friends. Well, well, well. It seems that J V was COMPLETELY right. Sorry for being that complicated. But I showed hidden files, and then did a nasty copy & paste, and it worked!!!! Can you believe it!
All my firefox extensions, and passwords, seem to be there. I'm so happy!

I must go on checking, but it somehow worked!
Thanks a lot JV, Secret Code and darkod. I guess this thread should be turned [SOLVED].

---

### Post by Elzigzag on 2010-01-12
> **SecretCode said:**
> I would suggest booting a live CD, so that you can be sure no files in /home are currently in use. Then copy again.

If you can bear to go the command line, cp with the -a parameter should give good results. Assuming your backup is on /media/cdrom and your hard disk installation is at /media/sda1:
```
sudo cp -ar /media/cdrom/home/ /media/sda1/home/
```

Sorry, I forgot to mention that I did all this booting from a Live DVD just as SecretCode told me. I booted from the very Backup Live DVD. 

All my settings were restored, but I had to re-install some apps, Google Earth, VLC, and so on. But after installation when I launched, let's say Google Earth, all my personal places were just there. Fine, just what I was looking for.
:popcorn:

---

