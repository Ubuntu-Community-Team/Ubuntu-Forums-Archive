---
title: "I don't want to update a package..."
date: 2006-02-27
forum: Installation &amp; Upgrades
---

### Post by Razziel on 2006-02-27
I've installed an old version of nautilus-sendto. Now, the updates-notifier (i don't know its name) needs to update the system and will remove the nautilus-sendto that I have just installed. Can I tell apt not to touch this package when I send an apt-get upgrade?

Thanks

---

### Post by claes on 2006-02-27
There is a function with dpkg so you can set a package to hold the version. Try:

sudo -s
echo packagename hold | dpkg --set-selections
exit

To remove if from the hold:

sudo -s
echo packagename install | dpkg --set-selections
exit

Claes

---

### Post by Xian on 2006-02-27
Another method:

$ sudo apt-get install wajig
$ sudo wajig hold <packagename>

To un-hold:
$ sudo wajig unhold <packagename>

---

