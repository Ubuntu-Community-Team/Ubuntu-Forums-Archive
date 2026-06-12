---
title: "update broke my pc"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by windows-killer on 2008-06-10
today I updated ubuntu with update manager and I restarted my pc because I wanted to use windows.
I booted back to ubuntu, loged in and then my monitor shut down. no dektop nothing. then I pressed a combination of keys to get to the command line and its able to show me the command line but not the desktop. what happened?
I think the updates broke my X server? 
can someone help me?
sorry for my English

Edit: am able to log on to the command line but when I press F7 to get back to my desktop the the screen shuts down. Or sometimes the screen shows some squares with scrambled letters on them.

---

### Post by wolfen69 on 2008-06-10
try```
sudo xfix
```

---

### Post by windows-killer on 2008-06-10
thanks for the reply but when I type this I get: command not found

---

### Post by windows-killer on 2008-06-11
Can someone help me????
come one guys you are all smart I know you can figure out my problem.
please tell me if you need more details

---

### Post by tamoneya on 2008-06-11
try:```
sudo dpkg-reconfigure ubuntu-desktop
```


there is no need to bump for 24 hours.

---

### Post by Sef on 2008-06-11
> there is no need to bump for 24 hours.

Agreed.  You can be given an infraction if you bump less than 24 hours after the last post.

---

