---
title: "APT-GET : Cant apt-get"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by darkspider on 2005-08-21
After run apt-get update, I executed 
```
[INDENT]**apt-get install libpcap**[/INDENT]
```
however, I've got this error message 
```
[INDENT]**root@xxx:/ # apt-get install libpcap**[/INDENT]
```
```
[INDENT]**Reading package lists... Done**[/INDENT]
```
```
[INDENT]**Building dependency tree... Done**[/INDENT]
```
```
[INDENT]**E: Couldn't find package libpcap**[/INDENT]
```
```
[INDENT]**root@xxx:/ #**[/INDENT]
```
Please kindly advise.

---

### Post by adwait on 2005-08-21
There are three possible things: 
1) You made a spelling mistake in the name of the app.
2) You haven't enabled universe and multverse in your appositories (if you don't know what that means, you probably haven't, so search the forum or wiki on how to do that)
3)The app you are looking for is simply not available in the ubuntu repositories.

---

### Post by earobinson on 2005-08-21
Did u just upgrade to breezy and posted this here by mistake?

---

