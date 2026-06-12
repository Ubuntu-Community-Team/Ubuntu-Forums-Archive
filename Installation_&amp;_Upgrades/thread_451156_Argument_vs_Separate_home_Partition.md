---
title: "Argument vs Separate /home Partition"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by Sand Lee on 2007-05-22
I know a separate /home partition is valuable for backing up data, but the annoying thing about it is that it also backs up various settings. Whether you are using gnome or KDE, you will find many hidden files in your home folder. AFAIK, these files contains settings to certain apps and to how your system interacts with you. 
My point is, copying the data to a flash drive or creating another partition unrelated to the system e.g. "/documents" would be a better idea for the user who aims to keep his files but also wants to upgrade to the latest OS on a clean slate.

This is just my view on this subject. I would really like to hear your views and thoughts.

---

### Post by aysiu on 2007-05-22
I have a separate /documents partition for that very reason. Then I just symlink the settings I *do* want to bring over.

---

### Post by Sand Lee on 2007-05-22
So do you mean that you have a separate /documents partition and you don't have a separate /home partition? And when you reinstall, you copy certain /home settings to /documents and copy those to the new /home? What is symlinking?

---

### Post by aysiu on 2007-05-22
Well, I originally had a separate /home partition until I encountered the problem of lingering settings that I didn't want any more.

So the next time I installed Ubuntu, I mounted the previously separate /home partition as /documents and then symlinked the /documents/.mozilla and /documents/.mozilla-thunderbird folders over to /home/username/.mozilla and /home/username/.mozilla-thunderbird

Symlinks are like shortcuts (in Windows) or aliases (in Mac). They're "fake" files and folders that just point to the real file or folder. So the Firefox settings appear to live in ~/.mozilla but really live in /documents/.mozilla

---

### Post by _simon_ on 2007-05-22
I backup what I want to DVD, seems simpler lol

---

### Post by aysiu on 2007-05-22
I back up to an external hard drive.

But backing up is a separate issue as far as I'm concerned. A separate /documents or /home partition saves you the trouble of copying *back* the backup after reinstallation.

---

### Post by Sand Lee on 2007-05-22
How does it feel to use the /documents partition instead of the /home partition? I imagine it would be a little weird since KDE and GNOME both are "centered" around /home (if you get what i mean).

---

### Post by aysiu on 2007-05-22
Well, as I said before, I symlink in the folders I want to pick and choose to bring in to /home

So I'm still using /home--I'm just not *forced* to use all of my old /home settings.

---

### Post by Sand Lee on 2007-05-22
I'm interested in setting up my hard drive like yours ;). How do I make a symlink? I've tried google to no avail.

---

### Post by aysiu on 2007-05-22
Well, if you're using Nautilus (Ubuntu), you middle-click-drag the folder or file from its original location (for example, /documents/.mozilla) to the place you want it to appear to be (for example, /home/username/.mozilla) and then let go of the mouse button. Then select *link here* from the context menu.

It's a similar process in Konqueror (Kubuntu), except that you right-click-drag the folder or file.

Not sure if it's middle-click-drag or right-click-drag in Thunar (Xubuntu). I haven't symlinked through Thunar lately.

You can also do it through the command-line ```
ln -s /documents/.mozilla ~/.mozilla
```

---

### Post by Sand Lee on 2007-05-22
so making a symlinks is basically the same as making a link in windows?

---

### Post by aysiu on 2007-05-22
> **Sand Lee said:**
> so making a symlinks is basically the same as making a link in windows?
Linux: symlink
Windows: shortcut
Mac: alias

Yes a symlink is the same as a Windows shortcut or link.

---

### Post by rwood on 2007-06-04
"a easy way to keep your/home partition the way you want it"
what i do is move all the stuff i dont want or need anymore to trash bin.
then install new system.

---

### Post by Sand Lee on 2007-06-06
that sounds like a good idea but, doesn't the system regenerate some files after you delete them? or is that an event that takes place after logging in?

---

### Post by malspa on 2007-06-06
Excellent idea on how to use the links.  I have a separate /home partition, but I also have another /home2 partition where I keep all of my documents.  I bookmarked the /home2 partition in Konqueror for easy access.  But using a symlink is just as well.

It's supposed to make it much easier for reinstalling if you have /home on a separate partition, but some distros can preserve /home even it's on the same partition as /.  Or so I hear.  Having the rest of your stuff on a /home2 partition just saves time.  Also nice if you have other distros installed.

---

### Post by EndPerform on 2007-06-06
I have the partitions separate, however, I'm also syncing certain paths between my desktop and laptop.  What this lets me do is make sure the important stuff is mirrored, and if I need to reinstall I can... and if the old settings become an issue, I wipe the /home partition and re-sync from the desktop when I'm ready.  It works pretty well.  

Another alternative I had thought about was writing a script that I'd execute prior to reinstalling which would wipe all settings directories so things would be fresh.

---

### Post by Sand Lee on 2007-06-15
After reading all the posts, I have come to the conclusion that the most effective scheme - well for me anyways - is having a /storage partition and a small /home partition as well. The /storage partition would contain all of my files and the smaller home partition would contain all of my settings (1-2GB). This setup is the most effective because if something ever happens to your system and you want to recover it, you could just reinstall and have all your settings. If you want to upgrade your system, you could just format the home partition on installation. I'll give this a try as soon as 7.10 comes out :p

---

