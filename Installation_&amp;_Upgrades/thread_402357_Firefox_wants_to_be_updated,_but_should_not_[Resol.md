---
title: "Firefox wants to be updated, but should not [Resolved]"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by kag on 2007-04-05
I'm using Dapper Drake and I installed Firefox 2 following the steps on [this page]("http://www.psychocats.net/ubuntu/firefox").

However now that a new version of the 1.5 line has come out, the software update pops me three new updates (firefox, firefox-gnome-support 1.5.0.11 and libnspr4). All three have "1.5.0.11" somewhere in the "New version:" field.

How can I tell the package manager that I already have a newer version? Or any other suggestion?

---

### Post by eapache on 2007-04-05
FF 2 should be in the package repository already. You might have confused it by installing version 2 without using synaptic. Can you check the add/remove programs area and see what version of FF is in it?

---

### Post by aysiu on 2007-04-05
The script that installed Firefox 2.0 installed 2.0 next to 1.5, not in place of it.

To test this functionality out, press Alt-F2. You should get a *Run* dialogue where you can run commands.

If you want to launch 2.0, you use the command *firefox*

If you want to launch 1.5, you use the command *firefox.ubuntu*

So 1.5 (the native Ubuntu version) is installed, just not used. 2.0 (the Mozilla version) is also installed. If you don't want to update 1.5 any more, go to Synaptic Package Manager and go to Package > Lock Version.

---

### Post by kag on 2007-04-05
Remember eapache, I'm using 6.06.
According to Synaptic, the installed version is 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 and the latest version is 1.5.dfsg+1.5.0.11-0ubuntu0.6.06.1


aysiu, will updating the 1.5 version break the 2.0?

---

### Post by aysiu on 2007-04-05
For more details on locking 1.5, read [this post](http://ubuntuforums.org/showthread.php?p=2076216#post2076216).

---

### Post by kag on 2007-04-05
Thanks!

---

