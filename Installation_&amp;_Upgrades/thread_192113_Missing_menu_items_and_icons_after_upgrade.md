---
title: "Missing menu items and icons after upgrade"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by mgweeks on 2006-06-08
I upgraded to Dapper and everything seemed to go fine. There were a number of packages that were flagged as obsolete but I opted to retain them just in case they were needed. After booting up, I noticed that my System - Administration menu was missing most of the items it hed before such as Synaptic Package Manager, Time and Date, Users and Groups, etc. I also noticed that none of the icons had been updated to the new icon set. The panel is also missing the search bar and quit icon.

I have gone into the Alacarte Menu Editor and it shows all of the items as being selected but they don't show up on the menu.

Anybody have any idea what went wrong? How do I fix it so that the menus and icons are updated correctly? Thanks for any assistance.

---

### Post by mgweeks on 2006-06-08
Sorry, I realized the missing icon's were simply the result of the theme I was using. I'm still missing the menu and panel items though.

---

### Post by mgweeks on 2006-06-09
In case anyone out there is interested; I've now discovered the rest of the problem. Somehow, my default login user was removed from the admin group. Once I added myself back into the admin and some other groups, my menu's now show up properly.

---

### Post by wagabonga on 2007-06-30
Hi, I'm a total newbie. I have Feisty Fawn installed on my machine but I also miss a lot of items from Admin menu, including the Synaptic Package Manager, Time and Date, Users and Groups, etc.

I tried to follow the helpful advice given by the previous user but I do not know how to add my existing user account to the admin group.

The command I found in Keir Thomas's book (Beginning Ubuntu Linux) shows how to create a NEW user and a group by using the command
[B]
sudo useradd -m -g <username> <groupname>[/B]

**-m** creates a new home directory for the new user, I understand. But I already have a home directory and I just want to add my name to the Admin list.

How can I do that with an EXISTING user? :( Thanks.

---

### Post by misterfixit on 2007-07-17
I just encountered the same problem.  Even when attempting to drag and drop an icon from the pull-down menu, doesn't work.  The icon drags but will not stick.  However when I go into home and do  cd /home/dave/Desktop and then dir, I see all of the icons.  How to restore them to all desktops?  I am user dave and user 1000.

Thanks

---

