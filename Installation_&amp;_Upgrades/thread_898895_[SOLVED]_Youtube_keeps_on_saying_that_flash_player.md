---
title: "[SOLVED] Youtube keeps on saying that flash player is not installed even though it is"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by shredder12 on 2008-08-23
I use 8.04 and have firefox 3 running...and 
Whenever i try to open and run a video in youtube it always says that either java is turned off or the flash player installed is not up to date...
though i have downloaded and installed flash player from its official site a couple of times..and guess what whenever i try to look for missing plugins in certain sites then it says that adobe flash player is missing..and when i click on the install it says that the non-free flash plugin is already installed...
Wht's the problem with it..
help me..

---

### Post by Cheesehead on 2008-08-23
> **shredder12 said:**
> ...i have downloaded and installed flash player from its official site a couple of times...

There's your first problem.

You should be installing from the repositories, of course, using Add/Remove (or Synaptic, if you know how).

_THE EASY ANSWER:_ (fastest)
Completely undo whatever install you have, and redo it *the right way* from the repos.
If you don't know how to undo it, the you *really* shouldn't be doing it.

_THE GEEK ANSWER_
How, exactly, did you install it? Step by step, show us the commands you used and the system's response.

---

### Post by Sef on 2008-08-23
> You should be installing from the repositories, of course, using Add/Remove

Applications > Add/Remove > show: All Available Applications > Search: adobe flash > click on top box (Macromedia Flash Plugin) > apply changes > apply > close.

---

### Post by aysiu on 2008-08-23
Can you paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? Warning: the first command may take a couple of minutes to execute: ```
sudo updatedb
locate libflash
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
cat /etc/lsb-release
uname -m
cat /etc/apt/sources.list
```

---

### Post by shredder12 on 2008-08-24
> **Sef said:**
> Applications > Add/Remove > show: All Available Applications > Search: adobe flash > click on top box (Macromedia Flash Plugin) > apply changes > apply > close.

Hey thanks it works now...

---

