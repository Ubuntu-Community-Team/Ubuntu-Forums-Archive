---
title: "Users and groups menu item missing"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by PMB2011 on 2011-01-23
Hi, I'm new to this forum.  I've just installed Maverick (server) in a VirtualBox, and the 'Users and Groups' item is missing from the System/Administration menu when logged in with the first account created.

I've tried 
 - giving root a password and logging in as that - the item still doesn't show
 - adding a new menu item for 'user-admin' (which I believe is the name of the underlying application). Gives "Failed to execute child process 'user-admin' (No such file or directory)"

How can I fix this issue? Where should user-admin be - maybe I need to add the path?

Many thanks
Peter

---

### Post by kansasnoob on 2011-01-23
I've never installed the server edition but try System > Preferences > Main Menu. Then look in that Window under System > Administration > Users & Groups to be sure it's checked.

---

### Post by PMB2011 on 2011-01-23
Thanks for the suggestion but it didn't appear in the Preferences/MainMenu list at all (checked or unchecked) prior to me adding it manually...

---

### Post by Rubi1200 on 2011-01-23
I don't know how relevant this is, but there is some information here:
[http://ubuntuforums.org/showthread.php?t=1672688&highlight=Users+groups+menu+missing](http://ubuntuforums.org/showthread.php?t=1672688&highlight=Users+groups+menu+missing)

Follow some of the links too.

Of course, this is for the GUI not server edition.

---

### Post by PMB2011 on 2011-01-23
Solved - gnome-system-tools wasn't installed. I'm surprised at that (given that this is server) but maybe (as the thread you linked seems to imply) some installs lose it. 

Many thanks,
Peter

---

### Post by Rubi1200 on 2011-01-23
You are more than welcome :)

Glad you got it sorted out.

Please mark this thread Solved using the Thread Tools near the top of the page so that other users can also find help.

---

