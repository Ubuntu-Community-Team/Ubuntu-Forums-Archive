---
title: "[SOLVED] Dapper Drake security"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by Kuroda_Shun on 2008-03-10
I keep having to reinstall the Ubuntu LAMP 6.06 it's the Apache v 2.0.55
Every time I get it installed it takes about a week or less before my logs start changing names to "access.log.1" and the error log as well.. I read that the set up was as secure as you can get out of the box. I never change anything except to give it a static IP and to name the site I keep on it.. How do I keep getting owned if I never change anything. Is there a better server that I can install instead of 2.0.55? Is there a patch for that server version that I don't know about?
I know for a fact I was hacked because I came across my modem page online that was posted that day with my current DHCP ip. So I rebuilt it, and now it's messed up again. how do I put a STOP to it?
PLEASE.......

---

### Post by Rocket2DMn on 2008-03-10
logs are supposed to do that... They change their names to .1, .2, etc... and then start a fresh log with the original log's name.  The higher the number, the older the log.  Or maybe I'm missing your question?

---

### Post by Kuroda_Shun on 2008-03-10
Thanks, that solves my problem about the logs changing numbers/names on me. So maybe I haven't been compromised the last couple of times. But since the first time I am scared to set up the phpmyadmin and all that all over again.
Am I missing a patch that isn't part of an update? or was the first time just a fluke that happens once in a while. I know that if I am targeted then there is pretty much nothing I can do about it. But it happened a week after I went online. 
Well if you say that the LAMP is as secure as you can get with the default load then I'll believe you.

---

### Post by Rocket2DMn on 2008-03-10
If you're worried about security, check this out: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
That guy is also starting to write a tutorial for iptables as well (the built in firewall in linux).

Any patches available you can get with
```
sudo apt-get update
sudo apt-get upgrade
```

---

