---
title: "search for files is broken"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-10-11
find works, the gui places, search for files finds nothing if I search in the filesystem these should show up.

scott2@scott2-desktop:~$ find / -name ncidd\*
/usr/share/man/man5/ncidd.alias.5.gz
/usr/share/man/man5/ncidd.conf.5.gz
/usr/share/man/man8/ncidd.8.gz
^C
scott2@scott2-desktop:~$

---

### Post by emarkay on 2009-10-11
Works fine for me to find what I have been looking for.  Dunno?  Reboot and try again.

---

### Post by sdowney717 on 2009-10-12
no seriously, for me it does not work. rebooting did not help/
it should have found something. it only finds something if i set a subfolder to search thru.

when i select filesystem, it never finds anything. people wont know where to start looking.

look at pictures, find nci* only shos files if you select /etc folder
just select filesystem and nothing

---

### Post by sdowney717 on 2009-10-12
alright, i fixed it.
reading the help file i disabled quick search and now it finds the files
this is an annoyance, it should look thru the index locate first,, 
THEN follow up with the find command and it must not be doing this.
note the pictures showing this instruction and the results.

average folk will simply think the file does not exist, so it is a big bug if it is not finalizing the search with find but only looking thru indexed files.

---

### Post by VMC on 2009-10-12
Thanks for reporting back on the fix. I too was never able to use it correctly. I just did I you and used the find command. Great find!

---

### Post by emarkay on 2009-10-12
I just encountered this too, now.  It was the ASTERISK.  I get more results, for example with "flashp" than "flashp*"to find "flashplugins" .   

How did you disable "Quick search"?

---

### Post by VMC on 2009-10-12
> **emarkay said:**
> I just encountered this too, now.  I.it was teh ASTERISK.  I get more results, for example with "flashp" than "flashp*"to find "flashplugins" .   

How did you disable "Quick search"?

Configuration Editor: /apps/gnome-search-tool/disable-quick-search

---

### Post by sdowney717 on 2009-10-12
from terminal run 'gconf-editor'

this is a big bug, imo. 
search for files will only show files that are indexed. If the file is not indexed it wont show them.
but according to the help file, it is supposed to follow up with the find command, so it does a quick indexed file search using locate and then supposed to do a slower non-indexed find command. But it does not do this if you are searching 'file system'

---

