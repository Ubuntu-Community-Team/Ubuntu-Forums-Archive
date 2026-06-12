---
title: "installing open office"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by paulnewby on 2007-12-24
Hello all, 

I have had Ubuntu installed now for just over a month and have found it to be excellent.

One thing i am having problems installing open office.

I am getting the following message:

E: /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.3_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libxo680li.so')

I have tried a number of things but i can't seem to solve the problem.

very greatfull if some one can advise.

Many thanks

---

### Post by Trymic on 2007-12-24
Why you tried to install open office since is already installed. Are you running Ubuntu from Live CD
From where did you tried to install it:
Add/Remove, Synaptic or manually?

---

### Post by paulnewby on 2007-12-24
After i had installed some of the updates, for some reason open office wouldn't work. so i uninstalled it.

I have re installed it using Add/Remove manager,

I have tried un installing and reinstalling with no luck.Still i get the same message?

---

### Post by Partyboi2 on 2007-12-24
What happens if you use the apt-get clean command
then try reinstalling it.
```
sudo apt-get clean
```

---

### Post by commbot on 2007-12-27
same thing, same error message. clean download of files, still won't install. any ideas?

and while I'm here, because this is annoying me now, why is 7.1 such a pain when 7.04 was easy as pie? too keen to get a new version out? i upgraded my home computer from Feisty, only to find I couldn't use my HP printer any more, I could no longer log in without a password, and now I can't use open office because it won't install. Believe me, Vista is easier to live with. While I don't particularly care for it, my wife and four year old daughter think its perfectly fine. And before anyone starts banging on about the hardware requirements, I actually had to upgrade my box to make beryl and compiz work. That made me laugh.

---

### Post by paulnewby on 2007-12-30
Thanks for the advise, 

i tried the sudo apt-get clean command and this has resolved the problem.

many thanks

---

