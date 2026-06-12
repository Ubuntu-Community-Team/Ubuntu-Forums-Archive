---
title: "upgraded to Ubuntu 12.04, now update doesn't work"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by lucky099 on 2012-10-17
I upgraded my Ubuntu 12.04 a few weeks ago. Now it couldn't update anymore and says that:

```
Failed to download repository information Check your Internet connection
```

I would appreciate it very much if anyone could help !

Amanda

---

### Post by jerrrys on 2012-10-17
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

And you should be good to go

---

### Post by lucky099 on 2012-10-18
There are errors all over place:
```
luckyseven@luckyseven-desktop:~  sudo apt-get update
[sudo] password for uckyseven:
Ign http://dk.archive.ubuntu.com precise InRelease
Ign http://dk.archive.ubuntu.com precise-updates InRelease
Ign http://dk.archive.ubuntu.com precise-security InRelease
Err http://dk.archive.ubuntu.com precise Release.gpg
    Something wicked happened resolving 'dk.archive.ubuntu.com:http'   (-5 - No address associated with hostname)
...........

```

Amanda

---

### Post by Cheesemill on 2012-10-18
This looks like a problem with either your internet connection or the dk.archive.ubuntu.com site.

Try switching to a different mirror, you can do this from the Update Manager.

---

### Post by lucky099 on 2012-10-18
Cheesemill

I have the same errors after switching to the main Server.
My Ububtu can not detect the wireless connection. I can't browse any page using Firefox either. 

Amanada

---

