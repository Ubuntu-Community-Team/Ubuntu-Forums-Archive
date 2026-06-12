---
title: "How to install MySQL-Admin"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-09-28
I have my reference: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
Under How to install MySQL Administrator but cant continue.

I've already install MySQL Server and I want to install MySQL Admin. I have done the following commands:

sudo apt-get update
sudo apt-get install mysql-admin

after this I get this message: 

E: Couldn't find package mysql-admin

Any help?

---

### Post by moephan on 2006-09-28
I'm pretty sure that mysql-admin lives in the Universe repository. The first thing to check is to ensure that you have the Universe repository enabled. You can check this by opening Synaptic Package manager then Settings-Repositories, and making sure that the repsitory labeled "Community Maintained (Universe)" is enabled.

Cheers, Rick

---

