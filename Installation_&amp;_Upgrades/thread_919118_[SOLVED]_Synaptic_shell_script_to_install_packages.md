---
title: "[SOLVED] Synaptic shell script to install packages - How do I use it?"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by charonred on 2008-09-13
Just need some advice of how to generate a shell script in Synaptic of all the 'Installed' packages in my system.

I build new PCs part-time as a hobby/business, and a script to install the packages I have on my system would make it dead easy for setting up other PCs that I build for friends/family (I've talked a few into dual booting with 'Hardy').

In Synaptic Package Manager, under 'Status', I've chose the option to list all 'installed' on my system and then select 'Generate Package Download Script', but all I get is a 10 byte file with this inside

#!/bin/sh

---

### Post by icheyne on 2008-09-13
dpkg --get-selections > pkg.list

---

### Post by charonred on 2008-09-14
thanks icheyne, 
that created a list of my installed software, but how do I get Synaptic to auto download and install what's in the list?

---

### Post by icheyne on 2008-09-14
It's easy using aptitude or apt-get from the command line. Try this:

```
 sudo aptitude install package1 package2 package3
```

One long command will install all the apps you want.

---

### Post by zvacet on 2008-09-14
If you want to do it with the script 

```
dpkg --get-selections > installed-software
```

put text file in another comp and run

```
dpkg --set-selections < installed-software
dselect
```

If you didn´t run **apt-get clean** or **apt-get autoclean ** you can use [aptoncd.]("http://aptoncd.sourceforge.net/")Install it from synaptic.

---

### Post by charonred on 2008-09-14
thanks again


icheyne;
does that mean I have to number each package as >  sudo aptitude install package1 package2 package3 all the way up to package1644 ?


zvacet;
I'm relatively new to Ubuntu  and am not that experienced at running these linux command line stuff; so how/where do I use the command lines with the 'pkg.list' - sorry, but I need some 'Ubuntu for Dummies' type instructions to get going

---

### Post by icheyne on 2008-09-14
No numbers, just the regular package name.

You **definitely** need to do some reading if you want to try advanced stuff like this.

I read [Introduction to Linux]("http://tldp.org/LDP/intro-linux/html/index.html") when I started and it saved me a lot of effort.

PDF and portable versions are available too - [http://tldp.org/guides.html](http://tldp.org/guides.html).

---

### Post by charonred on 2008-09-14
I've been so impressed with the standard install and functionality of 'Hardy', that I bought a copy of 'Ubuntu Unleashed', but I haven't got near reading any of it yet - just time limited with too many other things on the boil. 

At the moment I'm simply trying to get 'Hardy' tweaked and tuned for full-time use instead of Windoze; once that's done, then I can study up on Linux more in some of my 'free time' - for the moment, any 'show me' type instructions stuff is really appreciated (I've downloaded .pdf versions of docs from tlpd.org, thanks).

I'm also trying to get friends out of their discomfort zone with XP and into Ubuntu, so running some sort of script to install all the tweaks on each PC just makes life a bit easier. All the PCs I've built for them are AMD & Gigabyte based with most using ATI graphics, so installing all the same packages I have should work well for most of them - and then they can start posting 'help me' on Ubuntu forums as well ;)

---

### Post by zvacet on 2008-09-14
@ **charonred**

When you run in terminal

> dpkg --get-selections > installed-software

you will find tex file in your home directory named installed-software.You can put it in other comp in several ways(burn it on CD,stick) or simply post it to yourself or to your friend by e-mail(I believe that you have some gmail,yahoo... account).When text file is in second comp again in terminal

```
dpkg --set-selections < installed-software
dselect
```

You can also check link I posted to you which explains how aptoncd works.That can be solution too.If you still have any questions just ask.Good luck!

---

### Post by arunncce2089 on 2010-04-02
Hi

What i am trying to do is take the list of all installed packages from one machine 'A' and install same packages to other machine 'B' and in addition to that i want to uninstall all those packages from machine B which are not in machine 'A'.

Is there any way to do that?

Thanks

Arun Mittal

---

### Post by arunncce2089 on 2010-04-02
Please dont worry about the previous reply.
I figured out the solution

---

### Post by mordak13 on 2010-04-23
I opened Synaptic and under File, then Read Markings and then select the pkg.list file and it's working on my 3rd Ubuntu machine so far so good.

---

