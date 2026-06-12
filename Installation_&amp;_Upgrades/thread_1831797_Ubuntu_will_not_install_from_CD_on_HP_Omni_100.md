---
title: "Ubuntu will not install from CD on HP Omni 100"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by tgwilt on 2011-08-23
Hello all,

Due to a hardware crash I was forced to buy a new machine. Regrettably, I purchased an HP Omni 100 (all in one). It is a 64bit platform, and comes preloaded with (of course) Win7.

After burning the appropriate CDs (Ubuntu 10.04 LTS amd64 and Ubuntu 11.04 amd64) I began the journey. Now I _like_ to install Operating systems.

I was able to install 10.04 via wubi, but I don't want that. I want to repartition the drive and give Ubuntu 200G or so.

The problem is that once the CD boots, it hangs for a LONG time, eventually gets to the proper screen and even allows me to click on the Installation button. 

Then it hangs with a blank screen. Never installs anything. Same with 11.04. I am sure it can be solved, but I don't know how to do that right now.

The basic h/w is:

AMD AthelonII CPU
ATE Radeon 4700 on board video (I know...)
Realtek NIC 10/100
Ralink 802.11 b/n wireless

Any ideas?

Thanks in advance!

Tom

---

### Post by mörgæs on 2011-08-24
Hi, welcome to the fora.

For the blank screen problem, this thread is the best:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Mark Phelps on 2011-08-24
It's most likely NOT your onboard video.  I have a PC with an onboard 4290 and it works just fine.

You could try the Alternate CD.  While it has a text-based installation process, it ends up installing the same stuff.

---

### Post by tgwilt on 2011-08-26
I ended up having to install 10.04 LTS from the alternate cd, then used update manager to eventually get to 11.04.

Everything seems to work fine now, so thanks for the help!

---

### Post by mörgæs on 2011-08-27
Good, please mark the thread 'solved'.

---

