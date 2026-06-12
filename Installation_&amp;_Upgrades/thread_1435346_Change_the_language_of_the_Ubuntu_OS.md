---
title: "Change the language of the Ubuntu OS"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by siemprepeligroso on 2010-03-21
Dear friends,
I had to install the Edubuntu 7.04 on a PC. it is a government property and the owner of the PC claims that it used to be in Macedonian language. I wonder now how can I change the language of the whole OS, I know the support of this OS is already gone off.

So there is one other option left, I have to install the whole OS from the beginning, but the real question is that will I be asked to choose the OS language at the Installation Setup.

I am using CD for installing not the DVD so I wonder if it contains the language interface packs at all?

It would be much better to resolve the problem with no reinstall at all, but whatever tell me what is the solution now.

Thanks in advance. :)

---

### Post by kio_http on 2010-03-21
Install the language pack from the old Gusty repository. It exists as an outdated no update state as from the last day of Gusty's support time.

1. Edit /etc/apt/sources.list
2. Replace all occurrences of archive.ubuntu.com with old-releases.ubuntu.com
3. aptitude update
4. aptitude install <package name>

However if you ask me, newer releases like Karmic and in future Lucid are much more stable and speedy than Gusty, so why don't you just wait for Lucid and install it?

---

### Post by siemprepeligroso on 2010-03-21
I guess 7.04 is Feasty Fawn, is there going to be any difference in what I have to do? Or it is the same procedure?

and what about "aptitude" ?

---

### Post by Kom-Si on 2010-03-21
> **siemprepeligroso said:**
> I guess 7.04 is Feasty Fawn, is there going to be any difference in what I have to do? Or it is the same procedure?

and what about "aptitude" ?

"aptitude" is the command you type in terminal window (as other commands, too). aptitude is deprecated in modern versions of Ubuntu. I'd really recommend you follow the advice given above and install a newer version, say, current Karmic 9.10. it's fast, stable, and has great language support...

---

### Post by siemprepeligroso on 2010-03-21
In fact I use 9.10 at my PC, but the PC I am talking about is not mine, it is a government property so I have to follow the orders that are given to me, I would like to explain them the situation about new Edubuntu but it is of no use, since it is a part of a project. check Wikipedia about Edubuntu you will find out ;)

---

