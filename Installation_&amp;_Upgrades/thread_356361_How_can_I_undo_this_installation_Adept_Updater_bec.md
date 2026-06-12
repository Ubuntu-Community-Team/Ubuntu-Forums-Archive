---
title: "How can I undo this installation? Adept Updater became crazy"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by SebbeJohan on 2007-02-08
Hi,

I wanted to get hotmail into kmail and followed this howto [HTML]http://www.ubuntuforums.org/showthread.php?t=200408&highlight=hotmail[/HTML]
however I had to stop halfway because I didn't know the gedit for kubuntu. Anyway, now I can see that adept manager notifies me of an upgrade (linux-generic-headers and linux-image-headers) even if I proceed with the upgrade. The notification in the system tray is always there? I think this is due to the unsuccessful installation. How can I undo it????? this is exactly what I did (from the howto in question):

[PHP]Code:

sudo apt-get update

Now, install the inet daemon

Code:

sudo apt-get install inetutils-inetd

This takes care of all of our dependencies. Now on to the good stuff...

Code:

sudo apt-get install hotway hotsmtp [/PHP]

I stopped right there. Please help me undo this!!!! I'm afraid I broke something :(

---

### Post by mikewhatever on 2007-02-08
Hi, what's the output of ```
 uname -a
```

---

