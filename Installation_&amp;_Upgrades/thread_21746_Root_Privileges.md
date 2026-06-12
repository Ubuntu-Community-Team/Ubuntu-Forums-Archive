---
title: "Root Privileges"
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by jimwinfrey on 2005-03-23
Just installed Warty Warthog and thought everything looked good.  Went to add a couple of apps and found I was not asked to set up a root password (super user).  Is it possible to set up the su account without reinstalling Ubuntu?

Thanks,

Jim

---

### Post by wylfing on 2005-03-23
Ubuntu does not have a "root" account. You must escalate your priveleges on a command-by-command basis using the command 'sudo'. For example, to update your repository cache, you'd type
```
sudo apt-get update
```
The 'sudo' part escalates your priveleges for the purpose of running the command 'apt-get'. Make sense?

---

### Post by Buffalo Soldier on 2005-03-23
After running any command with **sudo**, it will ask your for a password. Just enter your user password that you use to login.

Give sudo a try, at least a week before you pass judgement. Most probably you'll find it more efficient than having a root user :)

---

