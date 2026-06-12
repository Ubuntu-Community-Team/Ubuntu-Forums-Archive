---
title: "How do I add the Multiverse rep from command line?"
date: 2014-09-03
forum: Installation &amp; Upgrades
---

### Post by Blix775 on 2014-09-03
I need the pepper-flash pluging from the non-free repositories for Chromium and I can't use the GUI to do it. I searched the forums for ways to do this but there was only tangential topics and not even one that directly addressed this. I'm using 14.04 btw.

---

### Post by mooreted on 2014-09-03
Open a command line and enter:

sudo nano /etc/apt/sources.list

Add the following lines to sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

Those are the entries in my sources.list.

---

### Post by Bashing-om on 2014-09-03
dennisvalencia11-gmail;

Something like:
```

sudo add-apt-repository "deb <your_source_url_here>/ $(lsb_release -sc) multiverse"

```
([deb http://us.archive.ubuntu.com/ubuntu](deb http://us.archive.ubuntu.com/ubuntu))
Also, if that handle is your actual E-mail, ya might seriously consider loosing it .. spam from the spiders on the net !

[INDENT][INDENT]Hope That Helps
[/INDENT][/INDENT]

---

### Post by oldos2er on 2014-09-03
Make a backup copy of your sources.list file first: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
``` then ```
sudo nano /etc/apt/sources.list
``` then add the following two lines to the file: ```
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
``` Ctrl-X will prompt you to save the file, hit **y** to save the changes, then ```
sudo apt-get update
``` to finish.

---

### Post by Blix775 on 2014-09-04
Thanks to everyone for the help. And how can I change my screen name, Bashin-om?

---

### Post by Bashing-om on 2014-09-04
dennisvalencia11-gmail;

As we move smartly right on along ->
If you infer this " dennisvalencia11-gmail " as the screen name. That is a matter you will have to take up with the forum moderators to resolve in the 'Resolutuin Center' sub forum.

[INDENT][INDENT]not much help
[INDENT][INDENT][INDENT]but a push in the right direction
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

