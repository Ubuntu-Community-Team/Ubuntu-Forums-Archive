---
title: "MySQL complete removal is not complete"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by markg85 on 2008-08-15
Hey,

I just did a mysql-server-5.0 complete removal to get rid of mysql and hopefully the conf files as well.. well i was wrong.

/etc/mysql was still there
/usr/lib/mysql was also still there while i did allow the removal script to remove all my databases.

Now comes a stranger thing.. i removed those folders myself and reinstalled mysql (i screwed something and wanted a default install back) now the /usr/lib/mysql folder was simply not made :s same with the conf files...

How can that happen!
This way i can never reinstall mysql with the default ubuntu settings.

Any solutions for this? Now i'm without mysql...

Seems to me that something is horrible wrong in the complete removal script of mysql.

EDIT:://
Might have found the solution..
when you completely remove mysql-server it won't remove mysql-common! it will remove a ton of other packages but not that one.. And for some reason it removed KDE as well! No clue why but it just did.

---

