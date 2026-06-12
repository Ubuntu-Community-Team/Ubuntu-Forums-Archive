---
title: "&quot;Places&quot; menu uses F-Spot instead of Nautilus!"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by desconocido on 2010-06-09
After a disastrous attempt to upgrade Ubuntu 8.04 to 8.10 (system would not boot), I partitioned the disk in two and installed 9.10 on the new partition.
The old data was still available so I copied my old home directory on top of my new one thus:
cd /media/bd.....d0/home
sudo cp -r --preserve=all -t /home ./bob

I have managed to re-install all my software, but a few problems remain.
Here is one of them:

In the Places menu in the top panel of the desktop, choosing anything except "Computer" leads to the folder being opened by F-Spot instead of presumably Nautilus. I probably messed something up by copying old hidden folders into my home directory. Any idea which folder would control what the Places menu does?

---

### Post by Deadite81 on 2010-06-09
That's a pretty crazy problem!  Perhaps you're defaults.list or mimeapps.list in ~/.local/share/applications point to Fspot as the default application for the mimetype inode/directory.  That shouldn't have happened, I don't know how it would; what happens when you open folders in Nautilus?  

It sounds like you know what your doing, so that's probably a long shot.

In /usr/share/applications/defaults.list or ~/.local/share/applications/defaults.list there should be line that reads:
```
inode/directory=nautilus-folder-handler.desktop
```Also, the files mimeapps.list in both the afore mentioned directories can override what's in defaults.list.  So if a line in those files exists with the inode/directory mimetype, nautilus-folder-handler.desktop should be the first in the list.

Any settings in these files in your user directory will override the global ones, so if you think this may be the case, be sure to check both! 

I second the notion of wanting to know where the data for the "Places" menu is kept.  I can hand edit every other menu under the xdg specification, spent a lot of time learning it actually, and CANNOT find this information, on this forum or elsewhere.  And believe me when I say I've looked and looked and looked...Sometimes not being a developer and using Linux sucks :)

---

### Post by desconocido on 2010-06-10
Wow. I found this in my local mimeapps.list. I have no idea how it got there.

```
inode/directory=f-spot-view.desktop;
```

I removed it. Problem solved. I might mark this thread solved if I thought I knew what was going on. Thanks.

---

### Post by Deadite81 on 2010-06-10
Kinda strange that your file was like that.  In my experience Ubuntu seems to make sure that this doesn't happen automatically, so I don't know what's going on either!
In any case, if you still want to use Fspot, or anything else to open a folder from the right-click menu, you can always add it back *after* nautilus-folder-handler.desktop in your mimeapps.list file, separated by a semicolon.
It is also possible to add new programs to the Nautilus right-click menu by choosing "Open With Other Program", but this has it's flaws (if the .desktop file has no assigned mimetype it will not show up in the list, which to me is a terrible oversight in the user friendliness department  Just because it has no mimetype does not mean I don't want to open a particular file with it!).
Anyway, glad to help!

---

### Post by Mgdavie on 2010-09-12
Thanks Deadite81!! This helped me too, except mine was with Rhythmbox. :popcorn:

---

### Post by Deadite81 on 2010-09-12
[ Link is dead ]
[ ]("http://stuffidowithubuntu.blogspot.com/2010/07/first-up-to-bat-nautilus-folder.html")

---

### Post by Cb750rider on 2011-10-20
I am glad I found this. I had the same problem after upgrading to 11.10 from 10.4 LTS. There were f-spot entries in mimeapps.list for the directory files. I removed those and everything is working great.

-Lee

---

### Post by Deadite81 on 2011-10-20
GNOME certainly hasn't made the upgrade from 2.x to 3.x smooth, but this problem was finally fixed in Nautilus 3.x, as far as I can tell anyway.

---

