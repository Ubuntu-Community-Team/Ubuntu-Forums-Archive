---
title: "Upgrading to Feisty w/o overwriting /home"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by Europa2010AD on 2007-07-06
Is there any way I can install Feisty (currently running Edgy) without overwriting my /home directory? I would like to have a clean install of Feisty, but retain my system settings in /home. However, from what I can remember during the one and only Ubuntu (Edgy) installation experience I have had, it'll ask me to choose the path of the /home directory. If I choose the path to my previous /home directory, wouldn't that overwrite my existing system settings?

Or should I just forget it and overwrite my existing /home directory -- are there any new files/settings that are specific only to Feisty that will be put into /home during installation?

Any suggestions would be much appreciated!

---

### Post by bmorency on 2007-07-06
do you have your /home folder on it's own partition? if you do then just remember which partition it is. during the install mount it as your home folder and do not format it. you can tell it to keep existing data. I have done it a few times before.

if you have just one big partition go into add/remove programs and look up "home user backup" to save your stuff. then you can reinstall feisty again and make /home and /usr/local their own partition. so next time you need to format you can keep those two partitions without deleting them.

---

### Post by Europa2010AD on 2007-07-09
> **bmorency said:**
> do you have your /home folder on it's own partition? if you do then just remember which partition it is. during the install mount it as your home folder and do not format it. you can tell it to keep existing data. I have done it a few times before.

I have my /home on its own partition. If I upgrade from Edgy to Feisty without overwriting /home, am I going to run into any Ubuntu configuration problems later on, with the Edgy settings being carried over to Feisty?

---

### Post by jis on 2007-09-07
I have the same problem, except I have Dapper installed.

---

### Post by merlinus on 2007-09-07
/home contains configurations and preferences for applications, not the os, so it should not be a problem.

-merlin

---

### Post by Europa2010AD on 2007-09-20
> **merlinus said:**
> /home contains configurations and preferences for applications, not the os, so it should not be a problem.

-merlin

So there is no way to retain any OS configurations and preferences during an upgrade even if I have my /home partition on another harddrive?

Call me lazy, but that's a lil bit of a hazzle having to reconfigure the OS every 6 months or so! :-P

---

