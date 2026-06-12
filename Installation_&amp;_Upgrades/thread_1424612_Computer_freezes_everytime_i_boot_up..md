---
title: "Computer freezes everytime i boot up."
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by anklebone12 on 2010-03-08
Haven't gotten any replies from the General help section so I assume it was the wrong area to post my problem. if this is the wrong area then please feel free to delete this/show me where to go with this problem.

I'm on the live cd now. 

Just installed Ubuntu, did the updates and everything went well. Then while I was enabling the compiz effects (3d cube, wobbly windows etc..) my computer froze. now whenever I try to boot it up, it freezes before even leaving the loading screen. Is there any way I can turn off the compiz stuff in my linux partition using the Gnome Terminal from the live cd, or any other way? 

Also, why is it freezing in the first place? I was certain my specs were up to date.

pleasse help.

---

### Post by lidex on 2010-03-08
Can you post the contents of your .xsession-errors file? It's in your user directory. Also these:
```
/var/log/Xorg.0.log
/var/log/messages

```

---

