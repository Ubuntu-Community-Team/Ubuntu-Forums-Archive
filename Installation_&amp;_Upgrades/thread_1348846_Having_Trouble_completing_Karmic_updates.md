---
title: "Having Trouble completing Karmic updates"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2009-12-07
A couple days ago got a KK update prompt saying 31 updates were available.
Tried to do that update but only the first 8 updates went through. Updates 9-31 all failed. Tried a couple times to update but they keep failing to complete and leave the following message:
> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

First time this ever happened with Ubuntu to me. 
Usually updating is trouble free. How can I complete this updating. I keep getting an icon at the top saying these 9-31 updates are available but they keep failing when trying to updates them.

---

### Post by pastalavista on 2009-12-07
Try opening System-> Administration-> Software Sources. On the first tab, where it says "Download from:" click the drop-down and select "other". Then click "Select Best Server" and try the Update Manager again when it's done.

---

### Post by cybrsaylr on 2009-12-07
pastalavista
Well tried doing what you posted above.

It looked like it was going through OK but then got the same message appeared when finished the attempts to update.
> ould not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Then inside the box below that this was included:
> Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)/dists/karmic/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)/dists/karmic/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Then that same icon, a red pyramid with a ! inside, appeared in the top taskbar which takes me to Synaptic Package Manager.

---

### Post by pastalavista on 2009-12-07
ok then, try it with the Ubuntu CD in the drive or else open the same "Software Sources" applet and uncheck the CD_ROM option.

---

### Post by cybrsaylr on 2009-12-08
> **pastalavista said:**
> ok then, try it with the Ubuntu CD in the drive or else open the same "Software Sources" applet and uncheck the CD_ROM option.

OK tried it with the Ubuntu CD in, that didn't work.
Then opened the same "Software Sources" applet and uncheck the CD_ROM option and it looked like it went through!
Did this a couple minutes ago and so far that red triangle with the ! in the middle did not return yet to the taskbar. Maybe that did the trick....I hope.

Thanks pastalavista.

---

