---
title: "new install issue"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by schmedley on 2006-08-30
I just installed Ubuntu "over" CentOS. I have 2 drives - one for the system and one for /home. After the install, when I try to click on the "Application" menu icon - the icon turns an "orange" color and does mot "open"? I'm guessing this may be a permissions issue but am not sure?

---

### Post by schmedley on 2006-08-30
I found the problem... the .config/menus directory and files within had the wrong userid. I changed them and the Applications menu works properly

---

