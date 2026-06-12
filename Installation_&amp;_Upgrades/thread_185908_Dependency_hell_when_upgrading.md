---
title: "Dependency hell when upgrading"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Wermut on 2006-06-01
When I try to upgrade from Breezy to Dapper Aptitude reports dozens of broken packages and many packages (nearly the whole KDE-desktop) are removed. It probably has something to do with packages installed from untrusted sources (for example kdelibs4c2a conflicts with kdelibs4c2). I was not able to resolve the problem in Aptitude; is there another possibility than a clean install?

---

### Post by aysiu on 2006-06-01
Dependency hell usually results from conflicting repositories.

You don't happen to have a mix of Breezy and Dapper repositories, do you?

In any case, a fresh list couldn't hurt:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then:
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by johnc4510 on 2006-06-01
Might not work, but have you tried:
sudo apt-get -f install
This fixes package problems, but I don't know if it will work for you.

---

### Post by Wermut on 2006-06-01
The proposed solutions did not work.

---

### Post by nicco on 2006-06-01
Hey, I had similar problems as you, but affecting other packages. Like you say it's caused by old packages I had installed earlier that conflicts with the new one.

I used the "smart" upgrade in Synaptic, and then manually went through the list of deleted packages and marked the ones I wanted to keep. Then it usually sorts itself out eventually.

---

### Post by lippel on 2006-06-01
I had similar problems with libstrutilsxx-0.7 and libstrutilsxx-0.7c2 (not sure about the exact names). apt-get -f install etc. didn't help at all, everything aborted because of the conflict. I started aptitude and uninstalled all libstrutilsxx packages from there, which worked.

---

### Post by Wermut on 2006-06-03
I followed nicco's advice and it worked. Synaptics seems to be somewhat smarter than aptitude when sorting out dependencies. I hope everything is allright now.

Btw: Does somebody know how to turn off the annoying effect when clicking an icon in Konqueror?

EDIT: Where has Gstreamer gone? Xine and arts don't work for me...

---

