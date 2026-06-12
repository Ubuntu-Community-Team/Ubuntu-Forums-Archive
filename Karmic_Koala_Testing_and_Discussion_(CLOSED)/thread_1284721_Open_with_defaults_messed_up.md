---
title: "Open with defaults messed up"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hanlin on 2009-10-06
Just today, I noticed that the application associations with my files have been messed up. Everything seems to want to open in either in Lyx or OO Writer, regardless of the file format. I'm not sure if this is Karmic related, but is there a way to reset all file extension associations to their defaults?

---

### Post by TrueJournals on 2009-10-06
The shared-mime-info update recently broke this...  [http://ubuntuforums.org/showthread.php?t=1284510](http://ubuntuforums.org/showthread.php?t=1284510) is the relevant thread, with [http://ubuntuforums.org/showpost.php?p=8064645&postcount=23](http://ubuntuforums.org/showpost.php?p=8064645&postcount=23) being the fix.  Note that you'll need to either run ```
nautilus -q
``` or restart your computer after running that command.

---

