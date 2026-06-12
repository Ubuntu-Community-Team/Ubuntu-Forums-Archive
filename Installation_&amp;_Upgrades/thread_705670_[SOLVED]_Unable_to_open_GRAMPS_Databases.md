---
title: "[SOLVED] Unable to open GRAMPS Databases"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by 8oluf7 on 2008-02-23
I have recently upgraded my wife's laptop from Feisty to Gutsy. Unfortunately, the upgrade installer told me there wasn't enough room on the / partition. I tried many different routes but, in the end, went for a clean install of Gutsy. Before doing this, I copied all of the files in /home onto another machine (which is running Windows XP, as it happens). After installing Gutsy, I installed GRAMPS with Synaptic, copied the files back into the /home directory, and tried to open the database that she's spent two years building. 

File type not recognized  !!!!! 

Can anyone explain what's happening and how I can retrieve the data?

---

### Post by 8oluf7 on 2008-02-24
More research turned up a very similar question on the GRAMPS project wiki:

**Unexpected file type or format between GRAMPS Clients**

[http://sourceforge.net/mailarchive/forum.php?thread_name=1202135317.10520.10.camel%40linux2500&forum_name=gramps-users](http://sourceforge.net/mailarchive/forum.php?thread_name=1202135317.10520.10.camel%40linux2500&forum_name=gramps-users)

One of the replies points to the required wiki entry:

**Recover corrupted grdb**

[http://www.gramps-project.org/wiki/index.php?title=Recover_corrupted_grdb](http://www.gramps-project.org/wiki/index.php?title=Recover_corrupted_grdb)

I used the version 4.3 of the Berkeley database tools, which can be installed using Synaptic.

Phew - what a relief.

Reminder to self - never separate database data from its context files! Backup regularly (and whnever there's a significant change) into a portable format.

---

