---
title: "how to install old version VLC on ubuntu 12.04"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by autogarsas on 2012-06-01
So already for 3th day trying to stream videos from my PC to dreambox (SAT tuner) and watch them on TV, but cant do that in any way. It was working fine on 10.04 with old VLC.

in VLC 2.0.2 streaming server i cant browse files:
[IMG]http://pico.lt/upload/files/2012-06/a7968c9a.png[/IMG]

And dreambox tells that server is not running. Unfortunatly dreambox vlc frontend wont be upgraded i think, so only way is go back with VLC.  So hope someone can help with installing old version, becouse was trying with .deb package but it wont install :/

---

### Post by iris-n on 2012-06-26
I did just that, but because vlc 2 couldn't play sound correctly on precise.

WARNING: Doing this can **** your OS pretty hard, so be careful.

First of all you need to remove vlc and all its dependencies

```
sudo apt-get purge vlc vlc-nox vlc-data vlc-plugin-notify vlc-plugin-pulse libvlc5
```

Now you have to tell apt to use oneiric's repositories instead of precise's. To do that, edit sources.list as root:

```
sudo gedit /etc/apt/sources.list
```

and you'll need to change the line

```
deb http://archive.ubuntu.com/ubuntu precise main restricted universe
```

to 

```
deb http://archive.ubuntu.com/ubuntu oneiric main restricted universe
```

(I'm actually using mint 13, so I'm not quite sure the lines in sources.list are exactly the same; to be sure, just replace any occurrence of precise with oneiric)

Now update your sources (do not upgrade!)

```
sudo apt-get update
```

And your repository is pointing to the good old vlc. Just install it normally

```
sudo apt-get install vlc
```

and mark it as "do not upgrade":

```
sudo apt-mark hold vlc vlc-nox vlc-data vlc-plugin-notify vlc-plugin-pulse libvlc5
```

otherwise apt will just upgrade it again to vlc2 when you upgrade your other packages.

Now revert your sources.list to the old state (i.e., replace oneiric with precise), and 

```
sudo apt-get update
```

You're done! Hope it works well for you, for me it's ok.

---

### Post by m0ckingbird on 2012-08-17
Hey I tried this but it did not work on 12.04. It gave me an error saying that 12.04 requires vlc 2.0 and it does not match....broken links will not install.

---

### Post by iris-n on 2012-09-07
m0ckinbird,

At exactly which step did this error happen? You succeeded at least in removing vlc 2?

I did try exactly these steps on ubuntu 12.04 later, and it worked.

---

