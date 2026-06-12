---
title: "E:GPG error: http://archive.canocial.com wily InRelease: Clearsigned file isn't valid"
date: 2016-03-21
forum: Installation &amp; Upgrades
---

### Post by Daniel_Motz on 2016-03-21
Hello Ubuntu community!

I have following problem:
If I type: 
```
sudo apt-get update
[B]or
[/B]sudo apt update
```

Result:
 [IMG]http://commonwealthbin.bplaced.net/terminalscreen.png[/IMG]
I am using Ubuntu 15.10 Wily Werewolf newest version.
No, my network does not need an authentification (directly connected with router)

---

### Post by ajgreeny on 2016-03-21
There is an error in your sources.list file which is showing **canocial** when it should say **canonical**.

I can't imagine how that happened unless you have been editing your sources manually, but edit the file with ```
sudo -H gedit /etc/apt/sources.list
``` and replace that typo, then try to update again.

---

### Post by Daniel_Motz on 2016-03-22
It works good! Thank you ajgreeny!
I had some problems with my hard drive last days.
Maybe that is the problem. I'm going to buy a new one. (using my old one since 3 years xD)


EDIT:  Marked as solved!

---

### Post by ajgreeny on 2016-03-23
Great! Please mark as SOLVED from the Thread Tools menu at the top.

---

