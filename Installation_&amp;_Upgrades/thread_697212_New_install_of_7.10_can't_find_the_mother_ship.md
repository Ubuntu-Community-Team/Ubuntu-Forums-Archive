---
title: "New install of 7.10 can't find the mother ship"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by JEBB on 2008-02-14
Today I installed 7.10, with partitioning, from a CD.  I had downloaded that Ubuntu version this week to my Mac and burned the iso using Toast 8.  I installed it on a Thinkpad R40 with partitioning so as to leave a partition with XP and a partition with Ubuntu.  All that seeemed to work fine until I tried to do the updates.  

I've got the Internet connection working as this message shows but there is no response when I have it check for updates or when I try to load a new program with Add/Remove.  

Suggestions?

---

### Post by taurus on 2008-02-14
Maybe you don't have all the repos enable in /etc/apt/sources.list so there is nothing to update.  Therefore, click the Preferences in Add/Remove and make sure there is a check mark in front of all the lines except the last one, Source code, and Cdrom in the window below.  Close that window and close down Add/Remove.  Now, run these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by JEBB on 2008-02-15
Tarus:  That was the answer!  Thanks.  But I didn't get to the terminal commands before the system starting updating.  

Also, I didn't uncheck CDrom before I clicked ok.  What damage will that cause?

---

### Post by taurus on 2008-02-15
Shouldn't be any damaged at all.  Just let it run until it finishes.

---

