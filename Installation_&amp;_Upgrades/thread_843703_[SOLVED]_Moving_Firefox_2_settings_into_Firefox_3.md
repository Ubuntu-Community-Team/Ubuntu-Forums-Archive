---
title: "[SOLVED] Moving Firefox 2 settings into Firefox 3"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by dbsoundman on 2008-06-28
I've just built a new computer, and I installed 8.04 on it. I had 7.10 before. I remember in previous upgrades I did some sort of folder shuffle to take my firefox settings (passwords, etc) and put them on the new computer. Before I decommissioned the old computer, I copied what I believe were the relevant folders from the old firefox (they have names like 0v99938.default), but now I don't remember where I should put them to restore my settings. I already imported my bookmarks so that's taken care of, but I had a whole set of shortcuts, plugins, etc. also. Any thoughts on how I do this? I couldn't find exactly what I needed via a search...

Thanks,
Dan

---

### Post by AlexBellisBrown on 2008-06-28
The folders for Firefox are somewhere in /etc i belive. Try searching for the Firefox folders with Desktop Search.

---

### Post by dbsoundman on 2008-06-28
Thanks for the tips. Unfortunately this is a fresh install, so I'm not just upgrading. I did figure it out though; you have to place the files in the .mozilla folder (which contains a "firefox" subfolder). The .mozilla folder is a subdirectory (hidden) in the /home directory. Once I did that, all was well. I had a couple conflicting bookmark files, but once I straightened that out, all was well.

-Dan

---

### Post by aysiu on 2008-06-28
Next time you can just copy the entire .mozilla folder. Might save you the trouble of keeping track of several subfolders.

---

