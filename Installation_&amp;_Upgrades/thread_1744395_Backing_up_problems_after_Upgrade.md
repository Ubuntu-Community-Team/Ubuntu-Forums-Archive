---
title: "Backing up problems after Upgrade"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by louscookies on 2011-04-30
Okay so here's the deal.

Had 10.10, upgraded to 11.04.. It didn't work and my screen spat out some mumbo jumbo I didn't understand and refused to boot into the OS.

I decided to just backup everything and do a clean install of 10.10 again, however I have hit a slight speed bump. I am running a Live USB of 11.04 to backup everything from my hard drives (I'm typing on it now), but there are a few files/folders I can't access because I don't have the right &quot;permissions&quot;..

Is there anyway that I can gain these &quot;permissions&quot; so that I can read the files and back them up? They are mostly music files I am trying to back up.

HELP!

Thankyou :)
Andy.

---

### Post by Hedgehog1 on 2011-04-30
If you are using Nautilus (the GUI) to copy the files, your default permissions only allow you to work in the '/home' folder.

If you need more 'powers', you can do this (for emergencies only, please):

```
gksudo nautilus
```

This gives you super-user access rights from the GUI.  Please only use this for special situations.


***The Hedge***

:KS

---

### Post by louscookies on 2011-04-30
Thank you!  It's working :)  This will probably be the first and last time I use that but, thank you so much! You're a legend

---

