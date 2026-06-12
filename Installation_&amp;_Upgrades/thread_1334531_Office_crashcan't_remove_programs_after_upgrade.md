---
title: "Office crash/can't remove programs after upgrade"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by rmeng on 2009-11-22
Well, my open office began to crash after I've upgraded to Jaunty.
I had some problems with eclipse too. 
Also, I can't completly remove programs for some reason.
When I use the option to remove completely those programs by using synaptic( I was hoping that reinstalling them can fix those problems), I can't get them removed completely. When I reinstall them even the old (bugged) settings are saved. What should I do?
Any advice?

---

### Post by rmeng on 2009-11-22
I think I might be doing something wrong.

Could someone tell me what should I do to remove the program completely?

When I "sudo aptitude purge openoffice.org" (or eclipse) doesn't seem to do the work. 

What should I type if I want not only the configuration removed but the installation files too?

---

### Post by audiomick on 2009-11-22
If I understand things right, Synaptic will always remove program packages, or tell you it can't for some reason.
If you are not able to remove config files, maybe you have to do that by hand. If you go to your home folder and select "show hidden folders" under View, you will see lots of folders that are named .something

I have 2 on my system that indicate a connection with Open Office. One is called .openoffice.org, the other .openoffice.org2

I would not erase them without first making a copy. I would try creating a new folder and moving them there, or changing the name after making careful note of the original, so that the freshly installed Open office can't find them. Your old configuration data should then be gone.

If things go horribly wrong, you should at least be able to get back to where you are now by replacing the files, or changing the name back. If things go right, you can then safely erase the old files

---

### Post by ajgreeny on 2009-11-22
Yes, simply rename the hidden folder in your home called ~/.openoffice as ~/.openofficebackup, then open your openoffice again.

If you use the quickstarter icon in the system tray you will also need to close that down as well or the new OOo folder will not be made or used.  That foxed me completely a long time ago, when I needed to do more or less what you need to do now.

If you have any personal templates setup you will need to copy them from the backup folder to your new one.

---

### Post by rmeng on 2009-11-22
didn't solve the problem.

any other ideas?

---

### Post by Hagar Delest on 2009-11-23
Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) _but don't transfer your personal data_ during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

