---
title: "uninstall gaim (Xubuntu) wants to uninstall xubuntu-desktop"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by delirium83 on 2007-01-30
Hi,
I want to replace Gaim by SIM and therefore I want to uninstall it for not having unused applications wasting disc space :D
When I select the Gaim-Package for removal in Synaptics I get a message that xubuntu-desktop needs to be removed first.

Can Gaim be removed without removing xubuntu-desktop first and if it's possible: how ?

---

### Post by an.echte.trilingue on 2007-01-30
xubuntu-desktop is just a metapackage, meaning that it contains no data but simply depends on all of the elements of the xubuntu desktop for the initial installation.  You can safely remove it.

Take care,
-mat

---

### Post by zeddock on 2007-01-30
On a fresh Ubuntu 6.10, I went through and uninstalled a lot of things I did not want... like Evolution and Gaim.   Now when I rebooted there are no icons, taskbars, or anything else I can click on.

I did see a notice during the process that my actions would also uninstall Nautilus.

How can I get the desktop back please?

zeddock

---

### Post by hal10000 on 2007-01-30
@zeddock:
Maybe you unstalled alittle bit too much. reinstall nautilus and gnome-panel from the console (press CTRL-ALT-F2 to log into a console): [COLOR="Red"]sudo apt-get install nautilus gnome-panel[/COLOR]

---

### Post by zeddock on 2007-01-30
> **hal10000 said:**
> @zeddock:
Maybe you unstalled alittle bit too much. reinstall nautilus and gnome-panel from the console (press CTRL-ALT-F2 to log into a console): [COLOR="Red"]sudo apt-get install nautilus gnome-panel[/COLOR]

I fear I did!  hehehe.  Oh well! This is how we learn, right!?

It is happy about nautilus. I tried the above apt-get and it said 0 updated, 0 deleted, and so on...

I used: 
sudo dpkg-reconfigure xserver-xorg
sudo aptitude install ubuntu-desktop

..and a few others.  No joy.

I think that xserver is OK because I do get the tan background, so isn't that a good sign that the server is serving GUI of some sort?

Although I am new to linux, it seems that it just does not know what to put on this display for panels, menus, etc...   these are things that would change with profiles, right?

So wouldn't it be someplace in those areas?

BTW, when I used sudo aptitude install ubuntu-desktop, there was a lot of activity and getting and installing. i saw a few things flash by which said python and evolution, etc...

So I am thinking I did uninstall too much.  SO now it should be back installed, right?

any other thoughts?

zeddock

---

### Post by zeddock on 2007-01-30
> **hal10000 said:**
> @zeddock:
Maybe you unstalled alittle bit too much. reinstall nautilus and gnome-panel from the console (press CTRL-ALT-F2 to log into a console): [COLOR="Red"]sudo apt-get install nautilus gnome-panel[/COLOR]

I fear I did!  hehehe.  Oh well! This is how we learn, right!?

It is happy about nautilus. I tried the above apt-get and it said 0 updated, 0 deleted, and so on...

When I used sudo aptitude install ubuntu-desktop, there was a lot of activity and getting and installing. i saw a few things flash by which said python and evolution, etc...
But with a reboot it was a blank desktop again.

I used: 
sudo dpkg-reconfigure xserver-xorg
sudo aptitude install ubuntu-desktop

..and a few others.  No joy.

I think that xserver is OK because I do get the tan background, so isn't that a good sign that the server is serving GUI of some sort?

Although I am new to linux, it seems that it just does not know what to put on this display for panels, menus, etc...   these are things that would change with profiles, right?

So wouldn't it be someplace in those areas?

So I am thinking I did uninstall too much.  SO now it should be back installed, right?

any other thoughts?

zeddock

---

### Post by hal10000 on 2007-01-30
You said you installed ubuntu-desktop, but you are using xubuntu, right?
Then i guess the package to install might rather be xubuntu-desktop

---

### Post by hal10000 on 2007-01-30
You said you installed ubuntu-desktop, but you are using xubuntu, right?
Then i guess the package to install might rather be xubuntu-desktop

---

### Post by zeddock on 2007-01-30
> **hal10000 said:**
> You said you installed ubuntu-desktop, but you are using xubuntu, right?
Then i guess the package to install might rather be xubuntu-desktop


I am on Ubuntu and installed Unbuntu.  Never on Kbuntu (Which is ubuntu with KDE desktop, right?

Man!  I wondered why you asked.  With my tail tucked between my legs I will go find a proper thread to ask this question.

Sorry folks.

zeddock

---

