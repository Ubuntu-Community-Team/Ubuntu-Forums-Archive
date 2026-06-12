---
title: "installing adobe flash player"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by ianvipermaster on 2007-07-21
After i installed Adobe Flash Player on my computer it said i had to go into the component directory of firefox and remove a file called xpti.dat but when i tried to remove it it said access denied and i couldn't delete it because i'm not the owner. but i'm the only user on this computer and i was the one who set up ubuntu so i should be the owner....i don't know what's going on?

---

### Post by Pumalite on 2007-07-21
I find it strange that Flash demands the removal of a file, when they do it automatically upon installation. But if you want to, you can change permissions to the file with: sudo chmod 777 <directory><file>

---

### Post by ddrichardson on 2007-07-21
Linux uses different permissions on files that allow certain actions to be carried out such as read/write and execute.

The main two users on your system will be your login and the root user. For security reasons, many system files are marked as belonging to the root user to prevent inadvertant changes.

As the above reader stated you can change the permissions with chmod. If its just to delete a file I'd use sudo rm filename or sudo rm -fR folder

---

### Post by Gremlinzzz on 2007-07-21
gksudo nautilus
this command gives you permission to do anything type it in terminal
:guitar:

---

