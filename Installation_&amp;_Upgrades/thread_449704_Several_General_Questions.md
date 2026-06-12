---
title: "Several General Questions"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by davidbessire on 2007-05-20
Howdy.  i'm not a complete novice (used Ubuntu Dapper for about a year at work and have used Solaris and other Linux distros in the past) but perhaps someone can enlighten me.

i just got an HP a1740n with Intel Core 2 Duo (64 bit) processor and goofing with it has raised some questions:

1. Initially i tried to install Ubuntu 6.10 64 bit version; but, when the X login screen came up neither the keyboard or mouse were responsive.  Is this problem specific to 64 bit installs on HP?  Any way to correct it?  There are no such problems with 32 bit version.

2.  i'd like to make this box into a good development workstation with functional installations of a bunch of stuff (ftpd, postgres, development tools, etc.) *and* the nice desktop i'm used to from work.  But, the desktop install doesn't come with inetd, ftpd, or the like; and the server install doesn't come with the desktop.  If i do a server install, is getting the Gnome desktop too as easy as "apt-get install ubuntu-desktop", as some posts lead me to believe?

3. Is it advisable to install Feisty?  Stable?  What problems might arise?

4. After i installed the 32 bit version i ran Automatix which seemed to install several things i didn't request.  Any advice / opinions on Automatix?

Thanks in advance for any help or suggestions.

-db

---

### Post by benanzo on 2007-05-20
I can't answer the problem with the 64bit install, but I can say that I have installed the server version in the past, and just do:

```
apt-get install ubuntu-desktop
```

to install all the desktop stuff.  It works great.  I have even just done a minimal server install and then just compiled my own kernel (you don't need to) and done:

```
sudo apt-get install gnome-core gdm xserver-xorg xfonts-base
```

This will install a very minimal GNOME desktop with gnome-terminal, gedit, nautilus, metacity (I think Firefox too?), as well as the xserver and some fonts.  then you can just pick and choose everything else you want.

I've been using Feisty and have had no problems that I wouldn't have had in Edgy or Dapper.
I don't use automatix because I worry about installing software from unknown repos that could possibly break my APT catalogue.  Be careful.

---

