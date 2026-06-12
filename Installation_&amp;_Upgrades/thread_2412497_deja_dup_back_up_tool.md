---
title: "deja dup back up tool"
date: 2019-02-13
forum: Installation &amp; Upgrades
---

### Post by mikealte2468 on 2019-02-13
About a week ago I posted this topic but I am experiencing additional issues.

After working out the problem, I suffered a crash and wound up reinstalling Ubuntu 18.04. Went back to the suggestion by TheFu. The 1st part worked - [FONT=arial]"sudo apt update && sudo apt upgrade" but the 2nd step failed. I am including a screenshot showing the terminal and the result of searching for python-gl.

Any suggestions would be appreciated.
[/FONT]

---

### Post by deadflowr on 2019-02-13
It's gi (small case letter I) and not small case letter L.

Edit: Also the software store doesn't show "technical packages".
It shows graphical  desktop applications (mostly), so things like this won't ever show up in it.
For a graphical package manager application that will show all packages including technical packages install synaptic package manager.
(that CAN be found and installed from the software store)

---

### Post by mikealte2468 on 2019-02-14
I admit that I am learning and sometimes my eyes play tricks on me.

I installed synaptic package manager and it showed that python-gi is installed.

Tried to run and it failed - please see screenshot.

What does it mean?

---

### Post by deadflowr on 2019-02-14
This seems similar:
[https://ubuntu-mate.community/t/solved-dejadup-not-backing-up-ascii-error/17099]("https://ubuntu-mate.community/t/solved-dejadup-not-backing-up-ascii-error/17099")

---

### Post by mikealte2468 on 2019-02-17
I have tried several things so I can perform a backup to a 1 TB external USB2 drive. The drive has about 600 GB free.

Looked into chmod as suggested in a 'bug' post (referred by deadflowr) but that doesn't seem to work for me. 

No personal files have been transferred yet including profiles for TB and FF.

Any straight forward suggestions would appreciated.

---

### Post by deadflowr on 2019-02-17
If deja-dup is causing too much stress you might as well try another backup utility,
Look here for suggestions: [https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")
Two I can think of off the top are Back in Time and one called Lucky backup.
Both are in the Ubuntu Software repositories.

Not a fix, unfortunately, but at least you should be able to get backups going.

---

### Post by mastablasta on 2019-02-19
Lukcy backup failed to do a backup in my case and i wasn't alone.

i switched to Areca, but another one that has a nice GUI is Duplicati.

---

### Post by mikealte2468 on 2019-02-19
Thanks for the replies. I'm going to try clonezilla ([https://clonezilla.org/](https://clonezilla.org/)) over the next few days as time permits. It seems similar to another tool I used in the past but no longer supported 'REDO' [https://distrowatch.com/table.php?distribution=redo](https://distrowatch.com/table.php?distribution=redo)

Mike

---

### Post by mastablasta on 2019-02-20
clonezilla backs up the whole drive (image). it is a "manual" process

yes, redo is unfortunately not longer developed and probably does not work on new UEFI systems. it was a very nice OS with best GUI for disk backup.

---

### Post by jlh_uif on 2019-04-24
I have a small branch on this thread... If I may? I'm on Lubuntu 18.04 LTS i386 32bit. When I Iaunch app, it asks me to authenticate to my G-Drive. Then it changes to BLANK page. Never gets to Google AUTH. Ideas? Have current release of "DDup". Suggestions? :(

---

### Post by btr66 on 2019-05-23
Having problems with Deja-dup.

I've removed and re-installed it.

Error o/p

```


Traceback (innermost last):
* File "/snap/deja-dup/172/bin/duplicity", line 1581, in <module>
*** with_tempdir(main)
* File "/snap/deja-dup/172/bin/duplicity", line 1567, in with_tempdir
*** fn()
* File "/snap/deja-dup/172/bin/duplicity", line 1419, in main
*** do_backup(action)
* File "/snap/deja-dup/172/bin/duplicity", line 1537, in do_backup
*** full_backup(col_stats)
* File "/snap/deja-dup/172/bin/duplicity", line 577, in full_backup
*** globals.backend)
* File "/snap/deja-dup/172/bin/duplicity", line 459, in write_multivol
*** (tdp, dest_filename, vol_num)))
* File "/snap/deja-dup/172/lib/python2.7/site-packages/duplicity/asyncscheduler.py", line 146, in schedule_task
*** return self.__run_synchronously(fn, params)
* File "/snap/deja-dup/172/lib/python2.7/site-packages/duplicity/asyncscheduler.py", line 172, in __run_synchronously
*** ret = fn(*params)
* File "/snap/deja-dup/172/bin/duplicity", line 458, in <lambda>
*** vol_num: put(tdp, dest_filename, vol_num),
* File "/snap/deja-dup/172/bin/duplicity", line 347, in put
*** backend.put(tdp, dest_filename)
* File "/snap/deja-dup/172/lib/python2.7/site-packages/duplicity/backend.py", line 395, in inner_retry
*** % (n, e.__class__.__name__, util.uexc(e)))
* File "/snap/deja-dup/172/lib/python2.7/site-packages/duplicity/util.py", line 79, in uexc
*** return ufn(unicode(e).encode('utf-8'))
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 37: ordinal not in range(128)


```
I saw the ref to the post on the Ubuntu Mate forum, but I don't think it's a permissions issue as I am writing to an external USB drive.

---

### Post by scpatl4now on 2019-05-23
I have always used Timeshift for my backups.  Its easy to set up, and it runs in the background so you dont have to worry about it.  I use that for all the system files.  I back up my Home folder using Grsync (has gui).
I've never liked deja dup...

[https://itsfoss.com/backup-restore-linux-timeshift/](https://itsfoss.com/backup-restore-linux-timeshift/)

[https://www.youtube.com/watch?v=6nOojLe_CI0](https://www.youtube.com/watch?v=6nOojLe_CI0)
(video is for Grsync)

---

### Post by btr66 on 2019-05-24
Thanks, I'll try that. 

It seems it may be a permissions issue. I did a test by backing up one folder with my backup destination set as my desktop. It worked.

---

### Post by kurt18947 on 2019-05-24
> **deadflowr said:**
> If deja-dup is causing too much stress you might as well try another backup utility,
Look here for suggestions: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
Two I can think of off the top are Back in Time and one called Lucky backup.
Both are in the Ubuntu Software repositories.

Not a fix, unfortunately, but at least you should be able to get backups going.

I use Lucky Backup to sync folders, it works for that. I'm not sure it's intended for system backup, perhaps it is dunno. I'd probably use an app intended for that purpose. I've tried Deja Dup with poor results as well, perhaps I didn't know what I was doing. What I have done with smaller partitions (<100GB) is to use gnome-disks to copy/paste a partition.

---

### Post by Mark_in_Hollywood on 2019-06-02
When Ubuntu's developers changed the Unity desktop back to Gnome in 18.04, after I ran my deja-dup restore, Gourmet Recipe Manager fails. I want to do a clean install of 18.04, but don't want to restore from deja-dup. I'm only backing up /home. How can I determine if there are incompatibalites?

---

### Post by #&amp;thj^% on 2019-06-02
Just in case >> install duplicity before the files can be restored.
```

sudo apt install duplicity
```

---

