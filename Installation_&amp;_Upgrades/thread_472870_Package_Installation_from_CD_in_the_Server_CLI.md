---
title: "Package Installation from CD in the Server CLI"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by ehull82 on 2007-06-13
Hi Everyone,
I was curious how I would install additional packages from the Ubuntu CDs in the CLI?

More specifically, I have installed Server 7.04 on my PC and I want to install the Gnome Desktop to try and make learning the OS a bit easier but I don't have an internet connection (in the process of moving). I have the Ubuntu server and desktop CDs though but don't know how I would install the packages needed.

Any suggestions welcome! Thanks.

-Eric

---

### Post by ehull82 on 2007-06-13
*nudge*

---

### Post by modorf on 2007-06-13
> **ehull82 said:**
> Hi Everyone,
I was curious how I would install additional packages from the Ubuntu CDs in the CLI?

More specifically, I have installed Server 7.04 on my PC and I want to install the Gnome Desktop to try and make learning the OS a bit easier but I don't have an internet connection (in the process of moving). I have the Ubuntu server and desktop CDs though but don't know how I would install the packages needed.

Any suggestions welcome! Thanks.

-Eric

you should be able to load the ubuntu-desktop packages from your desktop cd.

check your /etc/apt/sources.list to include your installation cd.
you will be looking for a line like this : 
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted

sudo apt-get update
sudo apt-get install ubuntu-desktop

that should load the gnome and all depenancies

---

### Post by ehull82 on 2007-06-14
That doesn't seem to be working.  I added the line you wrote, ran sudo apt-get update and it spit out an error saying I needed to use apt-cdrom to register my desktop cdrom.

I did 'sudo apt-cdrom add' and it seemed to work but then when I ran 'sudo apt-get install ubuntu-desktop'  it said that there wasn’t a package by the name ubuntu-desktop.

I finally tried doing a search (find –name *ubuntu-*.deb, and find –name *desktop*.deb) on my entire machine, the server CD and the desktop CD for the desktop package and it found nothing.

Suggestions welcome.
:-|

---

### Post by ehull82 on 2007-06-14
bump

---

### Post by Nortonw on 2007-06-15
I have the exact same problem.

Seems no-one knows how to do this.

I spent the whole day yesterday trying to achieve this and with no success.
Hopefully someone will be able to advise today.

---

### Post by pxwpxw on 2007-06-15
with cd in drive.

[code[
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
[/code]

(or you might prefer xubuntu-desktop or kubuntu-desktop)

---

### Post by ehull82 on 2007-06-15
I don't think people understand.  Even with doing everything that has been suggested (even though people are only saying to do the exact same thing over and over) it won’t install.  In fact there isn't a package with the name ubuntu-desktop on either one of the Ubuntu 7.04 ISO install CDs (desktop and server install CDs).  Try doing find –name *ubuntu-desktop*.deb with both ISO CDs mount and it will come back with nothing.

I finally did a search while on a machine at work for ubuntu-desktop .deb package and found [http://packages.ubuntu.com/feisty/metapackages/ubuntu-desktop](http://packages.ubuntu.com/feisty/metapackages/ubuntu-desktop) 

I downloaded the i386 .deb file, burned it to a CD and even using that CD it wont install.  I've tried everything I can to get apt-get to see that file and it is so beyond frustrating since it just won’t work!

---

### Post by zvacet on 2007-06-15
You need alternate CD to install any kind of desktop.

---

### Post by christhemonkey on 2007-06-15
You cant load most of the packages off the install cd as they are contained within a squashfs which is used on the cd.

<plug>
You can however use a program i have written called Wubdepends which allows you to get a program and all its dependencies so you can copy them to your offline ubuntu pc and install them.
See my signature for details :D.
</plug>


Oh and btw to install a .deb file from a cd/usb stick/whatever use the command:
```
sudo dpkg -i /path/to/your.deb 
```

---

### Post by ehull82 on 2007-06-15
Thanks I'll try that next when I get home.

---

