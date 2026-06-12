---
title: "fwbackups backup error log"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by elmasry.ayman on 2010-12-15
this is what I got after a schedueled backup using fwbackups:

```
Dec 14 02:00:02 :: INFO : Starting automatic backup operation of set `Projects INCR BKP' 
Dec 14 02:00:02 :: WARNING : There was an error while performing the backup! 
Dec 14 02:00:02 :: ERROR : Traceback (most recent call last):   File "/usr/lib/python2.4/site-packages/fwbackups/operations/backup.py", line 698, in start  pkgListfiles = self.createPkgLists()   File "/usr/lib/python2.4/site-packages/fwbackups/operations/backup.py", line 85, in createPkgLists  fh = tempfile.NamedTemporaryFile(suffix='.txt', prefix="%s - tmp" % _('rpm - Package list'), delete=False) TypeError: NamedTemporaryFile() got an unexpected keyword argument 'delete'  
Dec 14 02:00:02 :: INFO : Canceling the current operation! 
Dec 14 02:00:02 :: INFO : Finished automatic backup operation of set 'Projects INCR BKP'
```

I tried to install fwbackups using source compile and failed at first for not adding a certain option for the configure command (--prefix=/usr), and succeeded after adding the option. But I might have forgot to clean after the first bad installation, would this have anything to do with this error?

This is something that I get when starting fwbackups from the terminal

```
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply,
 the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

any explanations?

---

