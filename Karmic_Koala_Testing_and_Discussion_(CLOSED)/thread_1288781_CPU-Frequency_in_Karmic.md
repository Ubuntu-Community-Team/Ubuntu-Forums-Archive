---
title: "CPU-Frequency in Karmic"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thecow on 2009-10-11
I use the cpu-frequency scaling monitor a lot.  In previous versions of Ubuntu I was able to select a different frequency and it would stay at that frequency.  I can do that in Karmic except it asks for my password almost every time I want to change the frequency.  This is extremely obnoxious however I cant figure out a way to have it just have root privileges.  I remember in previous versions of ubuntu I would type:

```
sudo dpkg-reconfigure gnome-applets
```

However this no longer has any effect in Karmic.

Any help would be appreciated,
thank you

---

### Post by solnyshok on 2009-10-12
I also need the solution

---

### Post by daetsy on 2009-10-12
Me too

---

### Post by emarkay on 2009-10-12
Looks like a bug needs to be filed - I haven't used this so I really can't elaborate on the report.

---

### Post by cornflake000 on 2009-10-14
Have you tried this:

in /etc/rc.local

add this.... 

cpufreq-selector -c 0 -g performance
cpufreq-selector -c 1 -g performance

Make sure exit 0 is the last line.

Add another line for each cpu core or kernel eg. -c 3 -g etc.

It has always worked for me in Jaunty or Karmic.

---

### Post by thecow on 2009-10-14
What does that do?  I hate the governors.  I pick the frequency I want, the problem is that now it asks me for my password if I want to change it

---

### Post by solnyshok on 2009-10-14
tried it, did not help. Still need to input password for frequency change

---

### Post by biji on 2009-10-14
in jaunty.. i can go to Administration -> Authorization
find org.cpufreq then check always allow action
but in karmic no such org.cpufreq :(

---

### Post by TrueTom on 2009-10-19
[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/455694]("https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/455694")

---

### Post by mc4man on 2009-10-25
For the moment this should take care of the cpu applet and some other auth... if desired.

Note some of the edits

[http://ubuntuforums.org/showthread.php?t=1299820](http://ubuntuforums.org/showthread.php?t=1299820)

---

