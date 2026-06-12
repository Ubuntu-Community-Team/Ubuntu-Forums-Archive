---
title: "Fresh install &quot;The package system is broken&quot;"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by Windowsrookie on 2010-10-20
This is my first linux install, Fresh install of Ubuntu 10.10, and first thing I do is update.  I can't update because I get this message "The package System is broken Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"  

This a brand new fresh install, how can there be problems already!?

In terminal I've tried " apt-get install -f" and get  

"E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

---

### Post by alexandari on 2010-10-20
the **apt-get** command requires root previlieges to be executed,and in order to do so you should type
**sudo apt-get install -f**   (you will be asked for your username password)

read more about **sudo** here: [http://linux.about.com/od/commands/l/blcmdl8_sudo.htm](http://linux.about.com/od/commands/l/blcmdl8_sudo.htm)

---

### Post by Windowsrookie on 2010-10-20
Thank you, everything but sound seems to be working now. :)

---

### Post by dmjones63 on 2010-10-20
Great post - helped me out following install of v10.10 on new dual boot PC when I tried to run Update Manager.

---

