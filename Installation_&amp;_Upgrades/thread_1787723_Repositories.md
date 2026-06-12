---
title: "Repositories"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by smss on 2011-06-21
Hello.
Does anybody have information about "how to add repositories"?
 For example:
```

#sudo add-apt-repository "ppa:gnurubuntu/rubuntu"

```

---

### Post by nomko on 2011-06-21
Adding a PPA by using a terminal:
- open a terminal
- type in (or copy/paste the command line): **sudo add-apt-repository ppa:{name of package}/ppa**
- after this command a file has been created in the folder /etc/apt/preferences.d
- also an entry has been added in software sources (System > Administration > Software Sources).

Sometimes you migth even have to install an authentication key. This has to be done in the terminal as well: [B]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys {keynumber}.
[/B]
You can also do it manually if you know the correct APT line, like: **deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib non-free**
To do it manually, open a terminal and type in: **sudo gedit /etc/apt/sources.list**.
But you must have some knowledge of this stuff.

---

### Post by smss on 2011-06-21
Hi
thanks
I mean how can i create a script like this ! e.g i have created a software and i want people to use it by this script !

:D

---

### Post by nomko on 2011-06-22
Did you do a search in the internet using Google??

Then you could find this:

[http://tips-linux.net/en/linux-ubuntu/linux-tutorials/linux-file-system/create-repository](http://tips-linux.net/en/linux-ubuntu/linux-tutorials/linux-file-system/create-repository)

---

### Post by smss on 2011-06-26
There isn't any answer the my question?

---

