---
title: "Fluxbox, I wanna use it, can I?"
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by asterix404 on 2005-10-06
I was told by some people that I am supose to switch over my laptop from gentoo to ubuntu since ubuntu is nicer and very friendly esp with integrated stuff like for example my intel 2200 wireless card. First off, I noticed that ubuntu comes with gnome... I hate gnome, I find it very tacky and heuge esp running on a laptop when trying to save as much power as possable.

I love fluxbox, I love everything about fluxbox, can I get fluxbox to work with ubuntu and is there a nice clean way of doing it? I know that ubuntu uses apt-get, and this works much like the emerge except I would like to kinda know the difference, is there any docunmentation about the implementation of ubuntu that I can find? 

Does ubuntu recognize resiserfs? Can I recompile my kernel if I don't much like how ubuntu did it? I read the basic docs and didn't see much of anything, does anyone know where I may find the answers to my questions? Thanks a lot, ~Ben

PS. Does ubuntu get my ipw2200 intel wireless card working quickly?

---

### Post by duminas on 2005-10-06
> **asterix404]I was told by some people that I am supose to switch over my laptop from gentoo to ubuntu since ubuntu is nicer and very friendly esp with integrated stuff like for example my intel 2200 wireless card.[/quote]The "friendlier" bit is entirely subjective. I, personally, find Gentoo significantly easier to use, but it's a hobby system.

The choice is yours--don't feel coerced to switch by anyone but yourself. If you've got something that works, I'd advise you to stick with it, but if you're feeling adventurous...
> First off, I noticed that ubuntu comes with gnome... I hate gnome, I find it very tacky and heuge esp running on a laptop when trying to save as much power as possable. I love fluxbox, I love everything about fluxbox, can I get fluxbox to work with ubuntu and is there a nice clean way of doing it?You talking about removing GDM (Gnome) and using Fluxbox solely?
If so, I've created a thread about this very subject that you may want to watch [here](http://www.ubuntuforums.org/showthread.php?t=72333). No replies at time of writing, but I hope to get some, as I love Fluxbox too.  said:**
> I know that ubuntu uses apt-get, and this works much like the emerge except I would like to kinda know the difference, is there any docunmentation about the implementation of ubuntu that I can find?I may be wrong here, but let me take a shot at this...

Gentoo is a **source-based** distribution. This means it downloads sources to things you want (emerge) and builds them for you. You've probably noticed the CFLAGS/CXXFLAGS and USE variables on Gentoo, no? This affects how your programs are built.

Ubuntu is a **package-based** distribution. In this regard, Ubuntu works with prebuilt packages that you do *not* compile. You just download these (.deb extension) and install them with dpkg--apt-get does this transparently, though. There are also a couple of graphical tools to help you, here. The first is Synaptic, which is, to my knowledge, GTK-based. The second is Kynaptic, which is for KDE.. There is also a terminal-based apt frontend--_aptitude_. This also comes standard with Ubuntu.

Basically, in Gentoo, you build programs yourself to match your own optimizations. In Ubuntu, they're pre-built generically and you just install. Does that comparison help?
> Does ubuntu recognize resiserfs?Ubuntu will recognize reiserfs out-of-the-box, and there is a tutorial in the "Customization Tips & Tricks" section of these forums for how to get reiser4 support.
> Can I recompile my kernel if I don't much like how ubuntu did it? I read the basic docs and didn't see much of anything, does anyone know where I may find the answers to my questions?Of course you can. :)
Look in the "Customization Tips & Tricks" forum's "Index of HOWTOs" thread for the kernel-compiliation threads. I cannot recall which, but one of them is pretty friendly and shows you how to get .deb files built.
> Does ubuntu get my ipw2200 intel wireless card working quickly?It may. Depends on if your card is supported by that module, but you might need to install it yourself. I'm not the one to ask about this.

[size=1]Apologies if I made any mistakes...[/size]

---

### Post by asterix404 on 2005-10-06
No actuilly that sounds about right, and GDM isn't the same as gnome. GDM is just your login manager and is gentoo you can edit that by going to /etc/rc.conf and changing your start session to "fluxbox" as opposed to "Gnome" or "kde". I am more concerned with the card though, I know it has support but in gentoo it doesn't seem to work and I am wondering if my switch will. Thanks though.

---

### Post by Ryujin on 2005-10-06
One of the problems I have faced with Fluxbox is the ubuntu dependencies in apt, many programs install a lot of gnome stuff when it is unessesary, on systems that I run with Fluxbox I use Gentoo or Arch, they are better for minimalism and streamlined kernels, as for the IPW 2200 the driver is in Brezzy Badger Kernel, it atodetects mine in the install

---

### Post by duminas on 2005-10-06
What about the **--ignore-depends** flag for dpkg when you install certain programs, Ryujin?

---

### Post by ygarl on 2005-10-06
Ummm - I just searched for Fluxbox on Synaptic, installed all the stuff I wanted and it just worked.. Menus are almost completely bare, however so YMMV...

---

### Post by SilentCacophony on 2005-10-06
Hello. Regarding setting up a fluxbox desktop cleanly, it's not terribly difficult. I've done it before. To my knowledge, the best way to do that would be to do a minimal 'server' install, and then install only those packages that you want after that. That way, you get none of gnome installed unless you install packages which require it. A good way to browse the repositories and check dependencies is with the **aptitude** package manager, which is installed by default.

There is a [wiki]("https://wiki.ubuntu.com/Installation/LowMemorySystems") page that describes how to do so. Since fluxbox is in the universe repository, you'd want to check out the unofficial [ubuntuguide]("http://www.ubuntuguide.org/") on how to add extra repositories.

After the 'server' install, I'd install these packages to start with:

menu (if you want an automatic menu of installed apps)
x-window-system-core
xscreensaver (optional)
fluxbox
fbpager
fbdesk (if you want desktop icons)
fluxconf (optional config frontend)
xterm or wterm or eterm or ...

Choose a file manger (I like rox), browser, mail client, etc. You might want power management (acpid, apmd), or some dockapps. There are plenty of choices. You can make an ~/.xinitrc file to start up the wm and apps with startx, or install wdm or xdm.

If you've dealt with debian before, you'd be on familiar ground. If not, it might be an interesting learning experience. :)

---

### Post by asterix404 on 2005-10-06
hehehe thanks alot, I don't think I have delt with debian but I have wanted to... I think I will do it this weekend. Thanks a lot Ben

---

