---
title: "MythTV Help!"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by vdub1980 on 2012-04-23
Hi all, I'm new to the forum and linux/Myth tv and I'm having nightmares with this
 
The whole story is this. One of our IT guys has left and the day after  he went our MythTV server died so I've got the task of rebuilding it.  Luckily he had taken a backup of the old system the day before he went ,  so I just need to basically re-import everything. There's me thinking  this will be simple, but it's been a real headache.
 
I've installed Ubuntu 11.10 and MythTV .025. It's up and running, the  capture card is working fine but obviously there are no recordings there  yet.
 
I want to backup the new install DB before I start messing with it so I  don't have to re-install everything if I mess it up as it's taken me  days to get this far. 
 
I've run the mythconverg_backup.pl and is says "mythconverg_backup.pl: command not found"
 
I could really use some advice as I'm new to all this and there is a  certain pressure to get it up and running asap before the complaints  start coming my way!
 
Thanks for listening!

---

### Post by andrewc6l on 2012-04-25
Here's the official MythTV page for backup/restore:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

You can download mythconverg_backup.pl and mythconverg_restore.pl from there. (Follow the instructions to do the chmod - if you're on Ubuntu you'll probably have to put sudo in front of the chmod to have it work.)

---

### Post by vdub1980 on 2012-04-26
Morning and thanks for the reply

I'm sorry I should have updated this earlier.

I'm past that point now but am struggling to get the mythweb up and running.

When I surf to I.P/mythweb it displays the contents of the folder?

On the old server there was one mythweb file in /var/www folder which i've copied over to the new server. However when i surf to the location it seems to copy a load of files and folders in the www folder? This is the content that is displayed in the browser

---

