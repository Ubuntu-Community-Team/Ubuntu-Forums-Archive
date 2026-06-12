---
title: "How to deal with &quot;kept back&quot;?"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by snowbug on 2008-05-17
I am new to ubuntu and wasn't able find the answer to the following question searching the forum.

When I try to do a install, I received "The following packages have been automatically kept back" and "The following packages have been kept back" in the prompt and don't know what they mean and what to do with them.

Here is what I see on the screen:
```

alan@cupid:/home/alan# sudo aptitude install viewvc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[b][color=red]The following packages have been automatically kept back:
  openssh-client[/color][/b]
The following NEW packages will be automatically installed:
  enscript gawk libpaper-utils libpaper1 python-subversion rcs
[b][color=red]The following packages have been kept back:
  openssh-server[/color][/b]
The following NEW packages will be installed:
  enscript gawk libpaper-utils libpaper1 python-subversion rcs viewvc
0 packages upgraded, 7 newly installed, 0 to remove and 2 not upgraded.
Need to get 2425kB of archives. After unpacking 10.1MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
alan@cupid:/home/alan#

```

Thanks for the help.

---

### Post by chewearn on 2008-05-18
There is nothing to worry about.

Your apt-get command is specifically installing viewvc; the relevant dependencies are automatically added.

However, the update manager find new versions of openssh-client and openssh-server packages in the repositories.  These are probably security or bugfix updates.  You have not update the openssh* in your PC to these new versions.

Just run this command, and your packages will be fully updated:
```
sudo apt-get update && sudo apt-get upgrade
```

.

---

### Post by snowbug on 2008-05-18
Thank you for the answer.

However, when I do the upgrade, it gives me:
```

alan@cupid:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
[b][color=red]The following packages have been kept back:
  openssh-client openssh-server[/color][/b]
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
alan@cupid:~#

```

And I could not do the upgrade for these two packages. Any idea what is wrong?

Thanks,

---

### Post by chewearn on 2008-05-18
An explanation:
[http://www.debian-administration.org/articles/69](http://www.debian-administration.org/articles/69)

---

### Post by kellemes on 2008-05-18
> **snowbug said:**
> Thank you for the answer.

However, when I do the upgrade, it gives me:
```

alan@cupid:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
[b][color=red]The following packages have been kept back:
  openssh-client openssh-server[/color][/b]
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
alan@cupid:~#

```

And I could not do the upgrade for these two packages. Any idea what is wrong?

Thanks,

```
sudo apt-get upgrade
``` will upgrade only upgradeable packages, it does **not** remove packages.
```
apt-get dist-upgrade
``` will upgrade packages trying to satisfy the dependencies even if it means removing packages. So watch the output carefully.. Anyway, to get your system up to date, this is the command..

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by snowbug on 2008-05-18
Perfect!

Not only my system is back to normal, but also I have learned the reasoning behind it. 

Thanks for all the replies!

---

### Post by wirah on 2008-12-01
I would also like to thank you for this. The debian link was most useful.

Shame it's so obscure. I would expect dist-upgrade to perform a distribution upgrade!

Ant

---

### Post by MaindotC on 2008-12-14
Thank you as well.  I thought dist-upgrade was the command to upgrade the distribution like from 8.04 to 8.10 which is something I really don't want to do right now :D

---

