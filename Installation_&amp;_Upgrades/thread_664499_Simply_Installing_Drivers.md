---
title: "Simply Installing Drivers?"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by ttmw on 2008-01-11
ive just been searching for a driver i need apparently, and have downloaded it and put it in the documents in ubuntu and tryed running it only to get the error 

"could not open the file /home/me/documents/blabla.run"
Ive only used linux for about 2 hours and i haven't really fully understood how everything works. Id be really great full if someone could help me out?

heres the steps im trying to attcheive... [https://help.ubuntu.com/community/UniChrome]("https://help.ubuntu.com/community/UniChrome")  . and i have no idea how to backup my xorg.conf. or "cd to the diredtory"?

Thanks in advance for any help at all.

---

### Post by PmDematagoda on 2008-01-11
Could you please post what driver you are trying to install?

---

### Post by GavinZac on 2008-01-11
backing up your xorg.conf is done like so:
*sudo cp /etc/X11/xorg.conf /etc/x11/xorg.conf.backup*

and you can "cd" (change directory) to a folder like so
*cd /whatever/the/folder/is/*

---

### Post by ttmw on 2008-01-11
> **GavinZac said:**
> backing up your xorg.conf is done like so:
*sudo cp /etc/X11/xorg.conf /etc/x11/xorg.conf.backup*
]

it might seems like a really stupid question and you'll have to excuse my newness but where do i type these commands?thanks

---

### Post by ttmw on 2008-01-11
> **PmDematagoda said:**
> Could you please post what driver you are trying to install?

VN800 UniChrome Pro integrated graphics for ubuntu. Its to run on fujitsu amilo pro v2030.

hope thats of some help

---

### Post by GavinZac on 2008-01-11
> **ttmw said:**
> it might seems like a really stupid question and you'll have to excuse my newness but where do i type these commands?thanks

thats ok, we were all new once.

click the applications menu, click Accessories, and then click "Terminal"

there are, of course, ways of doing these things graphically and with the mouse, but sometimes its quicker and easier for us both, if we tell you what to do via the terminal.

---

