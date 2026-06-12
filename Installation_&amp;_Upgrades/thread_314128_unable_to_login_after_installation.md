---
title: "unable to login after installation"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by eesin on 2006-12-07
have installed edgy, from fc5. bcos my home dir is in a different partition, i chose not to format so as to retain data. but after installation i am unable to login. actually after login in, it will throw me out immediately. i know this has got to do with user/group id of the files inside my home directory. but how do i go about changing them so that i can login.

ps: currently i have created another user name for myself so that i can still use the m/c.

---

### Post by bapoumba on 2006-12-07
Hi,
if I understand correctly, are you trying to use the same /home with Fedora and Ubuntu ? Guess this is not a good idea. Both distributions should have their own /home, you can have an exchange ext3 partition to share files (even mails and bookmarks).
What is m/c ?

---

### Post by eesin on 2006-12-08
thanks. bcos all my files are in the home directory, so i created the same user name when installing ubuntu. actually, i have solved the problem, i ran the command is "chown username. . -R" inside the home directory where the files need to be changed to the "new" user. but then the panels did no look right, so i deleted the panel config files to get back the default.

m/c is my short form for machine.

---

### Post by bapoumba on 2006-12-08
Well, if you got it working, that's fine. Just keep in mind that if some desktop packages are updated in one distribution, but not in the other one, you might have problems with conf files.

And thanx for m/c (I actually did internet searches for that before I ask you, but did not find anything relevant ;))

---

