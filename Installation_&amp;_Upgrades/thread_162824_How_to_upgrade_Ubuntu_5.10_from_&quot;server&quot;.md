---
title: "How to upgrade Ubuntu 5.10 from &quot;server&quot; installation mode to default installation?"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by cefs99 on 2006-04-19
Hi,

I'd installed Ubuntu 5.10 with "server" installation mode only which means it's a minimized installation, no gnome etc. Now I just want to install gnome etc to have a GUI installed instead of adding the rest open office etc. How can I upgrade my 5.10? The installation CD does NOT have a upgrade option. and I dont want to reinstall everything. Is there a way for me to install Gnome and necessary session-manger, desktop manager and window manager etc ONLY so I can install firefox afterwards? I am bit lost in so many Gnome or X related packages.... 


TIA,

L

---

### Post by Jagot on 2006-04-19
sudo apt-get install ubuntu-desktop

Firefox is part of the default installation.  I don't believe you can obtain GNOME with Ubuntu without installing FF, though I could be wrong.

---

### Post by Nequeo on 2006-04-19
[QUOTE=Jagot]sudo apt-get install ubuntu-desktop

Firefox is part of the default installation.  I don't believe you can obtain GNOME with Ubuntu without installing FF, though I could be wrong.[/QUOTE]

You could try 'apt-get install gnome-desktop-environment'.

It's in the Universe repository, so might not work/integrate perfectly. If you're not quite comfortable with Linux yet you might be better off installing ubuntu-desktop as Jagot described and then 

'apt-get remove firefox' etc... until the bits you don't want are stripped away. Just be aware that this will also remove the meta package 'ubuntu-desktop'. So if at any future point you do a dist-upgrade to Dapper, you'll need to reinstall 'ubuntu-desktop' first to make sure you get the complete upgrade. 

Cheers,

---

### Post by Sef on 2006-04-20
> ...ONLY so I can install firefox afterwards?

You don't want to remove firefox.  There are dependecies in it that will screw up your system if it is taken out.

---

### Post by cefs99 on 2006-04-20
Thanks guys. It works! The only con is though it would make more sense if Ubuntu has a GUI package without application such as OO, multimedia and game etc.

---

