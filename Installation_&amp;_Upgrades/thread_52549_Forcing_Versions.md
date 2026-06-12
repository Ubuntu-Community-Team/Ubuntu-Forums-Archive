---
title: "Forcing Versions"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by mamato on 2005-07-28
Hi guys, it's me again :D
At the moment, I have add KDE 3.4.2 to my repository. But when I install the kde programs, they use the kde 3.4.0 version. Is there any way to force the system to install kde version 3.4.2?
thanks a lot..

---

### Post by Xian on 2005-07-28
Yes, you can pin those packages to that apt will prefer them.
What repositories are you using for KDE 3.4.2?

Did you read this [THREAD](http://ubuntuforums.org/showthread.php?t=52499)?

---

### Post by mamato on 2005-07-28
Yes, I have used the link on that post, but my sistem still install the 3.4.0 version?
Any clue about it?

---

### Post by Xian on 2005-07-28
[QUOTE=mamato]Yes, I have used the link on that post, but my sistem still install the 3.4.0 version?
Any clue about it?[/QUOTE]

Let's try these steps:

1. Add the lines below to your /etc/apt/sources.list file.
Remove any similar text that mentions the kubuntu.org repo.

```
deb http://kubuntu.org/hoary-kde342 hoary-updates main
deb-src http://kubuntu.org/hoary-kde342 hoary-updates main
```
2. Open (or create) the file /etc/apt/apt.conf

3. Enter the text below into the apt.conf file:

```
APT::Default-Release "hoary-updates";
```
4. Check to see if you have an /etc/apt/preferences file.
If so, remove any text that mentions pinned repositories.

5. Open a terminal and enter the following:

```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```

---

