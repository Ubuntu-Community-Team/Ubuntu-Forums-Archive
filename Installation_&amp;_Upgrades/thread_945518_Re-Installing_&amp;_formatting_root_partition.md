---
title: "Re-Installing &amp; formatting root partition"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by sites on 2008-10-12
When I just installed UbuntuStudio over my existing Hardy install, I chose to format the root partition.  After booting up the new system, my desktop background was still there, compiz was still running, gnome-panel wasn't running...... So basically all my old settings had been preserved.  How do I avoid this without formatting the entire disk?  I don't want to lose my home partition.

---

### Post by sites on 2008-10-13
wellallrightythen..... i found out that if i use a different name for my home folder, that does the trick.  of course, then i have to move the contents of the old home folder to the new one, but oh well....

any other ways of avoiding this problem? maybe i can delete a config file from the home folder, or something?

anyone?:confused:

---

### Post by tommcd on 2008-10-13
Just remove all the hidden config files and folders in your home directory. All the hidded config files begin with a "."
Just click edit > preferences in any file browser window and select the view tab. Check "show hidden and backup files" and move all the files and folders that start with a "." to another folder.

---

### Post by sites on 2011-02-27
And what if some of those hidden files contained data that I want to keep?  Thanks for the response, but I'll pass on that option.  Case closed..... 2.5 years later :)

---

### Post by tommcd on 2011-02-27
> **sites said:**
> And what if some of those hidden files contained data that I want to keep?  Thanks for the response, but I'll pass on that option.  Case closed..... 2.5 years later :)
Well you could always keep anything that you want to keep.

If you have a separate home partition, then all of your configurations that are stored in home will be preserved if you reformat and reinstall to the root partition. This is something that most people find to be desirable, so they do not have to recreate all of their settings, etc.
So just delete anything you do not want. Keep what you do want. It is always your choice.

Just out of curiosity, why did it take you so long to reply back? You could always ask for help here. I always follow up on threads that I respond to.
Write back if you need more help.

---

