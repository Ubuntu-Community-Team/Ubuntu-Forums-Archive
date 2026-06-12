---
title: "apt-get help!"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by spargos on 2008-04-04
I'm having a problem with trying to install a package called request-tracker3.6. i try running the following command:

apt-get install request-tracker3.6

but an error comes back saying:

Couldn't find package request-tracker3.6

I know people have been able to run this install without an issue, I am unsure of what to check to find out why this is failing for me.

-Jeff

---

### Post by Pumalite on 2008-04-04
Make sure your sources.lst is on.
System>Administration>Software Sources Marked them all. Reload. Try again.

---

### Post by spargos on 2008-04-04
how would you do that fromt he command prompt?

---

### Post by spargos on 2008-04-04
I've gone into the /etc/apt/sources.list and uncommented 

[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

and a whole bunch of them. and still the same error. Any additional ones you would recommend adding?

---

### Post by Pumalite on 2008-04-04
Backup your file first:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
Edit:
gksudo gedit /etc/apt/sources.list
If they are all commented out, uncomment them.
Save, exit
sudo apt-get update
sudo apt-get upgrade
Try again

---

### Post by Tomatz on 2008-04-04
edit

---

