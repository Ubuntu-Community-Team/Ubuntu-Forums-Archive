---
title: "I think I'm going to upgrade to 9.10.  &quot;back in time&quot; to transfer files, etc???"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by switch10 on 2009-12-07
I think I'm going to upgrade to 9.10 from 8.10.  I use the program "Back in Time" for backing up my stuff.  Specifically the directories I backup are:
/etc
/home
/usr
/var

I want to do a fresh install, not an "upgrade", so I have all of these directories on an external drive.  

My question is how should I actually go about restoring all of this stuff?  Should I use the Back In Time restore option?  should I manually merge the directories with the ones on the 9.10 install?

Thanks for the help,

Dave

---

### Post by phillw on 2009-12-07
> **switch10 said:**
> I think I'm going to upgrade to 9.10 from 8.10.  I use the program "Back in Time" for backing up my stuff.  Specifically the directories I backup are:
/etc
/home
/usr
/var

I want to do a fresh install, not an "upgrade", so I have all of these directories on an external drive.  

My question is how should I actually go about restoring all of this stuff?  Should I use the Back In Time restore option?  should I manually merge the directories with the ones on the 9.10 install?

Thanks for the help,

Dave

Yay, a fellow gateway user :-)

If you are NOT running a LAMP installation, then backing up your ~home will be okay. That will carry your mozilla bookmarks, passwords etc over along with documents, audio, video etc that you have saved on there. You can get a list of all your apps that you have put on, but, it is very likely that the new install will also make available newer versions of your apps. So, I'd only use that to remind you of what you have installed - Not to try and put back on.

I've never used that programme, as i use a command line to do my backups. clonezilla ([http://clonezilla.org/](http://clonezilla.org/)) and pybackpack ([http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html](http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html)) are options. 

If you're familiar with the 'inner workings' of your machine's hard drive partitions, or want to learn - you can do it from the command line - It's entirely upto you.

If you're running a server on your system, then you'd need to back up some more stuff.

make a new user for your new install, and put your ~home back there - if your system is happy, then you know that you can move that area to your usual username's ~home. Or, once you've got it all happy, you can.

Regards,

Phill.

---

