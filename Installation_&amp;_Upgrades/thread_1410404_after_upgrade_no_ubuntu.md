---
title: "after upgrade no ubuntu"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by vigolino on 2010-02-18
I installed karmic koala with wubi 2 weeks ago. I use windows 7. It was a fantastic installation session, it had no problems. The problems have begun after installing upgrades. After the last upgrade I can't start ubuntu. I don`t reinstall ubuntu, so who can help me to start my ubuntu? [http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

### Post by darkod on 2010-02-18
This is a bug in wubi. Download the improved wubildr file from here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

and replace the file you have in the partition where you installed wubi, for example C:\wubildr, or D:\wubildr, etc.

Restart and it should be fine.

---

