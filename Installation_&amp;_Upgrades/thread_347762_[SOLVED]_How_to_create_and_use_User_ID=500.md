---
title: "[SOLVED] How to create and use User ID=500"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by ridgeland on 2007-01-27
I need user ID=500 to work.  It's easy to create a new user with ID=500.  Go back to create another user and 500 is gone.  It's in /etc/passwd but not visible in User and Group maintenance.  I can log in as user 500 but in Login Screen maintenance user 500 can not be set to auto login.
Experimenting I see any user ID I create of 999 or less is invisible.  Any user ID I create of 1001 or more is visible.
Why care?
I believe in separating OS partitions and Data partitions.  Thus I have Fedora Core 4, Fedora Core 6 (twice actually), SuSE 10.1 and SuSE 10.2.  All on individual partitions for OS, all sharing a few Data partitions.  In each of those I use User ID = 500 for the main user and share data, even Firefox bookmarks via links.  A new bookmark I set while using SuSE is visible the next time I use Fedora.  The default Ubuntu logic blocks itself from this sharing.  
I realize the Ubuntu use of superuser ID=1000 and ID=0 (root) being disabled.  Please focus this thread on getting user 500 to work in User maintenance and auto-login, not the root explaination/debate.  
Thanks.
EDIT 29 Jan 2007 and 4 May 2007 - solution found to both problems:
1 - user maintenance --- sudo gedit /etc/login.defs   --- edit UID-MIN to be 500
In Ubuntu 6.10:
2 - auto login --- sudo gedit /etc/gdm/gdm.conf-custom  --- edit AutomaticLogin and TimedLogin to 
desired user name
In Ubuntu 7.04:
2 - Not an issue. In System -> Administration -> Login Window  in the tab 'Security' set minimum ID to 500. Close the WIndow, Open it again and then select the user for auto login.

Thanks ubuntuforums

---

### Post by reacocard on 2007-01-27
> **ridgeland said:**
> I need user ID=500 to work.  It's easy to create a new user with ID=500.  Go back to create another user and 500 is gone.  It's in /etc/passwd but not visible in User and Group maintenance.  I can log in as user 500 but in Login Screen maintenance user 500 can not be set to auto login.
Experimenting I see any user ID I create of 999 or less is invisible.  Any user ID I create of 1001 or more is visible.
Why care?
I believe in separating OS partitions and Data partitions.  Thus I have Fedora Core 4, Fedora Core 6 (twice actually), SuSE 10.1 and SuSE 10.2.  All on individual partitions for OS, all sharing a few Data partitions.  In each of those I use User ID = 500 for the main user and share data, even Firefox bookmarks via links.  A new bookmark I set while using SuSE is visible the next time I use Fedora.  The default Ubuntu logic blocks itself from this sharing.  
I realize the Ubuntu use of superuser ID=1000 and ID=0 (root) being disabled.  Please focus this thread on getting user 500 to work in User maintenance and auto-login, not the root explaination/debate.  
Thanks.

For user maintenaince, just check the option to show all users and groups.  As for auto-login, I don't know.

---

### Post by ridgeland on 2007-01-27
That seems a good clue.
"show all users" is not an option on my User and Groups maintenance window.
So I re-read the help and found a reference to:
/apps/gnome-system-tools/users/show_all
To get there you have to edit your menu to add System Tools -> Configuration Editor
There you can find the referenced "show_all"
I turned this flag on.  Exited gconf-editor.  Opened it again to verify the flag was still set. OK.
Went to User and Groups maintenance added user 501 - 
Still it does not display in User Maintenance.  
Since user 500 is not displayed I tried to add it again and got the error message it already exists.  /etc/passwd has it.
I also tried changing
/etc/gnome-system-tools/users/profiles
Here I found three fields uid-min=1000.  I changed them to 500, 500, 0.
Still no success.
Maybe these clues could help solve the mystery.
Thanks.

---

### Post by emperor on 2007-01-28
Same problem here. All my user accounts start at 500, not 1000 and no longer show up in Edgy's "users-admin". I used to use Redhat/Fedora and my file server is running CentOS 4. The Administrator should be able to see ALL accounts anyway. So this problem needs to be fixed!

---

### Post by emperor on 2007-01-28
A bug report has already been filed:

Bug #70850:[FONT=Arial][SIZE=1] [users-admin] show all users checkbox is gone and there is no way to view users with a UID of less than 1000

The work around is to edit "/etc/login.defs".

[/SIZE][/FONT]**WORKAROUND:
sudo gedit /etc/login.defs

**change this section:

#
# Min/max values for automatic uid selection in useradd
#
UID_MIN              1000             (change 1000 to 500 or perhaps 1)
[FONT=Arial][SIZE=1]

[/SIZE][/FONT]

---

### Post by ridgeland on 2007-01-28
Thank you emperor.
The edit to /etc/login.defs solved the issue of not seeing users 500 and 501 in User maintenance.
Still I cannot get auto-login to accept a user with ID less than 1000.  It lets me enter the ID but when I restart the Login Window maintenance the ID is gone.
So I'm stuck with manual login each session.  
I'm not going to chown all my data partitions and create new user 1000 in FC and SuSE just to see if Ubuntu is a keeper.

---

### Post by ridgeland on 2007-01-29
:D  I did it!
Login Window maintenance runs "gksu gdmsetup"
Editing some settings and searching for files with gdm in the name I found that
/etc/gdm/gdm.conf-custom had a new time stamp of just now.
Using 
sudo gedit /etc/gdm/gdm.conf-custom 
I changed the fields AutomaticLogin and TimedLogin from pseudoroot to me!
Yeah!  Now I can boot to my user ID (500) and share data and links with the rest of my OSs.
The GUI interface tool didn't help but search and gedit did.

---

