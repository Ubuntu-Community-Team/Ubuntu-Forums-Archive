---
title: "Why are there KDE related updates in my Ubuntu (not Kubuntu) installation?"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by oscarivera9 on 2012-07-21
I often notice, when the update manager pops up informing me of updates available, why are there KDE related updates if I don't use Kubuntu?  I am using Ubuntu 12.04, with Unity as my preferred desktop environment, even though I also have Gnome, Xfce, and Open Box installed (notice I never said KDE).  Some of these proposed updates include the KDE library and others that are very much dependent on KDE.  Currently, there is even Nepomuk included, which I know is the KDE backup option.  I've always wondered why these are available for someone who's not using KDE, but yet I assume that I need them so I install them.  However if I don't need them I'd prefer not installing them.

---

### Post by oldfred on 2012-07-21
Did you install any application that is default KDE? 

I prefer K3b and KMyMoney, so I do get a lot of KDE files downloaded as once you install an app it needs many support files.

---

### Post by PaulW2U on 2012-07-21
Are you sure that you haven't installed any KDE application that would pull in KDE libraries and hence attract updates at a later date?

You're the third person that I've come across today that has reported this. Very strange, especially the presence of nepomuk which is actually to do with file indexing and searching rather than backup.  :confused:

---

### Post by vasa1 on 2012-07-21
Run:
```
dpkg --get-selections > ~/Desktop/installed-software
```
It will create a text file called **installed software** on your desktop.
Look for packages beginning with **K**. If you can't figure it out, post that subset here. Someone will identify the package for you. If that doesn't work, you may have to put up the entire list here or somewhere.

Edit: as oldfred pointed out, all you need to do is to install just one single program that needs KDE-stuff and the whole family comes to stay ;)

---

### Post by oscarivera9 on 2012-07-22
> **oldfred said:**
> Did you install any application that is default KDE? 

I prefer K3b and KMyMoney, so I do get a lot of KDE files downloaded as once you install an app it needs many support files.


Wow!!!
I didn't realize that installing just one KDE application would install almost everything *except* for the actual KDE desktop environment.
So yes, I did install K3b and K9copy a while ago so I guess that answers my question.

Thanks much for your help oldfred, this is the second time that I ask for help and you come to the rescue in a very timely fashion.
In fact, thanks to everyone who helped me with my question.

---

