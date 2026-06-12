---
title: "Install CD damaged, need to get packages from somewhere else"
date: 2005-05-10
forum: Installation &amp; Upgrades
---

### Post by bluemax on 2005-05-10
Hi. I need to install evolution 2.2.1.1 and gnome-games. These packages never installed at all because the Ubuntu installation had read errors when it tried to get them off the CD (tried it a dozen times so I'm guessing it's the disc). But now whenever I use "apt-get install" to get those packages it keeps looking for the cd-rom  instead of to the repositories. Is there some way I can work around this to get it online?

PS I'm a complete linux newbie, so please explain carefully

---

### Post by Xian on 2005-05-10
[QUOTE=bluemax]But now whenever I use "apt-get install" to get those packages it keeps looking for the cd-rom  instead of to the repositories. Is there some way I can work around this to get it online?[/QUOTE]

Open a terminal: Applications > System Tools > Terminal
Type in this line:

$ sudo gedit /etc/apt/sources.list
<password>

Comment out this line so it appears as below:

# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

Now save the file and try the 'apt-get install' again.

---

### Post by bluemax on 2005-05-10
Argh, I didn't even see that line when I edited the sources file before. Thanks, and sorry for the dumb newb question.  ;-)

---

