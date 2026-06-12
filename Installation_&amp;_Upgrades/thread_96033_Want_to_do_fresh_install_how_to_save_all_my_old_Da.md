---
title: "Want to do fresh install: how to save all my old Data?"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by Blob on 2005-11-27
I want to upgrade to the latest and was wondering if someone could point me to a link with regards to keeping all my old folders and data and config files etc... from my former installation.

I thought I might just copy to a DVD the entire contents of my Home folder and simply drop it back into my fresh installation and I would have all my stuff back.

Is it that simple?

Thanks for any help.

---

### Post by xtacocorex on 2005-11-27
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

You'll have to modify it to work with just your home directory. If you don't want to do that, copying everything in your home directory works too. The only problem could be programs changing details in config files, but that shouldn't be an issue.

When you reinstall, make a separate partition just for home so if you ever reinstall in the future, you won't need to worry about data loss.

---

### Post by aysiu on 2005-11-28
If you're planning to do fresh installs often, you might consider making a separate /home partition (by the way, /home is where all your settings and preferences live).

---

### Post by Elrohir on 2005-11-28
just asking... what size should be good enough for /home??

---

### Post by aysiu on 2005-11-28
It depends on how big your hard drive is and what you put in your /home partition.

For example, I don't put anything in my /home partition except settings and preferences because my files (music, pictures, documents) all live on a separate FAT32 partition I share with Windows.

---

