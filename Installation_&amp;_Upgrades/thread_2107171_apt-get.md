---
title: "apt-get"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by ciscosystem on 2013-01-21
hello guy
 i removed a package on ubuntu suddenly i realized i don't have apt-get command anymore how can i install apt package again ?
 thanks

---

### Post by ibjsb4 on 2013-01-21
Are you sure?  It wouldn't remove itself, did you remove it?

Give it a try in terminal to see if it works.

```
sudo apt-get update
```

---

### Post by grahammechanical on 2013-01-21
Open the Ubuntu Software Centre and search for apt. And you might see at the top of the list Commandline package manager. If it has a green circle icon with a white tick/check mark then it is still installed. Otherwise, you must hope that Software Centre does not use apt to install software.

Regards.

---

### Post by |{urse on 2013-01-21
You can open a browser, go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Scroll down, there is a text search field, locate the package you want (be sure to select the correct distro i.e Quantal)(I'm assuming you need apt)

That would be here [http://packages.ubuntu.com/quantal/apt](http://packages.ubuntu.com/quantal/apt)

Once downloaded you can install the package with 

> sudo dpkg -i packagenamehere.deb

Here's the other problem.. are we sure the package 'apt' provides apt-get?

Anyone?

---

### Post by steeldriver on 2013-01-21
yes that should do it

```
$ apt-file search $(which apt-get)
apt: /usr/bin/apt-get
haskell-debian-utils: /usr/bin/apt-get-build-depends

```

---

### Post by |{urse on 2013-01-21
Ah, thanks. I was trying to remember the equiv to 'yum provides' lol. There ya go OP ;)

---

### Post by ciscosystem on 2013-01-22
thaaaaaaaaank uuuuuuu guys everything works great now i gave apt-get again  
:guitar::guitar:

---

