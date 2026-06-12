---
title: "Where is user data and settings stored?"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by onering on 2006-10-14
Tying to determine the best partition scheme for my Desktop Ubuntu machine.  I want to have all my user files (/home) and all other configuration/settings data (bookmarks, desktop settings, etc.) on the saem partition for easy backup.

Besides the /home directory, which other directories should I included?

Thanks.

---

### Post by meng on 2006-10-14
Your user settings will be saved in the /home directory, within hidden directories which you can see if you open a file browser in your home and press ctrl-H to see hidden files/folders. This should include your web browsing bookmarks and your email. So if you have a separate /home partition, you're done!

---

### Post by onering on 2006-10-15
Thanks meng,
So when I perform a data backup will all the hidden files be backed up automatically.  I guess it would depend on the program used.  Which backup program is recommended for use with Ubuntu?

---

### Post by aysiu on 2006-10-15
I back up using *rsync*: ```
rsync -av /path/to/source /path/to/destination
``` If you prefer a point-and-click, there's *grsync*, which is in the Universe repositories.

If you no idea what repositories are, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

