---
title: "Error installing software 12.04"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by hibeenicol on 2012-07-23
Hi all new to forums and new to Linux
 
I've managed to install ubuntu in an effort to get away form windows. Install went fine dual booting using windows installer. 
 
I then ran software updates yesterday and all installed fine. I then tried installing wine today using "apt-get install wine1.4" and it seems to be installing fine until the end and this is the error I'm getting
 
 
Sub-process /usr/bin/dpkg returned an error code (1)
 
 
All help appreciated thanks

---

### Post by oldfred on 2012-07-23
Welcome to the forums.

Have you just tried installing this:

#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

sudo apt-get install wine

Often there are meta-packages that install the most current version and its support files.

---

### Post by hibeenicol on 2012-07-23
Hi Oldfred thanks for getting back to me so quick. Seems like all is working how it should be thanks again.

---

