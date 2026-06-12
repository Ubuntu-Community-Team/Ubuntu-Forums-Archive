---
title: "can't upgrade"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by rude_lee on 2007-09-07
i have ubuntu fiesty ultimate and this is wat comes up when iget the upgrade notification and i press install 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

any help please and utorrent wont open up its screen the icon appears and its running but it is forever hiding and i dont know how to uninstall and install back under wine

---

### Post by Tomosaur on 2007-09-07
Did you do what the error message told you? Close all running programs, including the updater, then open up a terminal and type:

```

sudo dpkg --configure -a

```
When that's finished, try running the following commands to update your software:
```

sudo apt-get update
sudo apt-get upgrade

```Also - this is the programming forum - you would have a better chance of having your question answered in the Absolute Beginners, or General Help forums :)

Good luck anyway!

---

### Post by rude_lee on 2007-09-08
thanks that worked before it was saying i had no permissions but any help with utorrent even if it is to uninstall is please

thanks again

---

### Post by Tomosaur on 2007-09-09
> **rude_lee said:**
> thanks that worked before it was saying i had no permissions but any help with utorrent even if it is to uninstall is please

thanks again


I assume you installed utorrent under Wine - in which case you should just be able to run the uninstaller file.

Unfortunately I've never used utorrent, and I generally don't bother with Wine, so I can't be of much help! Again - this would be better suited in one of the support forums. I'll ask a mod to move it for you - you'd have a better chance of someone being able to help you :)

---

### Post by rude_lee on 2007-09-10
no uninstaller though any other way

---

