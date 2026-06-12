---
title: "can't seem to remove kubuntu"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by brutalandkind on 2008-05-17
Very much a newbie here; only been using ubuntu about 2 weeks and a friend urged me to try kde/kubuntu on top. Fair enough, and it seemed easy (following these directions: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde) which essentially led me to the command 'sudo aptitude update && sudo aptitude install kubuntu-desktop'). 

Turned out kubuntu was a lot buggier on my system (various display problems, keyboard repeats, that sort of thing) so I figured I'd just remove it (using the command 'sudo aptitude remove kubuntu-desktop').

However, now I still get the kubuntu shutdown/start screens, and the options menu accessed pre-login from the bottom right in ubuntu still offers the kde options. Also, all the "old" kubuntu programs are still listed on my menus, only with blanked-generic icons.

Can anyone guide me to completely removing the kubuntu stuff without a complete wipe and re-install? This is in Heron 8.04. I did try a couple of searches on this problem but cannot find anything on-point; apologies in advance if I am nevertheless covering old ground.

Thx.

---

### Post by teaker1s on 2008-05-17
you have old config files left, I would suggest 
```
sudo synaptic
```
search title and description and select completely remove on the remaining installed kubuntu packages.

before you fully commit to removal you will be given list of packages that will be removed (check your happy it&#347; just kubuntu related) then remove them.

If you want to remove all kde related packages
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by brutalandkind on 2008-05-17
> **teaker1s said:**
> you have old config files left, I would suggest 
```
sudo synaptic
```
search title and description and select completely remove on the remaining installed kubuntu packages.

before you fully commit to removal you will be given list of packages that will be removed (check your happy it&#347; just kubuntu related) then remove them.

If you want to remove all kde related packages
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

That worked *perfectly*! Thank you so much!

For what it's worth, I really like Ubuntu so far. And I love this forum! I haven't posted much, because nearly every time I have a question I find it has already been asked-and-answered succinctly and clearly already!

---

### Post by teaker1s on 2008-05-17
no problems, ubuntu is modular -you can practically uninstall it completely, reinstall and then reboot.
:popcorn:

---

### Post by wayno on 2008-05-18
damn this forum is good, thanks mate

---

### Post by Orion13622 on 2008-05-21
Thanks, that also worked well for me.  I too am new with Ubuntu, and installed both the KDE 3.5.9 and KDE4 on my system.  Not impressed with either of them at this time, but hey...they'll catch up eventually. (Small things like, the clock font not resizing when you tell it to be on a smaller toolbar tends to bug me).  Even though I run this on a Compaq Presario R3000z CTO machine (AMD Athlon 64, 2 gig of memory, 2.4 GHz) I'm still allowed to be picky.  :)  Yes, I am running 8.04 in 64bit and I do love it.  Quite nice.  Only problem I have is my internal memory card reader doesn't work.  Anyone have a solution for this by chance?  Thanks much again!

---

### Post by teaker1s on 2008-05-21
```
lspci -v
``` then you can find out the card reader mave vendor and product id

---

