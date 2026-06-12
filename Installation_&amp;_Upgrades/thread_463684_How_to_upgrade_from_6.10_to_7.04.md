---
title: "How to upgrade from 6.10 to 7.04?"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by Pumalite on 2007-06-03
I tried this, but I got nowhere:

pumalite@pumalite-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
pumalite@pumalite-desktop:~$ 

Any ideas? Thanks in advance. What is 'Need to get OB of archives. After unpacking OB will be used'? How do I get OB archives?

---

### Post by Pumalite on 2007-06-03
> **Pumalite said:**
> I tried this, but I got nowhere:

pumalite@pumalite-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
pumalite@pumalite-desktop:~$ 

Any ideas? Thanks in advance. What is 'Need to get OB of archives. After unpacking OB will be used'? How do I get OB archives?

Trying to avoid a fresh install.

---

### Post by bergersau on 2007-06-03
You need to edit your apt-sources file first to change all referances to "edgy" to read "feisty".
Then -  sudo aptitude update , that will refresh the package lists.
Then a sudo aptitude dist upgrade should do the trick.

The reccomended way is to use the update manager in preferance to aptitude I belive.  I'm not sure why, I think both should work.

I give this advice from memory so please don't blame me if you manage to bork your system. The usual backup first rule applies.

---

### Post by Pumalite on 2007-06-03
> **bergersau said:**
> You need to edit your apt-sources file first to change all referances to "edgy" to read "feisty".
Then -  sudo aptitude update , that will refresh the package lists.
Then a sudo aptitude dist upgrade should do the trick.

The reccomended way is to use the update manager in preferance to aptitude I belive.  I'm not sure why, I think both should work.

I give this advice from memory so please don't blame me if you manage to bork your system. The usual backup first rule applies.

Thanks a lot. Good advice in all counts. We'll see how it goes.

---

### Post by zvacet on 2007-06-04
Don´t change your source list yet.Look at this first

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

After you finish with upgrade change source list 

```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

**Of course you will comment(put # sign in front of the line)any unofficial repos you have before you do the upgrade.**

---

### Post by Pumalite on 2007-06-04
> **zvacet said:**
> Don´t change your source list yet.Look at this first

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

After you finish with upgrade change source list 

```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

**Of course you will comment(put # sign in front of the line)any unofficial repos you have before you do the upgrade.**

Thanks for the advice zvacet. It got here right on time. During the night I did the upgrade with the Upgrade Manager. I'm writing to you from my 7.04, so, there seems to be good news.  Of course I haven't had the time to look around yet. Next stop, the sources.list. Thanks again.

---

### Post by zvacet on 2007-06-04
You are wellcome.

---

