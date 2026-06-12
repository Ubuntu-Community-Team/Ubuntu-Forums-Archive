---
title: "Home folder polluted - What to SAVE when Upgrading OS"
date: 2019-06-04
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2019-06-04
In your Help Thread under Installation & Upgrade, under #8 you state;

> **mörgæs said:**
> 

**8 - User files**

Beware that some program pollute /home with a lot of (often hidden)  garbage files which do not serve any purpose and only take up space.  Because of this I recommend to copy only select files into the new /home  and not the entire folder.


I'm using UbuntuStudio v16.04, and wish to again attempt upgrade to   v18.04. What are the "select files" you suggest to be copied over to the   new /home directory? As I have backed up all of that dir.  

Thanks!
Rick ):P

---

### Post by SeijiSensei on 2019-06-04
Modern drives are really large. I just copy everything.

If you want to start with a clean profile, create another user.

---

### Post by kpatz on 2019-06-04
You could create a save folder under your home and then move everything there.  Then if you find you need something back, just move it back.  And in 6 months or so, if you like, just delete the save folder which will only have the junk you haven't needed.  Or just keep it.  I think I have save folders under my home from the past 12 years worth of upgrades and reinstalls.

---

### Post by Rick St. George on 2019-09-13
Thought I had closed this Thread. Before I do ... Wish to Add the following for Reference to all who find this Thread!
I found the following and included it as an Exclude List when doing my backups using Rsync. [https://github.com/rubo77/rsync-homedir-excludes](https://github.com/rubo77/rsync-homedir-excludes) 
Follow intructions there to customize your Exclude List / File.

Here is my syntax for my Backups, of Home Dir., using Rsync.

```

  	 	 	 	   [FONT=Times New Roman, serif]
sudo rsync -av --delete --[/FONT][FONT=Times New Roman, serif]exclude-from=/var/tmp/ignorelist /home/stephen/ /media/stephen/BU-Drive/Backups/[/FONT]

  

```

This will Backup Home / User to another HDD (using KingWin Power Switcher for several SDD/HDD) I turn on and use ONLY for Backups.
I do this Weekly, and this way I have ready Non-Compressed files to simply Copy & Paste. After the First BU, the following times go quick! As it will only copy incrementally what files have changed, or new files. This makes it extremely easy and quick. I will also copy my VM Data to the BU drive.

I will then do a complete BU with ACRONIS at Month End... just in case, to an External BU Drive (2 TB MyPassport).
Is this redundant? Maybe! But I learned back in the 80's to ALWAYS have a BU. As an author and trader - My Data files are critical.

Hope this Helps!

---

### Post by ajgreeny on 2019-09-13
**You** are not able to close a thread, not even one you started; that is something that only forum staff can do, though the forum software itself will close a thread after twelve months of inactivity.

However, once your problem has been solved please mark the thread as **SOLVED** from the Thread Tools menu up-top.
It is a great help to other users searching the forum.

---

