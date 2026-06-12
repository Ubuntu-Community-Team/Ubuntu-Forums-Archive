---
title: "Pre-upgrade questions"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by musicman2059 on 2005-10-13
I'm all excited about upgrading my computer to Breezy, but before I jump right in I want clarification on a few things first.

1. The computer I'm planning on upgrading from Hoary to Breezy is without an Internet connection.  I looked over the upgrade instructions in the wiki and saw that that the first step was to apt-get the base system and desktop packages.  I'm assuming that for this computer I'm at a loss for this in particular, and it makes it kind of unnerving for me because as I've heard, upgrading without these two packages can cause much more problems than upgrading with them. 

2. Currently, I have XFCE installed as my desktop environment and use it as my default.  Will my XFCE installation be affected by the upgrade?

---

### Post by GreenHawkIA on 2005-10-14
If you need to upgrade on a computer sans Internet, you can upgrade most of the base packages from the Install CD.  Use:
```
sudo apt-cdrom add
```
Then edit your repositories list:
```
sudo gedit /etc/apt/sources.list
```
In front of every repository except the first one, put two little ## marks, so that they won't be used (commenting).  Make sure your first source is:
> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
I suggest while you're at it, just in case you ever connect this computer to the internet - switch your repositories list to breezy - just change everywhere it says "hoary" to say "breezy".
Then:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Hope this helps!

---

### Post by GreenHawkIA on 2005-10-14
Oh and PS, I don't know the answer to your XFCE question, but I would suggest downloading the .deb packages you need to a CD-ROM, then going to a command line and using the sudo -i dpkg command to install the latest of what you need.
Maybe somebody smarter than me can help you with that.

---

### Post by graabein on 2005-10-14
I also have some pre-upgrade questions. From the [wiki]("https://wiki.ubuntu.com/BreezyUpgradeNotes"): ***Resolve any conflicting packages. Conflicting packages could possibly stop the upgrade, even at a very inconvenient stage.***

So how do I search for any conflicting packages on my system?

:KS

---

### Post by GreenHawkIA on 2005-10-14
Basically - the way I took this, and I am no Ubuntu expert - is that if you've installed anything yourself that is not from the Ubuntu repositories, you should remove it before upgrading to Breezy, due to a risk of conflicts.  The most common of these would be the latest version of Firefox, where there might be a conflict between Firefox and Ubuntu's version of Firefox.  However, if you never installed anything except with apt-get or Synaptic, you should be fine, also, if there isn't a version of it in the Ubuntu repos, you should be fine as well.
Also, btw > using the sudo -i dpkg command above should have read the sudo dpkg -i.  Dsylexics of the World - Untie!

---

