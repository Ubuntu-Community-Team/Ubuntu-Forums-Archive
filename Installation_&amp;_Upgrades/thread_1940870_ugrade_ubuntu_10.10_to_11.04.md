---
title: "ugrade ubuntu 10.10 to 11.04??"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by vishard on 2012-03-14
upgrade manager is not upgrading ubuntu 10.10 to 11.04 showing authentication failed error.

Help

---

### Post by jerrrys on 2012-03-14
open a terminal and enter:

sudo apt-get update

get errors?

---

### Post by Joypiper on 2012-05-08
I am having trouble with the same upgrade, as well.
Using the Upgrade Manager, I get the attached message.
But, when I tried to open a terminal and enter:

```
sudo apt-get update
```

I get no errors, but neither do I get the upgrade.

Any other ideas on how to upgrade?

---

### Post by Bucky Ball on 2012-05-08
Well, 10.10 is no longer supported and I wonder if that is at the root of your problem, i.e. 10.10 is no longer getting updates (which is why you're not getting updates) so perhaps the function to upgrade to the new release has also reached end-of-life and is no longer supported either.

I would say with 10.10 your on you're on your own at this point and may need to go for a clean install. I hope, for you, that this is not the case and perhaps a wiser head can clarify ...

It's a theory ... ;)

---

### Post by Joypiper on 2012-05-08
Actually, I ended up getting the upgrade by following the instructions on [[COLOR="Blue"]another website[/COLOR]]("http://askubuntu.com/questions/22747/how-to-upgrade-from-ubuntu-10-10-to-11-04")...

They posted the terminal command line required is as follows:

```
sudo do-release-upgrade
```

This seemed to do the trick.  I have not tested all applications / functionality, yet. As a minimum, I noticed I lost my wired network connection, and cannot get the card activated yet.

I will post any problems with my DELL XPS M1330 running 11.04 elsewhere. 

This should end this thread for me.

---

### Post by Bucky Ball on 2012-05-08
Cool. Please mark thread as 'Solved' from thread tools to help others. ;)

---

