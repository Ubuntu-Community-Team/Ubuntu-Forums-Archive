---
title: "Firefox dead after 9.04 to 9.10 upgrade"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by dbruce100 on 2010-01-07
Did an upgrade today from 9.04 to 9.10.  As far as I can tell, everything is working, with the exception of Firefox 3.5.6 with new install.  I've attempted an uninstall and install.  Tried the following with 3.5.6:

[http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/](http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/)

I finally found that if I use sudo (or gksudo) I can run firefox at the command prompt.  Any other time I run it, it just shows an icon on the lower bar and then it disappears, but within the system monitor it shows firefox......and will show as many as you run the icon with.

I've deleted the entire .mozilla directory, and manually removed all the firefox info fro /usr/bin also before a reinstall.  I assume it is either a strange permission issue or some link related issue.  

"which firefox" shows:  /usr/bin/firefox and the 3.5.6 files are located /usr/lib/firefox-3.5.6 .  Any help would be great, I'm at a loss at this point.  I'm sure it's something simple, but it's a royal PITA.

I have nxserver on the machine, if that means anything and there was a session locally as well as one remote during the upgrade (using the same account).

---

### Post by dbruce100 on 2010-01-08
3.5.7 update came down automatically today, same problem.

---

### Post by dbruce100 on 2010-01-08
For more fun, gksudo nautilus stopped working. Works fine as a standard user.  When run from a command line, I receive the following:

> dbruce@dbruce-desktop:/tmp$ gksudo nautilus


(nautilus:29781): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:29781): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by dbruce100 on 2010-01-08
Anyone have a clue; getting ready to just roll back to 9.04 (it's a Vbox install) and worry about it another day?

---

### Post by jsonder on 2010-01-08
I see a similar problem with the 9.10 Firefox updating on a Fresh installation of 9.10, BUT, probably because of minefield (Firefox 3.7a1pre.en-US) when Synaptic is updating the "installed" programs.

I can't remember trying the default firefox before installing minefield, so I can't verify that "other software" {even Mozilla's own software} screws up the Ubuntu repository update of Firefox 3.5, but it seems likely.

I have minefield installed in my /home/user/ directory, so I assumed the problem was somewhere in the .mozilla, but the person with the original enquiry had deleted that after (I am assuming after) his 9.04-->9.10 upgrade.  Maybe if it had been unistalled before the upgrade (all I need to save is the bookmarks file when doing this).  Below is the error statement:

[img]http://members.cox.net/jsonder67/error.png[/img]

---

### Post by dbruce100 on 2010-01-08
> **jsonder said:**
> I see a similar problem with the 9.10 Firefox updating on a Fresh installation of 9.10, BUT, probably because of minefield (Firefox 3.7a1pre.en-US) when Synaptic is updating the "installed" programs.

I can't remember trying the default firefox before installing minefield, so I can't verify that "other software" {even Mozilla's own software} screws up the Ubuntu repository update of Firefox 3.5, but it seems likely.

I have minefield installed in my /home/user/ directory, so I assumed the problem was somewhere in the .mozilla, but the person with the original enquiry had deleted that after (I am assuming after) his 9.04-->9.10 upgrade.  Maybe if it had been unistalled before the upgrade (all I need to save is the bookmarks file when doing this).  Below is the error statement:



.mozilla was deleted after the upgrade with no change.  The only thing I haven't tried is creating a new test user and seeing what happens. I can then move over the items I need.....but I'm not going to get my hopes up.

My wifes laptop upgraded perfectly with no issues.  I've installed a few packages on this Vbox image pre-upgrade, but  nothing related to firefox.  Opera is what I am using to browse at the moment, and all seems fine.

---

