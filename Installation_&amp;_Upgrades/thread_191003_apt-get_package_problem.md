---
title: "apt-get package problem"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by tobin8782 on 2006-06-06
ive got a problem with apt-get finding packages, sorry if this is a double thread but i think its a different issue to the other threads i could find. ive done a fresh install of 6.06, edited sources.list. apt-get update runs fine except it cant contact //security.ubuntu.com/ubuntu. i dont think its dns coz of this and i can ping the web by address name (eg [www.usyd.edu.au)](www.usyd.edu.au)). but my main concern is apt-cache search doesnt return any entry for build-essential or a couple other packages i have been looking for. thanks alot for any suggestions

---

### Post by aysiu on 2006-06-06
Can you post the exact output of this command? ```
sudo aptitude update
```

---

### Post by tobin8782 on 2006-06-06
this info is probably  necessary

my sources.list

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper multiverse
#deb [http://www.davidpashley.com/debian/irssi-sarge/](http://www.davidpashley.com/debian/irssi-sarge/) ./

---

### Post by tobin8782 on 2006-06-06
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to au.archive.ubuntu.com (1.0.0.0)]

and its still goin

---

### Post by tobin8782 on 2006-06-06
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done

thats it, cheers man

---

### Post by aysiu on 2006-06-07
Hm.

That "connection timed out" business makes me think you have some kind of weird proxy issue going on, and it has nothing to do with the repositories themselves.

Maybe these links might help:
[http://ubuntuforums.org/showthread.php?t=20344](http://ubuntuforums.org/showthread.php?t=20344)
[http://www.ubuntuforums.org/showthread.php?t=171126](http://www.ubuntuforums.org/showthread.php?t=171126)

---

### Post by tobin8782 on 2006-06-07
i dont think its a proxy issue, sorry i meant to say that in the first post. i dont use a proxy at all, i had to disable ipv6 in firefox. since i can ping and i can also apt-get install any packages that apt-cache search lists, thats whats led me to this conclusion, its just that alotta packages dont show up, also ones for enabling mp3 in rythymbox ie. gstreamer0.10-plugins-ugly.

cheers again

---

### Post by aysiu on 2006-06-07
Hm. What about [this](http://forums.debian.net/viewtopic.php?t=5249&)?

---

### Post by tobin8782 on 2006-06-07
cheers man, i set manual proxy to 85.133.25.7:80 and its good now except for one secturity address. but that doesnt matter, as long as i can build-essential im happy as. cheers buddy for ya time. if you know why this worked and can be arsed explainin it too me that would be choice,else cheers for ya time anyway. take it easy

---

