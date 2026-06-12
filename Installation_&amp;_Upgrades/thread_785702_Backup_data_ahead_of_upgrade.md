---
title: "Backup data ahead of upgrade?"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by mapes12 on 2008-05-07
I'm looking for an idiot proof, step by step guide detailing how to backup all my folders and system settings (e.g. Firefox bookmarks) etc. ahead of doing a fresh install of 8.04. Is it as simple as copying my Places>Home Folder or is there more to it than that?

I've searched the forums but strangely haven't found anything that spells out what I need to do.

---

### Post by tamoneya on 2008-05-07
all of your system settings are contained within /home/username so if you copy that folder to some other harddrive or computer you should be all set.

---

### Post by darc on 2008-05-07
Yeah, if you've got the know-how or the time to figure it out, I'd highly suggest you keep your "system" (root) on one partition and your /home on another.  That way if you ever need to do destructive re-installation, you just overwrite your / with the install, then remount your /home and all's peachy : )

I've been doing that since Slackware 7 (read : A long time ago : ) and haven't lost my data/settings in my home directory yet. 
-darc

---

### Post by mapes12 on 2008-05-07
Thanks.

I can find my Home folder and using Ctl h I can see my hidden folders and files. But I can't find a folder called "Username"?

I'm running 7.10 on an IBM Thinkpad T23.

---

### Post by lswest on 2008-05-07
your homefolder is /home/<your username>/ which is what the above poster meant.  The hidden folders and such hold your settings.

---

### Post by Het Irv on 2008-05-07
Try going up one level. But there is a problem, the location of the trash folder has changed since 7.10.  In Hardy, the trash folder is located in /home/user/.local/share/Trash not /home/user/.Trash

Will this cause problems?

---

### Post by lswest on 2008-05-07
> **Het Irv said:**
> Try going up one level. But there is a problem, the location of the trash folder has changed since 7.10.  In Hardy, the trash folder is located in /home/user/.local/share/Trash not /home/user/.Trash

Will this cause problems?

i assume it will just create the new trash folder.

---

### Post by Lord Landis on 2008-05-07
The best way to backup your data before doing anything else is to connect a USB drive (or other mount point) and then run rsync from the command line.  It can be invoked like such
```
sudo rsync -rpgov /home/*<you>* /*<destination>*
```

Note that you can just use '-av' instead of '-rpgov' and it will do pretty much the same thing.  Just **_MAKE SURE_** you put the source **before** the destination our you will wipe out everything.

Let me stress that again: source *before* destination.  Backups are wonderfully powerful, but they can be one of the most destructive things imaginable if you screw up the syntax.

The benefit to using rsync is that it's fully recursive (the -r option), automatically grabs the hidden folders, and checks the data for integrity as it goes.  The only real downside is that you can't use it to write to a CD/DVD.

Exactly how much data are you backing up?

And I have to second the previous comment - if you have the time to learn how to do it, set up /home on a different partition or physical drive.  It will save you hours of aggravation and stress if you ever need to nuke your system from orbit.

---

### Post by Het Irv on 2008-05-08
If you are not comfortable with command line, you can use QuickStart (see sig for link).  It is a great tool that you can use to backup your just your home, or all of your files.  It also has some great tools to get your system back up and running quickly.  It was build for 7.10, but it also works on 8.04.  If you want to find out more click the link, it will take you to the QuickStart forums.

---

