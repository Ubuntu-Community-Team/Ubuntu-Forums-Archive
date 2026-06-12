---
title: "cannot locate/install certain packages"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by jtmoney on 2007-02-14
hey guys,

i have a strange problem. i have an amd64 machine and installed the 64-bit version of kubuntu on it. i have enabled all the sources, however, whenever i tried to add the packages ivtv-source and mythtv, they could not be found.

figuring it was an issue with the packages not being available for the 64-bit version, i reinstalled the 32-bit version on the same machine and i have the same problem.

the install on my 32-bit laptop can see and install the packages fine.

i realize this is not a kubuntu forum, but i've been chatting with people all day on irc to no avail.

i've run sudo apt-get update, nothing seems to be working.

---

### Post by Kateikyoushi on 2007-02-15
Mythtv is in the multiverse repository did you enable it ?
Check it in System > administration > software sources.

---

### Post by JensenDied on 2007-02-15
well 1 google solved it
```

 deb http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse

```
add multiverse repositories to the end there

they might be in the kubuntu multiverse repositories, i dont know havnt looked, if they are not or they are shared these will work

source: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

enjoy

---

### Post by jtmoney on 2007-02-15
sorry i wasn't very clear, but i enabled all the repositories already. any other suggestions?

---

### Post by elemental666 on 2007-02-15
I believe the repo might be down at the moment, I'm trying to setup sun-java5 on mu ubuntu-server 6.06 and get the following:

```
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
```

---

### Post by Kateikyoushi on 2007-02-15
I do not know why won't the packages appear in the search but you could get them from packages.ubuntu.com .

---

### Post by elemental666 on 2007-02-15
Damnit, I'm a tard, I just deleted my sources.list while cleaning up old source lists...

Could someone post their official repo list?

---

### Post by Kateikyoushi on 2007-02-15
Well not really official but I am sure it will do. [LINK]("http://www.psychocats.net/ubuntu/sources")

Next time make backup of important files before editing them.

---

### Post by elemental666 on 2007-02-15
Thanks.

I did make backups, I just deleted them all...  it was stupid and doesn't happen often...

---

### Post by Kateikyoushi on 2007-02-15
By the way the server is reachable for me.

---

### Post by elemental666 on 2007-02-15
um, that sucks


for me

---

### Post by Kateikyoushi on 2007-02-15
Are you sure your sources.list is set up correctly ?
Did you try to search with aptitude ?

sudo aptitude search mythtv

---

