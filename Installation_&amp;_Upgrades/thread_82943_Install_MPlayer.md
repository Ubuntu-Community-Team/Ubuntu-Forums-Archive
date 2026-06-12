---
title: "Install MPlayer"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by smgil on 2005-10-27
Hi.

I'm trying to install mplayer and w32codecs in Hoary but I can't, I've tried backport repository but it seems like mplayer isn't avaible there now.

Could somebody tell me from where can I download mplayer ?

---

### Post by Xian on 2005-10-28
You could try the [mplayer-386_1.0-pre7cvs](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-386_1.0-pre7cvs20050716-0.1ubuntu9_i386.deb) version.

---

### Post by Samuli on 2005-10-28
W32codecs aren't in the repositories anymore because of legal problems,

Ty these instructions instead:

[http://www.ubuntuforums.org/showthread.php?t=75278&highlight=win32+codecs](http://www.ubuntuforums.org/showthread.php?t=75278&highlight=win32+codecs)

That's for the codecs. Now can't you install mplayer by just typing sudo apt-get install mplayer-386 (or whatever your architure is) ?

---

### Post by Xian on 2005-10-28
[QUOTE=Samuli]Now can't you install mplayer by just typing sudo apt-get install mplayer-386 (or whatever your architure is) ?[/QUOTE]
They are using Hoary and mplayer is not in the 5.04 repo.

---

### Post by smgil on 2005-10-28
[QUOTE=Xian]You could try the [mplayer-386_1.0-pre7cvs](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-386_1.0-pre7cvs20050716-0.1ubuntu9_i386.deb) version.[/QUOTE]

I've tried to install but I got a few dependence errors, it looks like some libraries aren't new enough but my sistem is updated. I think this package works only with Breezy.

Some time ago I tried to upgrade to Breezy but I got a Xorg error and my keyboard didn't work, and because I'm new in ubuntu and I saw some posts saying that it wasn't recommendable to upgrade because Breezy was still unestable I prefered stay with Hoary.

I've installed on my Laptop (Hoary) the mplayer but I don't remember from where :D.

Any other idea what could I do ?

---

### Post by Xian on 2005-10-28
[QUOTE=smgil]Any other idea what could I do ?[/QUOTE]
Try the [mplayer-386_1.0-pre6](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-386_1.0-pre6-0.3ubuntu6_i386.deb) version.

---

### Post by smgil on 2005-10-31
[QUOTE=Xian]Try the [mplayer-386_1.0-pre6](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-386_1.0-pre6-0.3ubuntu6_i386.deb) version.[/QUOTE]

It works now. I had to download others packages from the archive but i works :-).

Just for the record, I wonder there is a easy way to do this, like add an apt source.

---

