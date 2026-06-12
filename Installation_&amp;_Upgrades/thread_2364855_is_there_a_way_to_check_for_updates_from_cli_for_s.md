---
title: "is there a way to check for updates from cli for scripting ex conky?"
date: 2017-06-28
forum: Installation &amp; Upgrades
---

### Post by jeff666 on 2017-06-28
is there a way to check for updates from cli for scripting (for example conky)? I would like to know about newest kernel and security updates right when they are released (by using conky) but "apt upgrade -s | grep linux-image" will always return "WARNING: apt does not have a stable CLI interface. Use with caution in scripts." which makes it impossible to script with and it will also display auto removes which makes the results ambiguous. I need a cmd that would return something like "55 updates pending, new kernel, 12 security"

---

### Post by QIII on 2017-06-28
Hello!

You might be able to create a cron task to invoke

```
/usr/lib/update-notifier/apt-check --human-readable
```

in a script and pipe that to a log that can be read by conky rather than having it try to echo in the terminal.

Sorry, not at home at my Linux machines to check, but that's where I'd start.

---

### Post by jeff666 on 2017-06-28
thanks a ton thats perfect!

sorry spoke to soon 
sudo /usr/lib/update-notifier/apt-check --human-readable

returns zero updates

where as sudo apt upgrade has ten

---

### Post by QIII on 2017-06-28
What do you get from 

```
apt list --upgradable
```

What I am getting from apt-check, by the way, are three packages plus 7 dependencies.  So three.  Odd that you have 0 + 11.  Could you post back what you are seeing from upgradable and apt-check?

---

### Post by CatKiller on 2017-06-29
It's not something that I've played with, but doesn't apt update the MOTD to show available updates for when you log in? That might be useful as a data source for Conky.

---

