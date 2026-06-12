---
title: "Server GUI install"
date: 2017-01-10
forum: Installation &amp; Upgrades
---

### Post by SchnappiJedi on 2017-01-10
Which of these is going to give a more basic install without the added programs?

```
sudo apt-get install --no-install-recommends lubuntu-desktop
```

or

```
sudo apt-get install lxde
```

In both of these commands assume basic programs such as PCMan (or Nautilis, Dolphin, ect.) will be installed even if doing a bare LDXE, Xfce, Cinnamon, ect install...

---

### Post by HermanAB on 2017-01-10
There is a way to get a list of packages that will be installed:

sudo apt-get install --dry-run something

Another way is to make two virtual machines and try it.

---

### Post by Bucky Ball on 2017-01-10
> **SchnappiJedi said:**
> In both of these commands assume basic programs such as PCMan (or Nautilis, Dolphin, ect.) will be installed even if doing a bare LDXE, Xfce, Cinnamon, ect install...

Yea, but not much more, at least with lxde and xfce. Not familiar with others.

These commands will not yield anything like the same results. The first installs Lubuntu without the recommended programs but with some. You would be installing a pared-back Lubuntu in other words, not usual on a server. May as well just install Lubuntu with no install recommends from the start and not bother with the server.

The second command installs a desktop environment, which is what you're after, lxde. This is obviously more lightweight and people go the desktop environment only with a server if they are going to go there (and most don't).

---

### Post by wildmanne39 on 2017-01-10
*Thread moved to **Server Platforms**.*

---

### Post by SchnappiJedi on 2017-01-10
Kind of wish that this was not moved to the servers section but it doesn't really matter.

Much prefer a terminal for a server (and alot of desktop actions). However this is not for a server. For a Linux desktop don't like how Ubuntu (not picking on it, except for the Amazon stuff, Mint and all others are the same) bundle a good deal of stuff that don't want. However Arch is just a little too minimalist. Realized would achieving goal by installing Ubuntu Server and then adding a GUI and the programs that want. Just don't want the stuff that am trying to avoid in the first place by installing the GUI from scratch.

---

### Post by sjblnx on 2017-01-10
You may want to consider, i3wm ( Tiling window manager ) no apps will be installed. Barebones is what you want. Don't worry about all the tweaking of i3 in the video below, not needed for a server install.
[http://i3wm.org/](http://i3wm.org/)
[https://www.youtube.com/watch?v=j1I63wGcvU4](https://www.youtube.com/watch?v=j1I63wGcvU4) ( i3 tutorial 3parts )
[https://www.youtube.com/watch?v=bju_FdCo42w&list=PLtK75qxsQaMLZSo7KL-PmiRarU7hrpnwK](https://www.youtube.com/watch?v=bju_FdCo42w&list=PLtK75qxsQaMLZSo7KL-PmiRarU7hrpnwK) ( linux sysadmin basics )
[https://www.youtube.com/playlist?list=PLT98CRl2KxKHtOhMYulS43hayRsGXLzmx](https://www.youtube.com/playlist?list=PLT98CRl2KxKHtOhMYulS43hayRsGXLzmx) ( ssh tutorials )

---

### Post by CharlesA on 2017-01-10
Why not just do a minimal install and pick whatever DE you want to use?

---

### Post by Bucky Ball on 2017-01-11
> **CharlesA said:**
> Why not just do a minimal install and pick whatever DE you want to use?

Yea, this is what you want. After you explained what exactly you're after, forget the server. No point. Minimal install and then add the programs you want. I always did that and then added xfce and the programs I want/need only. Now I use Xubuntu-core which pretty much does the preliminaries for me. You get a basic Xubuntu with nothing in it, no web browser, no package manager. You add what you want. I generally add Synaptic Package Manager and take it from there.

Here's a link:
[http://xubuntu.org/news/introducing-xubuntu-core/](http://xubuntu.org/news/introducing-xubuntu-core/)

The very last link on that page is to some community ISOs, 16.04 LTS included, which can be used like any other install ISO. 

My advice? Don't waste any more time with the server palaver. Sure, you won't get a desktop environment and a bunch of other things, but you will get a bunch of server related stuff you may/probably never use. You don't need it.

---

### Post by slickymaster on 2017-01-11
Moved from the **Server Platforms** since the OP is not running a server nor his query regards ones.

---

