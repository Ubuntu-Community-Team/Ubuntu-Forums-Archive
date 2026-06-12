---
title: "Eee PC 900, can't upgrade flash"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by Naysayer on 2011-08-18
I'm pretty illiterate when it comes to computers, so hopefully someone can explain things in laymen terms. Basically I have an eee PC and a lot of things require me to upgrade my flash player, however I've been pulling my hair out trying to figure out how. Can someone please help me??

---

### Post by wojox on 2011-08-18
What version of Ubuntu are you using:

```
cat /etc/lsb-release
```

What flash version is installed:

```
dpkg -l | grep flash
```

---

### Post by Naysayer on 2011-08-18
When I typed the first one it said no such file or directory, so I might not be using ubuntu? I'm sure I sound stupid, I just ended up here when searching for answers.

and my flash version is adobe flash player 9.0.124.0-1asus1

---

### Post by wojox on 2011-08-18
Try:
```
uname -a
```

Are you using Xandros? If you using Firefox try [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

---

### Post by Naysayer on 2011-08-18
I'm not sure if I'm using Xandros. And when I tried flash-aid, it crashed and said it could not identify itself.

---

### Post by wojox on 2011-08-18
Okay go here [http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect) and download the .tar.gz package.

Then open you terminal and run:

```
ls -al
```

and post back what it says.

---

### Post by Naysayer on 2011-08-18
> **wojox said:**
> Okay go here [http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect) and download the .tar.gz package.

Then open you terminal and run:

```
ls -al
```and post back what it says.


When I tried to download it it said insufficient memory, please close yada yada.

When I went into the terminal and typed in what you said it just had a bunch of

User User  (some dates) and then various other things on the right hand side. Some of which were highlighted blue.

---

### Post by wojox on 2011-08-19
What about the 

```
uname -a
```

command? Lets see whose kernel is powering this thing.

---

### Post by Naysayer on 2011-08-19
> **wojox said:**
> What about the 

```
uname -a
```command? Lets see whose kernel is powering this thing.

"Linux asus-311547475 2.26.21.4-eeepc #2 Tue Jul 8 12:00:00 EDT 2008 i686 GNU/Linux"

That's what came up

---

### Post by Naysayer on 2011-08-19
bump                 .

---

### Post by steve11911 on 2011-08-21
Flashplayer 10.3 requires at least Ubuntu 9.10 or later.
Flashplayer 11.0,scheduled to be released this year, will require Ubuntu 10.04 or later.
Research indicates the kernel version your running dates to around june of 2007.Research also indicates that your chances of getting a modern Linux distro installed on your hardware are pretty good.Before deciding on a course of action;back up your data and do some digging.These should be helpful:

[http://forum.eeeuser.com/viewforum.php?id=43](http://forum.eeeuser.com/viewforum.php?id=43)

Please note that these 2 pages refer to different specific model number variants of the eee Pc 900.You should determine the exact model number you have and dig accordingly.

[http://ubuntuforums.org/showthread.php?t=1784977](http://ubuntuforums.org/showthread.php?t=1784977)

[http://ubuntuforums.org/showthread.php?t=1467749](http://ubuntuforums.org/showthread.php?t=1467749)

one more:

[http://www.eeebuntu.org/release/eeebuntu](http://www.eeebuntu.org/release/eeebuntu)

A good approach would be to  narrow the field then try several Live cd's and see which ones work best-then choose a winner for the full install.

I'll bet you can beat this bump...

To Naysayer: Kudo's dude...

---

