---
title: "What Upgrades Are Available?"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by JSeymour on 2010-04-02
G'day,

I searched.  I poured over the man pages.  No joy.  How can one, with a *command-line* utility, determine:

[LIST]
[*] What, if any, upgrades are available for a specific package?
[*] What, if any, upgrades are available for all installed packages?
[/LIST]
 TIA

---

### Post by conradin on 2010-04-02
Well, assuming your repository has the source of the updates you want you could update your repo and then specify a program to update using the install argument of apt-get. For here, I'm using wine as an example. 
```

sudo apt-get update
sudo apt-get install wine

```

---

### Post by Elfy on 2010-04-02
I have an update to checkbox available here after an apt-get update.

apt-cache policy checkbox gives me the following information

```
checkbox:
  Installed: 0.9
  Candidate: 0.9.1
  Version table:
     0.9.1 0
        500 http://uk.archive.ubuntu.com/ubuntu/ lucid/main Packages
 *** 0.9 0
        100 /var/lib/dpkg/status
```

so ```
apt-cache policy *package*
``` would let you know if there was an update available for a single package

---

### Post by JSeymour on 2010-04-02
Got it.  Thanks, guys!

---

