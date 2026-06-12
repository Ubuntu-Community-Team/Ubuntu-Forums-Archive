---
title: "installing firefox 3 beta3?"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by linksolo74 on 2008-02-15
I tried installing the backport in synaptic, but i found that it isn't the newest version (it is firefox 3 beta3pre). My question is: how do i install beta 3? I downloaded the source code and have ran it from there, but i want to install it like i would a .deb file. Is there a easy way to do this with the source code? Or is there a .deb file floating around somewhere? Sorry i'm a NOOb, but i have never installed source code before. I normally just install from synaptic or download the .deb file from [www.getdeb.com](www.getdeb.com), but neither of those work this time.

---

### Post by Partyboi2 on 2008-02-15
Maybe [this]("http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710") will work for you.

---

### Post by linksolo74 on 2008-02-16
ehh..... i'm not sure i like the sound of what it is doing. sounds like if it could make some problems when i get rid of it, when firefox 3.0 final comes out. I think i'll look for someother way. Thanks for the suggestion though.

---

### Post by Partyboi2 on 2008-02-16
google around you might find something else. If not you could just wait for the repos to be updated or until Hardy is released

---

### Post by nilarimogard on 2008-02-16
Actually firefox 3 beta 3 is in the repos for quite some time, you just have to enable Hardy repos, and sudo apt-get install firefox. That's not beta3pre anymore for a few days now :)

---

### Post by Partyboi2 on 2008-02-16
If you do enable the hardy repo to install firefox3 I would suggest  you disable it afterwards as having repo's from different ubuntu dist could cause system breakages

---

### Post by nilarimogard on 2008-02-16
Yes of course. Sorry i forgot to say that. Everyone wanting to install Hardy software, enable Hardy repos, install what you want and then disable it.

---

### Post by linksolo74 on 2008-02-16
How do i go about enabling hardy repos? I don't see that option in synaptic. Is there something i need to add?

---

### Post by nilarimogard on 2008-02-16
Click Add in Software Sources, and add this: deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main

---

### Post by linksolo74 on 2008-02-16
thanks, but it seems that if i install it that i will have to get rid of firefox 2 and songbird. I would like to keep these apps, but when i click mark for install it says to be removed firefox, songbird, sun-java 6 plugin. Is there a way to keep these apps while still installing FF3 B3?

---

