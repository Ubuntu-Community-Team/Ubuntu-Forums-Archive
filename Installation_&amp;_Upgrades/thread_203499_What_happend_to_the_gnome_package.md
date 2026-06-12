---
title: "What happend to the gnome package?"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by hizaguchi on 2006-06-25
Anybody know what happened to the gnome package?  I know I can get Gnome by installing ubuntu-desktop, but I really don't want alot of the other stuff that comes with that.  Used to be that I could just "apt-get install gnome" (like I would on Debian) and then later add the other packages that I want.  Now there is no big gnome package, and the only way I can figure to install it without a ton of other crap is to go through the ubuntu-desktop task in aptitude and try to pick just the gnome parts.  What's up with that?

---

### Post by Winblowz on 2006-06-25
Thats just how Ubuntu works I guess. Ubuntu is not Debian, and is not any other distro. Ubuntu is supposed to have many packages installed by default so it is easy to use.

---

### Post by taurus on 2006-06-25
If you can pick what packages you want to install with aptitude, then I don't know why you complain about it!!!  If you feel like wasting your time picking the packages, then just install the default and remove whatever you don't want later!!!  :rolleyes:

---

### Post by matthew on 2006-06-25
Are you talking about this package?

[http://packages.ubuntu.com/dapper/gnome/gnome]("http://packages.ubuntu.com/dapper/gnome/gnome")

If so, it's possible you need to [enable the extra repositories]("http://www.psychocats.net/linux/sources.php")

EDIT: I noticed the repositories page I linked to discusses 5.04 and 5.10 and not 6.06. Just change the word "breezy" from the 5.10 instructions to "dapper" and it's the same procedure.

---

### Post by hizaguchi on 2006-06-25
[QUOTE=taurus]If you can pick what packages you want to install with aptitude, then I don't know why you complain about it!!!  If you feel like wasting your time picking the packages, then just install the default and remove whatever you don't want later!!!  :rolleyes:[/QUOTE]
I'm not complaining.  I'm just asking why such a handy feature would be removed.  If I were complaining, I would have said something like, "OMG!!! Stupid devs took out the gnome pkg!!!!"  No, I was just wondering where it went.

And yes, I'm capable of hand-picking all the pieces of Gnome to get a usable desktop.  But then I'm also capable of resolving my own dependencies.  So if a gnome package was just an unneccessary convieneince, does that apply to apt as well?

---

### Post by hizaguchi on 2006-06-25
[QUOTE=matthew]Are you talking about this package?

[http://packages.ubuntu.com/dapper/gnome/gnome]("http://packages.ubuntu.com/dapper/gnome/gnome")

If so, it's possible you need to [enable the extra repositories]("http://www.psychocats.net/linux/sources.php")[/QUOTE]

Ah ha, exactly what I was looking for.  Thanks!  :)

In universe?  Would have never thought to look there. :/

---

