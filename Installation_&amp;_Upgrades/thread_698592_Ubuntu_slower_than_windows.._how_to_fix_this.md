---
title: "Ubuntu slower than windows.. how to fix this?"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by xlinuks on 2008-02-16
Hi,
I'm using Ubuntu for a year and a half, I noticed long ago that it works (a lot) more slowly than windows (XP), first off I mean the startup time of the default applications, in short, explorer.exe loads in a blink of an eye (for instance on the computer at work where I have also silently installed Gutsy) but when I switch to Gutsy Nautilus takes like 4 seconds to load (cold start), even the "warm" starts are way slower than the ones of explorer.exe. The same applies to the default image viewing apps, text editors (I understand that gedit is way more feature-rich but it loads like 10 times more slowly than notepad.exe!).
One prolly doesn't get to notice this (big difference) on a core-duo like computer, but on my work-machine with a pentium 4 (2.8Ghz) with 64MB of on-board intel Video - windowsXP outperforms my Gutsy by orders of magnitude. I mean practically any default app under windows loads (and executes) a lot faster...
So here's the actual question. Why is that? Because of the X-Server, because of the compiler not optimizing code as well as the the one Microsoft uses for its apps/platform? The thread I read about this issue all end up with something like "install video driver", "Ubuntu is faster" or "install xubuntu". I installed Ubuntu on my friends computers, based on AMD/Intel and everywhere Ubuntu is not as fast as WinXP.. A co-worker asked me today about this issue and I didn't know what to answer, I just said it's cause the visual libraries are build into the windows kernel directly and in Linux they are not..

So, any ideas in what areas should work be done to improve the overall performance? I'm an Ubuntu user (or even fan), I started learning C++ for that reason, among other things planning to create a qualitative FM for Ubuntu.
At least an article related to that would be great...

---

### Post by tighem on 2008-02-16
You might try thunar instead of nautilus. It's faster.

I'm no XP expert, but I'm pretty sure explore.exe is always running. Check your task manager and you'll see it.

---

### Post by julian67 on 2008-02-16
Gnome desktop is not the fastest desktop and Ubuntu is not the fastest distro.  Anyone who has tried a few different distros can appreciate this.  For something with snappier application opening while remaining with Ubuntu a good choice is Xubuntu, you'll find the same kind of performance that you see on XP with applications loading very quickly.  There is also Fluxbuntu, very snappy with fluxbox in place of Gnome. There are also some changes you can make to Ubuntu (or any distro) such as adding the noatime option to fstab, implementing prefetching and so on (google or search the forums for more on tweaking Ubuntu). Imo the performance difference you're experience has everything to do with the Desktop Environment (Gnome) and not the underlying base of the GNU tools and Linux kernel.....I believe this because if you run Xfce or fluxbox or similar you get extremely good performance even on older hardware.  You might also want to look at other distros which tend to be faster, they include Debian, Mepis, Antix (both Debian based like *buntu), Zenwalk, Wolvix (slackware based), Slackware itself, Arch and so on. One of the benefits of Free software is that you're free to try out all kinds of different stuff to find what suits you best. 

It's also worth remebering that there's more to performance than how fast an application loads, there are also the questions of how the application *performs* and how the system as a whole performs when under load. Ubuntu can look a lot better compared to XP when the system is heavily loaded, it tends to remain stable and the applications remain more stable too.

---

### Post by xlinuks on 2008-02-17
Yep, Ubuntu is definitely a lot more stable and who knows, perhaps if WinXP manages to be as stable it might also get (much) slower as a side effect..
Gnome in Mandriva seems to be faster, but the distro itself IMHO is far from being as polished as Ubuntu.. (has important glitches I can't fix)
I installed the xfce desktop - it's faster and pretty nice, it doesn't seem to support multiple language keyboards, I need Russian. In Gnome I can do it in it's preferences, but in xfce's version there was only the English layout (perhaps it's burried somewhere else..). The DND could be better, but in some areas xfce it is actually better.. if its developers keep the good work I might dump Gnome for xfce..

---

### Post by julian67 on 2008-02-17
There's keyboard switching available via a panel plug in (Keyboard Layout Switcher). Right click on the panel and add it :) If the option isn't there then the plug in is easily installed with synaptic/apt.  Xfce can do pretty much everything Gnome can do but you might need to investigate Thunar's custom actions, there's a lot of good help on the Xfce website. The only major omission imo is there is no network shares browser but pyNeighborhood or LinNeighbor fit the bill nicely.  I was pleased and surprised to find that my favourite Gnome apps (Epiphany, Liferea, Evolution, F-Spot, Totem-Xine) launch faster under Xfce than they do in Gnome.

---

