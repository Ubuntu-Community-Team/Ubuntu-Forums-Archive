---
title: "Problem with Tomboy"
date: 2009-05-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-05-22
The strange thing is that Tomboy automatically displays after booting, but after closing, it won't run.
Running 'tomboy' produces the following:
> [DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG]: Unable to locate 'gnomesu' in your PATH
[DEBUG]: Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG]: Successfully found all system tools
[DEBUG]: Unable to locate 'wdfs' in your PATH

What is 'wdfs' and where do I find it?
Cheers, Mike

---

### Post by freeman2000 on 2009-05-22
"wdfs" stands for the WebDav filesystem for Fuse.  It seems to be some way of mounting file systems in Linux, and of sharing files.  I hope this gets you started.  Good luck.

---

### Post by mdurham on 2009-05-23
> **freeman2000 said:**
> "wdfs" stands for the WebDav filesystem for Fuse.  It seems to be some way of mounting file systems in Linux, and of sharing files.  I hope this gets you started.  Good luck.
Thanks for that freeman2000. I wonder why Tomboy needs something that isn't in the repo's? (or at least I can't find). The odd thing is that it has started to run after booting and is open on the desktop. From there I can use it as normal, but, if I close Tomboy it wont run again, I get the message from my first post.
Cheers

---

