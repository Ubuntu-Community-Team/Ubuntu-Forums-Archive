---
title: "eeebuntu 3.0 using jaunty repos"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by nyktovus on 2011-02-27
so thats the current deal. i wanna update my software a bit, keep things working smooth. what repos should  i use (and no i dont wanna upgrade.. the NBR isnt close to what i have workin on my eeepc. )

currently my sources.list is:


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe


whats better:)??

---

### Post by sikander3786 on 2011-02-27
Jaunty is an out-dated release so the repositories won't work as they are on your system. You need to tweak them a little. See here.

[http://ubuntu4beginners.blogspot.com/2011/01/access-repositories-on-eol-end-of-life.html](http://ubuntu4beginners.blogspot.com/2011/01/access-repositories-on-eol-end-of-life.html)

You won't get any updates or secutiy patches though. All you get is already contained material in the repos.

And what you mean by 'better'? What are the choices?

---

### Post by ajgreeny on 2011-02-27
You will not be able to do that easily, I'm afraid as the support for 9.04, jaunty, has now lapsed and the repos you point to do not exist any more.  You can still get the OS and the packages that made it, but any updating is impossible without the repos.

---

### Post by nyktovus on 2011-02-27
so why cant i use the repose of a newer release.?

---

### Post by nyktovus on 2011-02-27
would that create a problem, or break the system. can i do an apt-get upgrade?
thanx

---

### Post by snowpine on 2011-02-27
eeebuntu is not Ubuntu. eeebuntu forums are here: [http://forums.auroraos.org/](http://forums.auroraos.org/)

Upgrade instructions for end-of-life Ubuntu releases (such as 9.04) [are detailed here]("https://help.ubuntu.com/community/EOLUpgrades"). No idea if this will also work for eeebuntu.

---

