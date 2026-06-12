---
title: "Best way to upgrade to 18.04"
date: 2018-03-15
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2018-03-15
Hello what is the best way to upgrade from 16.04 to 18.04 without doing a clean installation

---

### Post by Frogs Hair on 2018-03-15
Usually LTS upgrades are available after the first point release. You'll be able to check that at the following link after the final release of 18.04.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by oldos2er on 2018-03-15
You could try ```
sudo apt update

sudo apt full-upgrade

do-release-upgrade -d
``` I can't recommend doing this unless you have good backups in place first though. Caveat emptor!

---

### Post by RobGoss on 2018-03-15
Thank you both for the help 

I tried the second suggestion but it did not seem to do anything

---

### Post by Frogs Hair on 2018-03-15
The commands may work after the final release of 18.04. 

Edit: They do work with 17.10.

---

### Post by RobGoss on 2018-03-16
> **Frogs Hair said:**
> The commands may work after the final release of 18.04. 

Edit: They do work with 17.10.

OK thanks so much for the help my friend have a great day

---

### Post by monkeybrain20122 on 2018-03-17
The best way is to backup your data and do a clean install. Too many threads where "upgrade" using methods above left people with broken systems, and the process takes a long time too.

---

### Post by friarlawless on 2018-03-19
I did a Deja-Dup backup and took the plunge into 18.04b with this article today. So far so good. In my personal experience once they get this far along on the beta it's pretty safe. But don't take my word for it. :)

[https://itsfoss.com/upgrade-ubuntu-version/](https://itsfoss.com/upgrade-ubuntu-version/)

---

