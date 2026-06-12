---
title: "tomboy notes blank after sync"
date: 2010-02-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dimeotane on 2010-02-20
I just synced my notes yesterday to find that half my notes were blank upon opening them.  Some notes missing on my laptop are there on the server, intact.  Some are now missing from both my laptop and Ubuntu One. This is a critical problem as many of us rely on Tomboy daily for managing our information.  

I'm speculating here but could this be related to syncing across two different versions of Tomboy... one run from Karmic (1.0) and one run in Lucid (1.1.2) ?

This bug was first reported only a few days ago on launchpad.

[https://bugs.launchpad.net/ubuntuone-client/+bug/524339](https://bugs.launchpad.net/ubuntuone-client/+bug/524339)

---

### Post by dimeotane on 2010-02-20
Good news I just chatted with rye  on #ubuntuone

"this is known, it has already been fixed but the fix is not yet deployed 
...
 I will make sure that the fix is deployed on Monday, this is a very important part of the service"

twitter.com/ubuntone update:
*We are currently investigating the issue that may cause your notes to be empty after synchronization. Stay tuned!*

---

### Post by dimeotane on 2010-02-21
If you haven't yet backed up your Tomboy notes to a local file, and you have valuable information in your notes that you don't want to lose, back up now! 

I think the only way to be sure is copy it off ubuntu one by hand into a text file.  (I'm using notecase).

At this point some of my info only remains online on Ubuntuone, and if on my next sync, those notes are also blanked out... it's gone for good.

---

### Post by Konrad Ansehelm on 2010-02-22
I'm affected by the same problem. I checked the bug report but did not see any mention that it is fixed. I advise to make backups of the notes very regularly and refrain from syncing until it is resolved.

The export to HTML option is rather unwieldy, it's easier to simply archive the tomboy notes folder :
```
tar -czvf ~/Desktop/tomboybackup.tar.gz ~/.local/share/tomboy/
```

edit: btw I'm on Karmic

---

