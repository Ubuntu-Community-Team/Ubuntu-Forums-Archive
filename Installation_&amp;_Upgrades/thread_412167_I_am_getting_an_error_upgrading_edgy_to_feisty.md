---
title: "I am getting an error upgrading edgy to feisty"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by Happy_Man on 2007-04-17
Hey everyone,

I decided to beat the server slowdown that will inevitably occur come release, by upgrading my system today! Unfortunately, it won't let me. I went ahead and typed in 

```

update-manager -d

```

and it showed up, and I clicked the upgrade button. So far so good. Then it gets to the second step, and throws this error:

> 
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)


It then "restores my system to its original state" and exits the upgrader. I've tried three times. Same error, same place. What should I do?

---

### Post by Kuropi on 2007-04-17
That is odd. I did the same thing as you and I was able to download 7.10 without a problem.

---

### Post by St. Coin on 2007-04-17
I'm having the same problem:

Error During update:
```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
```

---

### Post by Happy_Man on 2007-04-17
Wow....maybe their servers are down?

---

### Post by j_dog on 2007-04-17
try this, it's working for me right now.

```

update-manager -c  -d

```

---

### Post by St. Coin on 2007-04-17
> **j_dog said:**
> try this, it's working for me right now.

```

update-manager -c  -d

```

Gives me the same error. :(

---

### Post by Happy_Man on 2007-04-18
Same here...saame error.

---

### Post by Voland on 2007-04-18
It seems to me like problems with mirror. Try to use another one or main server.

---

### Post by TimelessRogue on 2007-04-18
Good morning ...

I used a different method (see [http://ubuntuforums.org/showthread.php?t=412477](http://ubuntuforums.org/showthread.php?t=412477)) but at time have gotten the same message when doing the updates/upgrades ... turned out to be my local server was down periodically.  As was already suggested, it might also be a case of the mirror being quite busy so you could try another one (I use "main" successfully.)

---

### Post by Happy_Man on 2007-04-18
Bump

---

### Post by gsyoungblood on 2007-04-18
What kind of hardware are you using?

I've also had similar problems. I'm using a thinkpad t43p. Changing to the wireless interface is what it took to get things working. ([http://ubuntuforums.org/showthread.php?p=2477407#post2477407](http://ubuntuforums.org/showthread.php?p=2477407#post2477407))

It appears the wired NIC is a tg3 (Tigon3). By some chance, is that what your system has?

---

### Post by gsyoungblood on 2007-04-18
Switching to wireless did not resolve the problem after all.

I posted a message to the networking forum.
[http://ubuntuforums.org/showthread.php?p=2478501#post2478501](http://ubuntuforums.org/showthread.php?p=2478501#post2478501)

---

### Post by lotacus on 2007-04-18
> **Kuropi said:**
> That is odd. I did the same thing as you and I was able to download 7.10 without a problem.

heh, are you a time traveler?

---

### Post by ALIENDUDE5300 on 2007-04-19
> **Happy_Man said:**
> Hey everyone,

I decided to beat the server slowdown that will inevitably occur come release, by upgrading my system today! Unfortunately, it won't let me. I went ahead and typed in 

```

update-manager -d

```

and it showed up, and I clicked the upgrade button. So far so good. Then it gets to the second step, and throws this error:



It then "restores my system to its original state" and exits the upgrader. I've tried three times. Same error, same place. What should I do?

I think you have to wait until the final version is released...

---

### Post by jfinkels on 2007-04-19
You can try just changing all the entries in your /etc/apt/sources.list file so that everywhere you see 'edgy', just change the word to 'feisty', and then do "sudo aptitude update && sudo aptitude upgrade".

---

### Post by ModusOperandi on 2007-04-21
I was getting that error, as well (or at least something like it, may have had a different URL, but the gist was the same.) I went into Synaptic, opened the Repositories, and unchecked all third-party repos, and the universe, multiverse, and restricted boxes. I'm upgrading right now.

---

### Post by therr on 2007-04-25
Like others, I experienced this error.  The fix required in my case was to disable many of the 'extra'  repos I had enabled or added by hand to /etc/apt/sources.list.

My upgrade is in progress and the only repos that I have enabled are as follows:
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main

---

