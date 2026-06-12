---
title: "error from update manager"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by zayd.daruwala on 2010-08-27
this is the error i got when i tried to update it today... on the top the icon for the update manager is a red circle with a white line like a stop sign. when i click on it this is the error message i get. 

Could not initialize the package information

An unresolved problem occured while initializing the package information.

please report this bug against "update-manager" package  and include the following error message :

'E:Malformed line 54 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'


I would appreciate all the help i can get.

---

### Post by mikewhatever on 2010-08-28
You'll need to open your list of sources a see what's wrong with line 54, or post the content here  for review. To open it in gedit, run
gedit /etc/apt/sources.list

---

