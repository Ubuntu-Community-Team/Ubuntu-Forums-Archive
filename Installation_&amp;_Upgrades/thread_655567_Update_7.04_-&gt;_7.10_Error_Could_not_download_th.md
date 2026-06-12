---
title: "Update 7.04 -&gt; 7.10 Error: Could not download the release notes"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by muh2k4 on 2008-01-01
Hello there.
Iam in quite some confusement at the moment.
For some technical reasons i was forced to reinstall my ubuntu on my laptop.
Since i still had the Ubuntu 7.04-Live-CD i used this one to install the OS, i ran an update and finally i was offered the chance to upgrade to 7.10 via the upgrade-manager.

When i no choose that option i receive the following error:
"Could not download the release notes
Please check your internet connection"

as to be seen here: [click for screenshot]("http://mydlt.de/david/update.png")

I browsed the internet a bit for that problem but this one seems either to be rare or iam just to plain incapable. My bets on the second!

Some help or useful suggestions would be appreciated. thx!

---

### Post by Pumalite on 2008-01-01
If you are wired to the Internet, try this:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

You might want to take a look at this too:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by muh2k4 on 2008-01-01
Wow this seems to do something! Iam trying to find a way a couple of days already ... 

Lets see how far it gets when he is done downloading all the sources!

thx in advance. david.

---

### Post by Pumalite on 2008-01-01
You are welcome. Good luck.

---

