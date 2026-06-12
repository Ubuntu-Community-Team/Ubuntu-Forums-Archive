---
title: "Nothing happens"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by bjornsi on 2008-05-18
Very often, most often, when I get a messade about a number new upgrades, I start up upgrading. But nothing happens, just the Ubuntu sircle rotating telling I am upgrading. Nothing hppens often through a whole night. I start the PC again an try once more. Most often nothing happens neither this time.
I use Ubuntu 8.04 (hardy),Gnome 2.22.1 I have RAM 122.9 MiB,Can I do something that will help me when I wish to upgrade?

bjornsi

---

### Post by Pumalite on 2008-05-18
Post you entire specs. Are you upgrading from what to what?

---

### Post by bjornsi on 2008-05-18
Pumalite

I will mention this next time I get the problem. At the moment there are no new upgrades to see.
Thank you for your answer. I also loved your comment about the great teacher.

bjornsi

---

### Post by Pumalite on 2008-05-18
Good luck!

---

### Post by prshah on 2008-05-18
> **bjornsi said:**
> Very often, most often, when I get a messade about a number new upgrades, I start up upgrading. But nothing happens, just the Ubuntu sircle rotating telling I am upgrading.

(Just a side note: With such low RAM, you should probably be running Xubuntu rather than Ubuntu).

Looks like the common broken sudo problem. To confirm, Open a terminal (Applications-Accessories-Terminal) and give the command
```
sudo
```

The normal output should be```
~:$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

```

but if you should get an error "Cannot resolve ...", your sudo is broken. Don't worry, it's easy to fix! Continuing in the terminal:

```
hostname
```
Note the name shown.

Then
```

gksu
```

, and in the box that opens up, give the command as
```

gedit /etc/hosts

```
and the user as root. Find the line with "127.0.0.1". The name following that number series should be EXACTLY the same as the hostname above. If it isn't change it, save, and quit. Note that you should have 2 entries for 127.0.0.1; one should have localhost, and the other should be exactly the same as the hostname command above.

sudo should start working immediately.

---

