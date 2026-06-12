---
title: "Gnome RDP error connecting to database"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by mapic on 2007-08-11
When starting Gnome-RDP on Ubuntu 7.04  I get "Error during the connection to database"

Starting from a terminal creates the same message, followed by  a memory dump.

Funny thing is that has been working for ages, until  yesterday when I  installed Kubuntu-desktop. Did not work for me because KDE hang at start so I removed  Kubuntu-desktop.

AFAIK the Gnome-RDP error started immediately after that.  I tried removing reinstalling but doesn't improve. Rdekstop works.

Thank you very much for any help

mapic

---

### Post by Sciamano on 2007-08-13
Same problem here. But I've never installed the kubuntu desktop.

---

### Post by sk8dork on 2007-08-14
i am having this same problem....weird. everything was working for months up until last week, today when i tried to run gnome-rdp i got the error connecting to database problem. i actually have been running openbox with gnome-setting-daemon. i don't have kde-desktop installed, nor have i changed anything recently. i tried upgrading everything with 'aptitude upgrade' but that didn't help.

i'm now having to use tsclient.

---

### Post by Unlimited1 on 2007-08-22
anyone have an answer to this issue yet?  I know it's a permission issue because I can run it fine under root permissions, but I just don't know where the file is to fix the permissions on...  (can't find it).:confused:

thanks,

---

### Post by greyghost751 on 2007-08-25
Try deleting  .gnome-rdp.db in your home folder, this worked for me.

---

### Post by Sciamano on 2007-09-21
yippeee, it worked!! Thanks greyghost751!

---

### Post by hodenkat on 2008-06-16
> **greyghost751 said:**
> Try deleting  .gnome-rdp.db in your home folder, this worked for me.

I just renamed it...same result... it worked!

Thanks

---

### Post by lisati on 2008-06-24
> **greyghost751 said:**
> Try deleting  .gnome-rdp.db in your home folder, this worked for me.

Thanks.


EDIT: Google is your friend (which is how I found this thread)

---

### Post by mtncrvr on 2008-06-24
I also had the same problem, worked fine for a long time and suddenly it's not working..

It would appear that the mysqlite version or format used has been changed from 3.0 to 2.1 per the header of the .gnome-rdp.db files as follows:

Newly created .gnome-rdp.db file (after I renamed the existing file and rdp is working again):
This file contains an SQLite 2.1 database

Previous file header (when it was broken):
SQLite format 3

Not sure why this happened though ? Anyone ? It's pretty annoying to loose all of your RDP sessions (I had >30 that will now have to recreated....:mad:).

---

