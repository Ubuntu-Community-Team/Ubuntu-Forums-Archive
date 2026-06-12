---
title: "Installing from Gusty Repositories"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Mr.Macdonald on 2008-02-24
Hello,

I am rather upset because

-I have been working to install Eclipse for the Android project which worked until I tried to install the Android plugin fails because it wants the JDT Plugin but i have no idea how to install that but would like to use the Eclipse update manager

-I have gotten the android to work but with Ubuntu Gusty and would like to know if it is possible to use the gusty repositories along side or instead of the feisty for some installations without installing gusty.

any help would greatly appreciate, but if you could configure your help to use the available programs, such as synaptic or eclipse update manager, to solve them i would prefer this because I would be able to remember it easier than commands in terminal(if that made sense)

But Help in any form is always accepted

---

### Post by Mr.Macdonald on 2008-03-06
Sorry to bump

But i solved my "Eclipse Android" problem with YoXo's

But i still would like to know if it is possible to install from the gusty repositories

---

### Post by zvacet on 2008-03-07
> But i still would like to know if it is possible to install from the gusty repositories

It is possible.**But is it recommended?** I belive no.Anyway if you know in which repo your package is (let it be universe for example) add that epo to your source list

```
gksudo gedit /etc/apt/sources.list
```

add 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe

save and close

```
sudo apt-get update
```

One you install wanted package remove or put # in front of gutsy line.It is very bad thing to have mixed repos.

---

### Post by Mr.Macdonald on 2008-03-07
I understand that it isn't recommended 

But

I need/want GIMP 2.4 (latest) and i would prefer a Ubuntu ready version that i can apt-get because i feel that it would go into a database and be much cleaner of an install.

---

