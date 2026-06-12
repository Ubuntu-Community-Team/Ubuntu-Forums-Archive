---
title: "Installing wine"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by dan9550 on 2012-05-29
Hi, i am trying to install wine but i am having issues.

If i try "sudo apt-get install wine" i get:
The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

What can i do to install wine?

---

### Post by dino99 on 2012-05-29
be sure to install the latest wine 1.5.5

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by fantab on 2012-05-29
> **dan9550 said:**
> 
What can i do to install wine?

Install 'PlayonLinux'... it installs wine with all its required dependencies and libraries. Moreover it will be easier to manage and configure wine with PlayonLinux.

```
$ sudo apt-get update
$ sudo apt-get install playonlinux
```

---

### Post by dan9550 on 2012-05-29
I now get this:

The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-unstable but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by HalfNote5 on 2012-05-29
Try adding the following to /etc/apt/sources.list

```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main 
deb http://deb.playonlinux.com/ precise main 
```You can actually do it easily this way:

[COLOR=DarkRed]**(THIS IS ASSUMING THAT YOU ARE USING PRECISE. If you are using a different version, replace "precise" in the line with the distro name applicable to you.)**[/COLOR]


```
sudo echo "deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main" >>  /etc/apt/sources.list

sudo echo "deb http://deb.playonlinux.com/ precise main" >> /etc/apt/sources.list 
```And then simply run:
```

sudo apt-get update
```THEN try installing wine.

---

### Post by fantab on 2012-05-29
> **dan9550 said:**
> I now get this:

The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-unstable but it is not installable
E: Unable to correct problems, you have held broken packages.

We have to first remove everything wine from you system then install playonlinux:

```
$ sudo apt-get --purge -remove wine
$ sudo apt-get clean all
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install playonlinux
```

---

