---
title: "Ubuntu/Kubuntu"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by jonttix on 2006-06-05
I have installed ubuntu with a cd, then i wanted kubuntu instead so I installed it. My question is, can I now uninstall ubuntu, and if so how do I do that?

---

### Post by aysiu on 2006-06-05
[QUOTE=jonttix]I have installed ubuntu with a cd, then i wanted kubuntu instead so I installed it. My question is, can I now uninstall ubuntu, and if so how do I do that?[/QUOTE] There's no easy way to do it. Are you hard-up for hard drive space? Is that why you want to remove it?

Until I update the "remove Gnome" tutorial for Dapper, you'll have to do this: ```
sudo aptitude remove ubuntu-desktop
sudo aptitude update
sudo aptitude install gtkorphan
gksudo gtkorphan
``` Then mark for removal the orphaned packages you no longer want to have around.

---

### Post by ubnoobie on 2006-06-05
[QUOTE=jonttix]I have installed ubuntu with a cd, then i wanted kubuntu instead so I installed it. My question is, can I now uninstall ubuntu, and if so how do I do that?[/QUOTE]

it won't be easy, but it can be done. you'd have to manually go through the contents of the ubuntu-desktop package, and it's depends, and depends of those depends, etc.. and manually select them for removal using aptitude. removing just the ubuntu-desktop package (the desktop initially installed) will not remove it's contents, just the meta package.


here's one attack strategy that uses aptitude to minimize the amount of work somewhat.. (note not actually tested, just ran through aptitude to check the process and get the final results... use at own risk)...

[LIST=1]
[*]using aptitude: hit _ (purge) next to ubuntu-desktop (the *desktop meta packages are under tasks)
[*]hit + (install) next to ubuntu-minimal, ubuntu-standard, kubuntu-desktop.

[*]hit G to get to the summary. it will 'fix' broken packages

[*]hit Q to get back to where you were.

[*]expand kubuntu-desktop task, find the kubuntu-desktop meta package itself and go into it (hit enter on it)..  select everything in it (do not select the kubuntu-desktop meta package yet)..  then hit Q once to get back to the list of packages.

[*]hit B to find 'broken' packages and hit + (install) next to each (B then + repeatedly until there are no more broken packages)

[*]hit G to get back to the summary screen (just to be sure everything's ok). and then go Q back again. this time select the kubuntu-desktop package. it shouldn't break anything at this point. 

[*]hit G, once more, hit _ (purge) on the 'packages being removed...' and 'packages being deleted...' lines.

[*]go through the above sections to see if there's anything being removed that you don't really want gone.  cross your fingers and hit G once more.
[/LIST]


sounds like a lot of work? ya... but i think the above will purge most, if not all, the ubuntu-specific packages (that aren't in kubuntu) while keeping all the kubuntu ones... at least that's what i see in the aptitude summary when i run through the above...


if this is a clean install, your best best might just be to do a new installation using a kubuntu cd.

---

### Post by aysiu on 2006-06-05
Okay, I updated it.

If you have both Kubuntu and Ubuntu installed, and you want to remove Ubuntu, go here:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by CybaCowboy on 2006-06-06
Mmm, switching from Ubuntu to Kubuntu with only a Ubuntu CD is a real pain in the ***...

I did it just recently and although I was eventually successfuly, I acutally uninstalled Ubuntu's complete interface, leaving me with just a text prompt!

Fortunately, the friendly folks here helped me to the K Desktop Environment (KDE) using the text-only version of Ubuntu...


You know that Kubuntu CDs are now available, for free I might add?

Head over to [http://shipit.kubuntu.com](http://shipit.kubuntu.com) for details, and to order your free CD/s...

---

### Post by glotz on 2006-06-06
Could you use the old overwriting trick in here? I mean reinstall Ubuntu with aptitude to the Ubuntu + Kubuntu system and then uninstall it with aptitude?

---

### Post by Rajan Varadarajan on 2006-06-06
I have a slightly different question. I like both GNOME and KDE packages/apps available to me. With Breezy, I did the regular install and then installed KDE on top of it. That way, I got some of my special KDE apps.

Can this be done with Dapper without having the Kubuntu CD? Last time I did this from the repositories.

Thanks for your help. I am just waiting for my CDs to show up!!

---

### Post by aysiu on 2006-06-06
Yes, it can be done the same way as in Breezy:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

