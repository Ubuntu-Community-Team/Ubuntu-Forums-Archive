---
title: "Installing Desktop over current server edition"
date: 2015-01-05
forum: Installation &amp; Upgrades
---

### Post by Jesse_Turner on 2015-01-05
I currently have Ubuntu 14.04 server installed in a 3 disk RAID5.  I went to add the GUI on this system and after restart the system said The disk drive for /var is not ready yet or not present. After telling it to skip mounting, and other files started to load it looks like the GUI was installed in the /var directory for some reason.  See below for how my RAID5 is set up so maybe someone can tell me what I did wrong.  My ultimate goal is to have the system (server, GUI, Applications) installed on one partition, and the users files will go to the /var (sub directories to follow) directory. Sorry for the crappy picture.   Thank you for any help!

RAID 5 with 3  2TB HDDs installed on a server

[ATTACH=CONFIG]259024[/ATTACH]

---

### Post by mastablasta on 2015-01-06
RAID5? why? > In August 2012, Dell posted an advisory against the use of RAID 5 in any configuration and of RAID 50 with "Class 2 7200 RPM drives of 1 TB and higher capacity" for business-critical data. then again it's your data and your PC/server.

why not have user's data in data? why not keeps the OS sepratelly from the data?

ok back to your issue. what GUI did you add? how did you add it? what command was used?

by default user's files and settings are in /home and i am not Quite sure why you would push them into var. if oyu really need them there you can always do a link.

why do you think GUI was installed in the /var directory?

---

### Post by Jesse_Turner on 2015-01-06
Thank you for your reply.  To answer your questions.  I am just learning so any suggestions are greatly accepted.  RAID5 was what is on other servers we have so I just stuck with that RAID.  What RAID do you suggest? This server only has room for 3 drives.

I am setting up this server as a server for installing and using Owncloud only and based on my virtual installations, owncloud installs in the var/www/owncloud directory and all user data is stored in /var/www/owncloud/data.  

Keeping the OS separately from the user data is  what I want to accomplish so that the 3.7 TB partition is for user data only.  Again I am new so I do not know if I am answering your questions correctly.

I added the 14.04.1 GUI  by sudo apt-get install ubuntu-desktop.   Once the computer restarted it was telling me that the /var was not mounted and after pressing S to skip the terminal was showing what looked to be the GUI files not being found (it was going fast so I am not sure what all was not loading) but it all was referring the /var directory.

I hope this answer were what you needed and again, thank you for any help.

---

