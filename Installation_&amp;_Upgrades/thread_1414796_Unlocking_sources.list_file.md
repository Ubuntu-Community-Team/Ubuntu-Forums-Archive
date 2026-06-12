---
title: "Unlocking sources.list file"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by strumusa on 2010-02-24
I'm new to linux...Can someone please tell me how to unlock my sources.list file, so I can add code and upgrade Firefox 3.53 to 3.6?  Thanks..  Ubuntu 9.10


Forget it...I tried again, and it saved my source code...

---

### Post by Barriehie on 2010-02-24
> **strumusa said:**
> I'm new to linux...Can someone please tell me how to unlock my sources.list file, so I can add code and upgrade Firefox 3.53 to 3.6?  Thanks..  Ubuntu 9.10


Forget it...I tried again, and it saved my source code...

How about posting what you did to solve it and mark the thread as such. :)  It will help the next searcher!

---

### Post by wojox on 2010-02-24
Nice thing about 9.10 is if you add a ppa you shouldn't even have to mess with the sources.list. Ex:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get install firefox-3.6
```

---

