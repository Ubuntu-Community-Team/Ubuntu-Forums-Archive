---
title: "How to install Winrar"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by zhoujielun on 2013-02-24
Hello!
I'm new and want to install winrar on ubuntu. I have downloaded the linux version of winrar but don't know how to install it.
I have tried two terminal commands: 
"sudo aptitude update && sudo aptitude install rar unrar"
(computer didn't find the command)
and "sudo apt-get install unrar"
(computer said that he can't install unrar"
What have I done wrong?? It's the first time i'm installing a programm on ubuntu.

---

### Post by oldos2er on 2013-02-24
I think if you substitute "apt-get" for "aptitude," which is no longer installed by default, the command should work. ```
sudo apt-get update && sudo apt-get install rar unrar
```

---

### Post by zhoujielun on 2013-02-24
> **oldos2er said:**
> I think if you substitute "apt-get" for "aptitude," which is no longer installed by default, the command should work. ```
sudo apt-get update && sudo apt-get install rar unrar
```

My computer is still saying that he can't install rar and unrar....

---

### Post by zhoujielun on 2013-02-24
> **istealth shadow said:**
> have you tried opening the tarball then clicking on an installer?

lol... i spent a whole hour figuring that out ..:p

what is tarball?

---

### Post by MAFoElffen on 2013-02-24
Easiest is xarchiver, that includes rar as one of it's formats. Basic gui, but is opensource and free.

Next is unrar-free... unrar and rar are non-free, but those will install and run for 40 days or so, then you have to pay to register it to keep them functioning. unrar-free is from the same author, works on most rar archives, but not the newer format rar's. But then again, is free.

I used rar and unrar until it ran out... then uninstalled it and went to xarchiver.

I still have WinRar on one of my Windows installs, that I paid/registered years ago. I always have a shared dataspace that I use for both Windows, Linux and Unix data >> on a shared nfts filesystem or on NAS.

---

### Post by varunendra on 2013-02-24
> **istealth shadow said:**
> have you tried opening the tarball then clicking on an installer?
Nevermind that, you don't need tarballs.

FYI, they are third party packages which you only need if the desired package is not available in repositories, while rar, unrar are available there.

> **oldos2er said:**
> ```
sudo apt-get update && sudo apt-get install rar unrar
```
Make sure you have 'multiverse' repository enabled before doing above :
Open 'Ubuntu Software Center' > goto Edit > Software Sources > make sure 'multiverse' repository is enabled (that is, the 4th checkbox has a tick mark in it. You might wish to enable all of them)

Closr software center and search for rar, unrar in USC, or close it as well and simply run the above two commands once more.


**PS:**
Just so you are aware, the 'rar' program..
> ..is shareware and you must register it after 40 days of use.
On the other hand, 7zip (p7zip package) is free and is much more efficient. Unrar is non-shareware though.

**PPS:**
> **istealth shadow said:**
> basically, tar.gz files are the same as .rar, .zip, .iso, .7z etc they are all the same,
Not at all. They are all archives, yes, but with huge difference in type and properties, and often have different purpose too.

> apparently winrar for linux is command line **only**
not entirely true. It is a commandline utility, yes, but is also automatically integrated in the default 'Archive Manager' gui. So you also get a gui for using it.

---

### Post by varunendra on 2013-02-24
> **MAFoElffen said:**
> I used rar and unrar until it ran out....
You might wish to correct it a bit. Unrar (nonfree) is actually a freeware, just install it and run 'unrar' command to verify that. The 'nonfree' part stands for its source code only.

I have it installed, and is working perfectly for about a year now. :)

---

