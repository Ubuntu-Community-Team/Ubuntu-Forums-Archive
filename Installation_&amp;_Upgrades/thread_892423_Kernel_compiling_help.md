---
title: "Kernel compiling help"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by Dragonatorul on 2008-08-17
Hello.

I have a Asus M3N78-EH motherboard and the SATA drive and network card are not recognized by the LiveCD edition of ubuntu 8.04. 
Here are some links to the bug reports [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231159]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231159")
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/231162]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/231162")

I learned that it's because of the kernel and I should recompile it. I tried to do so but without an internet connection. I downloaded it manually in windows and saved the master kernel thread page so I could follow it's instructions to the letter, which I did.

Problem is, even before I got to compiling the kernel I got a ton of errors. Here is what I had in the terminal window at the time (zip archived text file attachment).

Someone please help, I have to get my linux working properly before September for school. I've been looking for a way to fix it for two months now. Without an internet connection there's nothing I can do with it.

---

### Post by lorebett on 2008-08-18
Hi
did you install build-essentials?
it looks like you miss standard libraries...

---

### Post by Dragonatorul on 2008-08-21
I used the first command in the master kernel thread, if that's what you mean.


sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev

---

### Post by lorebett on 2008-08-22
mh... then you should have all you need to build the kernel... :confused:

---

### Post by Partyboi2 on 2008-08-22
I would double check that you have build-essential installed.
```
dpkg -l build-essential
```

---

