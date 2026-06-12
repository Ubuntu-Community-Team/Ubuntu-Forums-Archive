---
title: "apt-get removes kde"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Belisarius on 2007-04-24
Hi,
Not sure if this is the right forum but here goes:

I have Edgy on my main PC and Feisty(was beta) on my laptop. I have KDE installed on both.

I just used apt-get to install ncftp on the main(64bit) PC and during the install it listed a load of libraries that it said could be removed using apt-get autoremove. Now I confess to being a bit rushed so I didn't look closely and just did it thinking I'd free up some space. What it actually did was remove KDE from my system

I did the same thing on the Fiesty laptop and it comes up with the same message.

I'm currently running an update to Feisty on my main PC so I'm not sure whether it will put KDE back on automatically or whether I need to reinstall.

KDE still appears as a session option but when I select it I just get Gnome.

Am I missing something here? Is there a problem or is it just part of some GNOME world domination plan? :) 

Cheers

Andy

---

### Post by AndrewNi on 2007-04-24
It was probably the kubuntu-desktop meta package that got removed. That package depends on all the KDE packages (including ones you may not have wanted and decided to remove), so if say you removed Akregator it would also remove the kubuntu-desktop meta package.

Now that's gone, apt thinks that all those KDE packages that you want to keep were automatically installed and are wasting space. So using autoremove removes all KDE packages.

---

### Post by Belisarius on 2007-04-24
That's a really useful facility :confused: 

I think I'll not bother doing it my laptop and just reinstall on my main.

Thanks

Andy

---

