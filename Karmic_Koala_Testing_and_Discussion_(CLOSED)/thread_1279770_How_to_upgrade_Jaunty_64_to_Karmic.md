---
title: "How to upgrade Jaunty 64 to Karmic"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Guy Sibley on 2009-10-01
Hey. 
I have been trying to locate Karmic Koala update in my update manager but I cant find any distro updates.  In fact, I updated earlier this morning (and at least once a week) but update manager still says, and has said for a few days, that I last updated 22 days ago. What is going on? I have followed multiple sets of instructions on how to perform this update, IT HAS NOT WORKED. plz help.
Thank you all so much.:confused:

---

### Post by Bachstelze on 2009-10-01
```
sudo sed -i s/jaunty/karmic/g /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Guy Sibley on 2009-10-01
Thank you!

---

### Post by Guy Sibley on 2009-10-01
So  the upgrade to Karmic caused my computer not crash. Not kidding, I have been spending the last 5 hours or so reinstalling and upgrading from my only disk which was hardy heron. why did this happen? I understand that Karmic is still in Alpha and I still want to help test it and look for bugs, but this was very odd.

---

### Post by louieb on 2009-10-01
> **Guy Sibley said:**
> upgrade to Karmic caused my computer not crash. Not kidding, ... but this was very odd.

Why was it odd?  Upgrades do that. Upgrades to an Alpha version just do it more often.  Just like you - had to learn the hard way. Backup before upgrading. I use   [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522")  Take an image of your install 1st - saves you lots of work.

---

