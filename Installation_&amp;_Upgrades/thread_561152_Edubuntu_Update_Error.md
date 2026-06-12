---
title: "Edubuntu Update Error"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by themainliner on 2007-09-27
Posted in Beginners section, please help if you can. :biggrin:

[http://ubuntuforums.org/showthread.php?t=561138](http://ubuntuforums.org/showthread.php?t=561138)

---

### Post by Pumalite on 2007-09-27
Post the entire output of:

sudo apt-get-update

---

### Post by themainliner on 2007-09-27
Excellent, I took out your erroneous extra hyphen :wink:, and got masses of errors, all pretty much the same here are the first two lines:

```
Err http://gb.archive.ubuntu.com feisty Release.gpg
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
```

Obviously, I stared aghast at this vast quantity of crap then I noticed **Cannot connect to 8080:80**!!

Aha, I thought 8080 is the port on the proxy...so the network proxy is configured incorrectly.  So I edited that GUI stylee with **System | Preferences | Network Proxy** and I am now sorted.  Thanks very much for the pointer in the right direction.

Cheers!

---

### Post by Pumalite on 2007-09-27
You are welcome. Sorry for the extra hyphen.

---

