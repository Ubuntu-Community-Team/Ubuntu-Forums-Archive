---
title: "Updates and software installation"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by dtk on 2005-09-24
Hi!
I'm gonna install Ubuntu but I realize there will be a certain need for me to get some new software and recent updates. I have a broadband I-net channel only at work but I wanna use Ubuntu at home. So can anyone tell me if there is an opportunity to get such updates by periodicaly booting Ubuntu on my computer at work from HD of my home computer without alerting Ubuntu's configuration? Or maybe my question should sound like... How can I store several configurations of Ubuntu and have a possibility to simple switch between 'em?
I'm a new to Linux so I would like you to give me a reference to complete instructions! Thanks!

---

### Post by Xian on 2005-09-24
[QUOTE=dtk]How can I store several configurations of Ubuntu and have a possibility to simple switch between 'em?[/QUOTE]
That's really a separate issue from the topic you raise, as it deals with user prefs and not just package repo source options. Further, there are a multitude of methods for doing what you desire, and you'd be well served by googling for a strings like 'apt-get local repository'.

But an easy way is to just update one system's package cache by doing an 'apt-get update' session, then burn the /var/cache/apt/archives path to a CD and sync it to your other HD. On your next 'apt-get upgrade' command it will pull from those updated sources.

---

