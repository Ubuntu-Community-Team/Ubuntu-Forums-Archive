---
title: "Unable To install FatRat"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by BeatnikBandit on 2010-03-29
from my searches on the Ubuntu sites it said it would be in the universe repository although its not I am using Ubuntu 9.10 Karmic although I think it may be on the Lucid repository not Karmic? :confused:

SO since it is not in the repository can someone help me out with installing it I would guess manually the problem is i have only installed maybe 2-5 programs from source i do have the build and make libraries installed so if someone wants to help we can skip those steps.

I feel bad asking because i feel as it is a question that should be easy to answer and i hate asking stuff like this but I wish to use this program and IDK how to install it :(

**ANY HELP is appreciated THANK YOU**

---

### Post by n0dix on 2010-03-29
Add the repo:
```
$ sudo add-apt-repository ppa:nilarimogard/webupd8
```
and installing:
```
$ sudo apt-get update && sudo apt-get install fatrat
```

---

### Post by BeatnikBandit on 2010-03-30
Thanks are there any other good repositorys that are commonly used for apps like this or will i find them to be more specified as a repository like the one with a few programs and different versions of others but in all only a small repository with 1 or 2 interesting apps, IDK if we had a list of repositories and what they contain would be nice and help people like me who are not the best at compiling from source and some that are more difficult to build than others. IDK again it might be something that would only be useful for people like me who i would hope will learn how to compile more apps as i have about5 under my belt but all done with a how to so i cant hang on my own yet but i at least have the build and make dependences. 

In all thanks with a repository its almost idiot proof once you know apt

---

### Post by n0dix on 2010-03-30
I think there is not an official repo. But Internet can work like one. Indeed, your repo a find it looking on Internet.

---

