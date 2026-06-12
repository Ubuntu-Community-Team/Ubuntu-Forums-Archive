---
title: "Won't install...GUI extremely sluggish"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by digbydriver on 2006-10-08
I downloaded the CD...checked OK.  Booted to GUI screen. Clicking on Browser or Email pgm but they do not open.
Clicked on "Install"...system very slow...gets to step two..select geographic location...sticks there.
Mouse works. Monitor works...GUI comes up.
Using Pentium III at 350Mhz.
192Mb ram
Windows XP previously running on this system. Trying to run Ubuntu only..one partition.
Disappointing so far.
Right now am installing Fedora on same system, just to check it..Fedora is installing fine.
I thought Umbuntu was a text based install.  I did not see a text based install.
Any ideas? I assume the system is OK with Linux...since Fedora is installing itself on it as I type this.
Wanted to try Umbuntu, but for some reason it does not run at all.
Ideas?

---

### Post by Kateikyoushi on 2006-10-08
Try Xubuntu, the system requirements are much lower for that version, the alternate cd is recommended as installation media for lower end systems.

---

### Post by Virtute on 2006-10-08
Another way, if you're computer just absolutely refuses to run a LiveCD period, is to get the Server version.  It installs with absolutely no GUI, and once you get it installed just run a simple 'apt-get install gnome' (or KDE, whatever) and set everything up, no problem.  I had to do this with a bunch of outdated computers at school that couldnt load a LiveCD with the RAM that they had.

---

### Post by Iandefor on 2006-10-08
I hesitate to chip in, because in my experience, people who aren't that familiar with Linux quickly get overwhelmed with their options.

That said, there are more than a few options, some of which may not be the best option for your computer. Here are some options that immediately jump to mind, with my own thoughts on how each would suit your needs:
[I]
1. [/I][I]Get the Alternate Install CD
[/I][INDENT]This probably wouldn't help too terribly much. It's the same installer interface as was used in Breezy Badger (meaning it uses a text-based interface), but installs the full default Dapper Drake operating system.

I can assure you that it will be painfully slow to use Dapper on a computer with the system specifications you listed.
[/INDENT][I]
2. [/I]*Get the Server Install CD*[INDENT] This would be *my* preferred way of installing Ubuntu on a system like yours, since it installs only the most basic set of packages and leaves you at a bash prompt from which you can just install the extra packages you want.

However, it seems like you're not that familiar with Linux yet, so I wouldn't recommend this. It's easy to get confused and wind up breaking your installation (leaving you exactly where you started) if you don't know what you're doing. However, if you'd be willing to play around on the command line for a bit, you can get quite a usable system using this method.
[/INDENT][I]
3. [/I]*Get Xubuntu*[INDENT] This would be a better option than either 1 or 2. XFCE is a pretty lightweight desktop environment that's still really usable. Xubuntu is a variant of Ubuntu that uses XFCE instead of the default GNOME desktop environment. This is what I would recommend. You can find out more about it [here]("http://www.xubuntu.org/").
[/INDENT][I]
4. [/I]*Get Fluxbuntu*[INDENT] Fluxbox is *even more* lightweight than XFCE, and there is an independent variant of Ubuntu called Fluxbuntu that uses Fluxbox instead of GNOME. However, it's still in heavy develpment and liable to break. If that doesn't faze you, [go for it]("http://www.fluxbuntu.org/").
[/INDENT]One last thing: Ubuntu *used* to be a text-based installation, but with Dapper Drake they chose to make the text-based installation an *alternative* way of installing Ubuntu, with a full graphical installation the main way to install it.

---

