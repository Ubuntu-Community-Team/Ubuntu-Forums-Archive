---
title: "apt preferences question"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by l_b on 2008-03-14
Hi all!

I'm having some troubles with configuration /etc/apt/preferences

What I'm trying to do: I want just all gutsy packages. Except the ruby packages. I want them from Hardy. What I have so far:

```

;This is for not installing ALL hardy packages
Package: *
Pin: release v=7.10
Pin-Priority: 101

Package: *
Pin: release v=8.04
Pin-Priority: 100

;This is for installing ruby hardy packages
Package: *ruby*
Pin: release v=8.04
Pin-Priority: 1100

Package: *ruby*
Pin: release v=7.10
Pin-Priority: -1

```

When I do upgrade -s it doesn't want to update anything (so that's ok)
But apt-get install ruby wants to install the gutsy packages :(

When I do a apt-get install ruby -t hardy it installs the hardy packages. But then they won't get updated because apt doesn't see them as the "default" packages. 

Does someone know how to solve this?

---

### Post by zvacet on 2008-03-15
You can download them from [here](http://packages.ubuntu.com/search?keywords=ruby&searchon=names&suite=hardy&section=all),or you can add this line in your source list

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy universe

```
sudo apt-get update
```

install your packages ans after that delete hardy line from source list

---

### Post by l_b on 2008-03-15
> **zvacet said:**
> You can download them from [here](http://packages.ubuntu.com/search?keywords=ruby&searchon=names&suite=hardy&section=all),or you can add this line in your source list

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy universe

```
sudo apt-get update
```

install your packages ans after that delete hardy line from source list

But then they won't get updated any more. The line was already there:

```

root@polly:~# cat /etc/apt/sources.list.d/hardy.list
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

```

Thanks for the reply though.

---

### Post by zvacet on 2008-03-15
It is not  good thing to have mixed source list.That is why I said to you to delete Hardy line after installation of packages.

---

