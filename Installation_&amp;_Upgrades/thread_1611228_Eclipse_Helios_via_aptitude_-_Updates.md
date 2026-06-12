---
title: "Eclipse Helios via aptitude - Updates?"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by CyberRascal on 2010-11-01
Hi, I just used

apt-get install eclipse-platform

to install Eclipse on my maverick. As I started it, I realized I got the second latest version of Eclipse - galileo. Still trying to wrap my head around using aptitude, so I was wondering - why is this? Did I use the wrong name? Is it simply because they haven't updated the repository? Thanks!

---

### Post by cipherboy_loc on 2010-11-01
I also noticed that.  After a bit of Googling, I noticed an outdated Launchpad repository ([https://launchpad.net/~eclipse-team/+archive/ppa](https://launchpad.net/~eclipse-team/+archive/ppa)), but nothing else. Thus I think your best bet is simply to download the archive of Helios from their web site and extract it in /opt, and add /opt/eclipse to your $PATH variable.

---

### Post by mikewhatever on 2010-11-01
Probably the second. Many packages in the repositories are not the newest version.

---

### Post by af207 on 2011-03-27
That's what i've been doing, installing it into /opt. But now i'm using the Netbook remix and the menu for helios no longer appears. But it still appears when I use galileo which had been install from the ubuntu software center. are there any workarounds to access the menu in helios? ...

---

### Post by af207 on 2011-03-27
Ok. I just found the answer. I was looking in the script to run Galileo as installed from the ubuntu software center. There was this line: 
export UBUNTU_MENUPROXY=0
Apparently this prevents its menu from integrating with the highly problematic "mutter". When i made a script with this line to start helios, it worked fine ...

---

