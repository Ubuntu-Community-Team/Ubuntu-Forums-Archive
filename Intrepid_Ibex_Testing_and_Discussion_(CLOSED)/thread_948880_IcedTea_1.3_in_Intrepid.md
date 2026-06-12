---
title: "IcedTea 1.3 in Intrepid?"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jblackhall on 2008-10-15
I just read that [IcedTea 1.3 was released today]("http://www.phoronix.com/scan.php?page=news_item&px=Njc4Nw").  I know a version of it is bringing open-source Java to Intrepid.  I was just curious if this new version was set to make it in?  I don't know where to check for that, and I haven't paid attention to whether it they've been using a pre-release version already in Intrepid.  Looks like it's got some nice new features.  If they haven't been tracking development, I think it's probably unlikely to make it at this point.

---

### Post by jblackhall on 2008-10-16
I'll take that to mean no one knows then

---

### Post by kj74 on 2008-10-16
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[https://lists.ubuntu.com/archives/intrepid-changes/](https://lists.ubuntu.com/archives/intrepid-changes/)
[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008781.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008781.html)

---

### Post by Darrena on 2008-10-16
It should be available soon:

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008781.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008781.html)

---

### Post by inportb on 2008-10-17
Whoa, I think it just hit the repos. It's upgrade time =p

---

### Post by SnakeHips on 2008-10-18
Hi ,I have AMD64 on Intrepid (kernel 2.6.27-7) and added OpenJDK as follows:

Applications / Add/Remove applications:
OpenJDK java 6 runtime
OpenJDK java 6 webstart

After a reboot I checked in terminal and thus...

pete@desk:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)
pete@desk:~$ 

[www.java.com](www.java.com) reports NO java installed and [www.runescape.com](www.runescape.com) (what I want it for) the same.

Any ideas ?

---

### Post by inportb on 2008-10-18
Did you install the browser plugin?

---

### Post by kj74 on 2008-10-18
> **SnakeHips said:**
> Hi ,I have AMD64 on Intrepid (kernel 2.6.27-7) and added OpenJDK as follows:

Applications / Add/Remove applications:
OpenJDK java 6 runtime
OpenJDK java 6 webstart

After a reboot I checked in terminal and thus...

pete@desk:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)
pete@desk:~$ 

[www.java.com](www.java.com) reports NO java installed and [www.runescape.com](www.runescape.com) (what I want it for) the same.

Any ideas ?

You need web browser plugin but i doubt runescape(it is some kind of game?) will work.

---

### Post by SnakeHips on 2008-10-18
> **inportb said:**
> Did you install the browser plugin?

Well I tried to add "icedtea plugin" from add/remove apps but it complains about "fix broken packages first" ??  So i'll take out openJDK and try again...

---

### Post by SnakeHips on 2008-10-18
> **kj74 said:**
> You need web browser plugin but i doubt runescape(it is some kind of game?) will work.

Its worked on every other version since Dapper and currently works fine on my Hardy install. Just seems Intrepid is being a little troublesome with the Java ??

---

### Post by inportb on 2008-10-18
What I did:
```
sudo apt-get install openjdk-6-jdk icedtea6-plugin
```

If you don't need the JDK:
```
sudo apt-get install openjdk-6-jre icedtea6-plugin
```

You have broken packages... how did that happen?

---

### Post by taavikko on 2008-10-18
> **SnakeHips said:**
> Its worked on every other version since Dapper and currently works fine on my Hardy install. Just seems Intrepid is being a little troublesome with the Java ??

Actually tested icedtea6-plugin on runescape, and it works, at least on my installation.

Too bad that openjdk is not working where it needs to be,
In my net Bank (sampopankki) they merged with Danish Danskebanken and switched to java, as security reasons. Now it's troublesome to have it working :(

Note: i don't play runescape, just tested it to see if it works ;)

---

### Post by SnakeHips on 2008-10-18
It's working fine now after three or four installs and removes! 

And i'm just using Runescape for testing purposes as well ;-) lol

pete@desk:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)
pete@desk:~$

---

