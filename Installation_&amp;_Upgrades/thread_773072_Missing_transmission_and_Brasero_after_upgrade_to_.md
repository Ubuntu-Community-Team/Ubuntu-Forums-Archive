---
title: "Missing transmission and Brasero after upgrade to Hardy"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by mrand on 2008-04-28
I hate to post another message on this, but no responses are forthcoming in the general help section where I initially posted [(here)]("http://ubuntuforums.org/showthread.php?t=768688").

That I've been able to tell, all indications are that I successfully upgraded via update manager from 7.10 (installed originally with the Alt-CD and then added Mythbuntu via package manager) to 8.04.  MythTV got upgraded and so did Firefox.  But Transmission and Brasero are no-where to be found, which has me somewhat concerned... what else is missing?

```
mrand@media:~$ uname -a
Linux media 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
mrand@media:~$ transmission
The program 'transmission' is currently not installed.  You can install it by typing:
sudo apt-get install transmission-gtk
bash: transmission: command not found
mrand@media:~$ brasero
The program 'brasero' is currently not installed.  You can install it by typing:
sudo apt-get install brasero
bash: brasero: command not found
mrand@media:~$ sudo apt-get install ubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mrand@media:~$

```

Thanks a ton... I'd really rather not have to reinstall from scratch!

   Marc

---

### Post by bingobingo on 2008-04-28
Why did you need to upgrade to 8.04 MythTV? Was 7.10 not working for you? What additional benefits did you see with 8.04 over 7.10 did they claim, inorder for you to want to 'upgrade' it? Just curisous, because if it ain't broke why fix it.

---

### Post by mrand on 2008-05-02
> **bingobingo said:**
> Why did you need to upgrade to 8.04 MythTV? Was 7.10 not working for you? What additional benefits did you see with 8.04 over 7.10 did they claim, inorder for you to want to 'upgrade' it? Just curisous, because if it ain't broke why fix it.On the assumption that you are not trolling (seeing as how you are dissing Hardy in other threads), yes, there are reasons I needed to upgrade.  In fact, I probably need an even newer kernel (2.6.25) than what is in Hardy, but that's a different discussion. Back to the thread...

I'm hoping that someone will see this and have some ideas why Firefox 3b5 installed/upgraded correctly, but Brasero and Transmission didn't get installed.  Is there a more suitable forum or sub-forum that someone thinks would be able to answer my basic question:

How do I ensure that all aspects of my system were upgraded to Hardy?

Thanks everyone!

   Marc

---

### Post by Sef on 2008-05-02
[Duplicate Post]("http://ubuntuforums.org/showthread.php?t=768688").  Locked.

---

