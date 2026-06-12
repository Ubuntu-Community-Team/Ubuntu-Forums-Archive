---
title: "Question regarding program reinstallation..."
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by dayosh on 2008-10-23
When I originally installed WINE, my Applications menu was automatically updated to include a WINE entry.  Just now, I uninstalled WINE in order to do a fresh reinstall, and the entry was not automatically re-added.

Is there a list of "already installed" programs somewhere that I must remove WINE from in order to have it automatically added to my Applications menu again, or do I need to do something completely different?  I know it's possible for it to be automatically added, since it was when I originally installed it, and I'm rather curious as to why it didn't simply automatically add it to the Applications menu as it did before.

Any help or advice on this matter is greatly appreciated, and thank you very much in advance.   :)

---

### Post by aysiu on 2008-10-23
The entries are usually .desktop files. Maybe paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) to see if Wine's .desktop file exists? ```
sudo updatedb
locate wine
locate .desktop
``` Warning: the first command could take a few minutes to execute

---

### Post by dayosh on 2008-10-23
Many thanks for the input, aysiu.  I had a little difficulty with the first command (realized it was probably "updatedb," which did take a moment or two).

I currently have reinstalled WINE, so I'll have to uninstall again to search it out and purge it, but I will bookmark this post so that I can do so with considerably more ease than would have been, otherwise.  Once again, many thanks!   :)

---

