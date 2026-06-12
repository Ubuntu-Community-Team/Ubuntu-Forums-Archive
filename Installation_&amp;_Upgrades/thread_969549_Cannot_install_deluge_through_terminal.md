---
title: "Cannot install deluge through terminal"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by Scheh789 on 2008-11-03
When I use sudo apt-get install Deluge in the terminal it sends me this error:
ghost@ghost-laptop:~$ sudo apt-get install deluge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deluge
ghost@ghost-laptop:~$ 

Not only does it do this with deluge but also with other various programs trying to download in terminal.

Please help!!

---

### Post by kostkon on 2008-11-03
> **Scheh789 said:**
> When I use sudo apt-get install Deluge in the terminal it sends me this error:
ghost@ghost-laptop:~$ sudo apt-get install deluge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deluge
ghost@ghost-laptop:~$ 

Not only does it do this with deluge but also with other various programs trying to download in terminal.

Please help!!
Actually the package's name is deluge-torrent, thus you need to do
```
sudo apt-get install deluge-torrent
```
But make sure that go to *System -> Administration -> Software Sources* and check if you have all the repositories enabled (except Proposed, you don't need to have this enabled).

---

### Post by Scheh789 on 2008-11-03
ahah wow i feel like an idiot, thank you very much!

---

### Post by werewerewere on 2009-12-05
i put in 
sudo apt-get install deluge-torrent and still get E: Couldn't find package deluge-torrent
can  anyone help me please?

---

### Post by falconindy on 2009-12-05
You can use `apt-cache search` to find pacakges. Also, you may just want to hook up the deluge PPA:

[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

---

### Post by oldos2er on 2009-12-05
> **werewerewere said:**
> i put in 
sudo apt-get install deluge-torrent and still get E: Couldn't find package deluge-torrent
can  anyone help me please?

 Make sure you have the universe repository enabled. System, Administration, Software Sources.

---

### Post by werewerewere on 2009-12-05
i made sure universe repository was enabled  
now when i type in apt-get chache search  am i supposed to just get a @ubuntu line

---

### Post by oldos2er on 2009-12-06
Have you run **sudo apt-get update ** ?

---

