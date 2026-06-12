---
title: "New to Ubuntu and need help!"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by icccrossover on 2006-10-24
1. I am trying to view streaming video off the internet but some sites only recongnize windows media player.  I need to install something that will play these videos and I heard the Mplayer is the way to go but I have no idea how to download the right one or where to get it from or anything.

2. I'm also trying to add/remove programs, when I add programs I can't find them on my computer.  Where does it save them to?  How do I run them?

---

### Post by bulldog on 2006-10-24
Try synaptic System-->Administration-->Synaptic

This is the standard packagemanager.

Do a search for mplayer or totem or xine there are more.

You can try Automatix,this can install a bunch of programs for you at your choice.
Including java,flash-player and your video drivers.

Look here,

[http://www.getautomatix.com/](http://www.getautomatix.com/)

And choose automatix2

---

### Post by icccrossover on 2006-10-25
Dude, seriously, I have no idea how to install automatix.  I really am new to all this.  Also I did the System/administration/synaptic and I installed the kmplayer but now I can't find it or use it.  I'm confused.

---

### Post by gerowen on 2006-10-25
> **icccrossover said:**
> Dude, seriously, I have no idea how to install automatix.  I really am new to all this.  Also I did the System/administration/synaptic and I installed the kmplayer but now I can't find it or use it.  I'm confused.

Just run the command "kmplayer" from the command line or anywhere.  If you want to make a desktop icon for it, just make one, and in the "command" box, set it to "kmplayer".  When a Linux program is installed properly, it puts what is called a symbolic link in one of a couple of folders that are set up for them, and this makes it possible to just run the command "kmplayer" without having to hunt down where it actually installed to.

---

### Post by bulldog on 2006-10-25
> **icccrossover said:**
> Dude, seriously, I have no idea how to install automatix.  I really am new to all this.  Also I did the System/administration/synaptic and I installed the kmplayer but now I can't find it or use it.  I'm confused.


If you read carefully you can I guess.:D 

It's not that hard to do.

---

### Post by Elshadii on 2006-10-25
> **icccrossover said:**
> Dude, seriously, I have no idea how to install automatix.  I really am new to all this.  Also I did the System/administration/synaptic and I installed the kmplayer but now I can't find it or use it.  I'm confused.

This is a complicated issue to be honest.  Try googleing for some howto's by searching:

install mplayer ubuntu

I found this one:

[http://www.debianadmin.com/install-mplayer-ubuntu.html](http://www.debianadmin.com/install-mplayer-ubuntu.html)

This howto has serious drawbacks for a new user because it asks you to edit your sources.list file without showing you how.  Don't do that until you are comfortable with your skill level.  Go to this site and it will tell you how to add additional repositories by showing you how.

[http://ubuntulinuxhowto.blogspot.com/2006/06/how-to-add-extra-repositories.html](http://ubuntulinuxhowto.blogspot.com/2006/06/how-to-add-extra-repositories.html)

You can also add repositories through the package program called Synaptic it's under System > Administration > Synaptic Package Manager

---

