---
title: "Server dist-upgrade instructions"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by wardjame on 2006-06-08
I am running a staging server that was Breezy installed with the server command.  Are there instructions for dist-upgrading this?  The wiki specifically says I have to be runing desktop and I don't want to hose my server.

---

### Post by nanotube on 2006-06-08
[QUOTE=wardjame]I am running a staging server that was Breezy installed with the server command.  Are there instructions for dist-upgrading this?  The wiki specifically says I have to be runing desktop and I don't want to hose my server.[/QUOTE]
see here: [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)
it gives you several methods of upgrading, including one that works through commandline.

---

### Post by wardjame on 2006-06-08
I looked at that but this line:
> 1. Make sure that you have ubuntu-desktop, kubuntu-desktop, or edubuntu-desktop installed (depending on which distribution you are using). This is vital for apt to perform the upgrade successfully.

made me assume that it was not what I wanted to be doing.  You still feel this is the best upgrade path for me?

Thanks for your help.

---

### Post by nanotube on 2006-06-08
[QUOTE=wardjame]I looked at that but this line:

made me assume that it was not what I wanted to be doing.  You still feel this is the best upgrade path for me?

Thanks for your help.[/QUOTE]
well, that instruction is for those people who are running desktop, to make sure that all the desktop dependencies are pulled in. since on your server you have no desktop, obviously you don't have to worry about desktop dependencies being pulled in.

so, i'd say that this should work without any problems. but, since i do not run a server myself and have not had to upgrade a server to dapper, you may wish to wait until someone who actually has done that can confirm from personal experience.

---

