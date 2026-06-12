---
title: "broken dependencies"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by arnaudj on 2008-11-29
Hello people,
I have a laptop, I wanted to install easycam2 to be able to use my cam, but i got stuck. I'm going in circle... here are my dependencies:

```

arnaud@labtop:~$ sudo apt-get -f install -f easycam2-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  easycam2-core: Depends: build-essential but it is not going to be installed
                 Depends: python-xml but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
arnaud@labtop:~$ sudo apt-get -f install -f build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  easycam2-gtk: Depends: easycam2-core but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
arnaud@labtop:~$ sudo apt-get -f install -f python-xml
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  easycam2-gtk: Depends: easycam2-core but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
arnaud@labtop:~$ sudo apt-get -f install -f g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  easycam2-gtk: Depends: easycam2-core but it is not going to be installed
  g++: Depends: g++-4.3 (>= 4.3.1-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
arnaud@labtop:~$ sudo apt-get -f install -f g++-4.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  easycam2-gtk: Depends: easycam2-core but it is not going to be installed
  g++-4.3: Depends: libstdc++6-4.3-dev (= 4.3.2-1ubuntu11) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
arnaud@labtop:~$ sudo apt-get -f install -f  libstdc++6-4.3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  easycam2-gtk: Depends: easycam2-core but it is not going to be installed
  libstdc++6-4.3-dev: Depends: g++-4.3 (= 4.3.2-1ubuntu11) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
arnaud@labtop:~$ sudo apt-get -f install -f  dpkg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dpkg-dev: Depends: patch (>= 2.2-1) but it is not going to be installed
            Recommends: build-essential but it is not going to be installed
  easycam2-gtk: Depends: easycam2-core but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
arnaud@labtop:~$ sudo apt-get -f install -f  easycam2-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
easycam2-gtk is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  easycam2-gtk: Depends: easycam2-core but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
arnaud@labtop:~$ 

```

I cannot install anything else after that.
neither g++... It's driving me nuts.

If you need other screenshot, anything, please, let me know.
I will appreciate any comment!
thanks a lot.

---

### Post by taurus on 2008-11-29
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install easycam2-core
```

---

### Post by arnaudj on 2008-11-29
thanks a lot taurus!!
i had to find my install CD (not so easy).
but it was the hardest thig i had to do.
it works perfect!

---

### Post by ibogi on 2009-11-18
I had the same problem but couldn't fix it with this method. 

There were two versions of the same package in the repositories. When I switched from using repositories in Serbia to using main repositories, then it worked without problem. I think there was something bad with serbian repositories.

---

### Post by p4g4n on 2010-04-10
Hello everyone,
    I'm not sure if what I'm about to say deserves a separate thread, but quick search led me to this thread so here we go:
    I'm Ubuntu user from Serbia also... and I had few problems in the past with broken (unmet ?) dependencies. The matter of fact, I just had one, few minutes ago so I finally decided to write something about this issue.
    The last one I had was when I "installed" kohana 3 in my web folder. I needed curl installed. I installed it via apt-get and then went to synaptic to grab php5-curl. Found it and when I marked it for install it said that the system had problems with dependencies. As I already knew the solution, I went to Settings/Repositories and changed my DEFAULT repository from Serbia to Main Site repo. After reload, everything worked fine.
    Now, as I have mentioned earlier, this has happened before... and will happen again. I was doing some small research on most popular Linux distros in Serbia, and found out that,of course, Ubuntu was the most popular. So, from my point of view, what that means is that all newcomers (in Serbia) will have the same problem which MIGHT discourage them from using Ubuntu as they still have a lot to learn about the system. And this issue is not the standard one (related to some software bug or trick).
    As I know, the Serbian repo server is located in Belgrade on the Electro-techincal sciences faculty(literal translation sry) and what is causing this problems... I don't know. There are some difficulties obviously like, few years ago, server didn't work on weekends :) . We can all agree that this is in some way strictly local issue and that we must take into account the faculty administration and management and what not... I'm not going into that stuff.
    Just wanted to let you know about this, in case if you're in position to do something about that.

P.S. Sorry for long post and possibly bad grammar

---

### Post by km0r3 on 2010-04-11
> **p4g4n said:**
> Hello everyone,
    I'm not sure if what I'm about to say deserves a separate thread, but quick search led me to this thread so here we go:
    I'm Ubuntu user from Serbia also... and I had few problems in the past with broken (unmet ?) dependencies. The matter of fact, I just had one, few minutes ago so I finally decided to write something about this issue.
    The last one I had was when I "installed" kohana 3 in my web folder. I needed curl installed. I installed it via apt-get and then went to synaptic to grab php5-curl. Found it and when I marked it for install it said that the system had problems with dependencies. As I already knew the solution, I went to Settings/Repositories and changed my DEFAULT repository from Serbia to Main Site repo. After reload, everything worked fine.
    Now, as I have mentioned earlier, this has happened before... and will happen again. I was doing some small research on most popular Linux distros in Serbia, and found out that,of course, Ubuntu was the most popular. So, from my point of view, what that means is that all newcomers (in Serbia) will have the same problem which MIGHT discourage them from using Ubuntu as they still have a lot to learn about the system. And this issue is not the standard one (related to some software bug or trick).
    As I know, the Serbian repo server is located in Belgrade on the Electro-techincal sciences faculty(literal translation sry) and what is causing this problems... I don't know. There are some difficulties obviously like, few years ago, server didn't work on weekends :) . We can all agree that this is in some way strictly local issue and that we must take into account the faculty administration and management and what not... I'm not going into that stuff.
    Just wanted to let you know about this, in case if you're in position to do something about that.

P.S. Sorry for long post and possibly bad grammar
Actually, there's not always **the one** solution.

[http://kubuntuforums.net/forums/index.php?topic=3096272.0](http://kubuntuforums.net/forums/index.php?topic=3096272.0)

Just my few cents.

---

