---
title: "Help installing sdl dev dependency problems"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by ness0216 on 2007-04-04
I'm starting to do some SDL development so I went to install libsdl1.2-dev and I get this error
```

libsdl1.2-dev:
 Depends: libglu1-mesa-dev but it is not going to be installed or
	libglu-dev

```

So i went to try to install libglu1-mesa-dev and got this
```

ibglu1-mesa-dev:
  Depends: libglu1-mesa (=6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed

```

I'm figuring it's because I have cvs repositories set up for beryl. Is there a way I can force it to install the version that is needed for the sdl development packages?

---

### Post by PsychoAlienDog on 2007-04-14
I'm having the same problem, and I also have Beryl installed.

[QUOTE=the aptget man page] A specific version of a package can be selected for installation by  following the package name with an equals and the version of the package to select. This will cause that version to be located  and selected for install. Alternatively a specific distribution can be selected by following the package name with a  slash and the version of the distribution or the Archive name (stable, testing, unstable).
[/QUOTE]

I Tried it and everything seems to be normal.  SDL installed no problem.

---

### Post by ErikDeBruijn on 2007-04-21
To get around this:

1. temporarity disable (comment it with #) the beryl repository (edit /etc/apt/sources.list)
2. [FONT="Courier New"]# apt-get update[/FONT]
3. If you want a specific version, type:
[FONT="Courier New"]apt-get install libglu1-mesa=6.5.1~20060817-0ubuntu3
[/FONT]
4. install the packages that you inteded to (which depended on this version)
5. enable the repository again

Most releases will not break if they're only a few days apart. But beryl simply keeps up with all changes very quickly...

---

