---
title: "install problems"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by momo0000 on 2008-05-25
I have a problem to add an application like 7zip. I would like to install this application to read rar files. So I hope you can help me.
So I am going to explain the problem now:
First I'm searching for the application and to apply it after i applied, an error is coming on my screen:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

That's my problem and I hope you can help me. I'm not so good in these things so if you help me, explain it please in all steps.  :confused::confused::confused::confused:

---

### Post by zvacet on 2008-05-25
Applications>accessories>terminal type

```
sudo dpkg --configure -a
```

to install p7zip also in terminal 

```
sudo aptitude install p7zip p7zip-full
```

---

