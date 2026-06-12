---
title: "Ubuntu not showing when on battery"
date: 2010-02-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JCoster on 2010-02-20
I guess this is more of an FYI as I've fixed it myself now but for the past week I've previously been unable to tell when I'm on battery (I've always had the AC adaptor icon and no battery information).

I fixed this issue this morning with the following:
```
sudo apt-get install --reinstall gnome-power-manager
```

..which installed a new package (can't remember what it was called now).  

I rebooted, and the issue is resolved.
JC

---

### Post by FAJALOU on 2010-04-06
I'm on Lucid Beta, and I can confirm this fix....
Weirdddd bug!!!  But this is a way to fix the no notification 'bug.'

---

