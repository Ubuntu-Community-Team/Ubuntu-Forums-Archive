---
title: "Install died four weeks later"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by tommy_kay on 2008-06-10
I installed Ubuntu 7.10 about a month ago.  It wasn't a flawless install, but it partly worked.  I could get the graphical interface and I could dual boot with Vista.

A few days ago I tried to boot Ubuntu, and now I only get a text prompt.  I can't get the desktop to start.  Here is what it says:
[COLOR="RoyalBlue"]
Starting up ...
Loading, please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
kinit: name_to_dev_t(/dev/disk/by-uuid/7a_lotsofletters_999) = sada6(8,6)letters
kinit: trying to resume from /dev/disk/by-uuid/7a_lotsofletters_999
kinit: No resume image, doing normal boot...

Ubuntu 7.10 tom-toshiba tty1
tom-toshiba login:[/COLOR]

I can log in, but this still does not start the graphical interface.  For example, if I type
[COLOR="RoyalBlue"]
sudo /etc/init.d/gdm restart[/COLOR]

then it stops and then starts gnome, but still no graphics, only text. If I type

[COLOR="RoyalBlue"]exec gnome-session[/COLOR] then it says 

[COLOR="RoyalBlue"](gnome-session: 13033): Gtk-WARNING **:cannot open display:

Ubuntu 7.10 tom-toshiba tty1

tom-toshiba login:[/COLOR]


Thanks in advance,  Tom

---

### Post by tommy_kay on 2008-06-10
Tried /etc/init.d/gdm start (and restart, and force-reload) and it responds

[COLOR="RoyalBlue"]* Starting GNOME Display Manager...[/COLOR]

but it doesn't.  What I mean is, I'm still at the command prompt.  BTW, [COLOR="RoyalBlue"]startx [/COLOR]doesn't either.

---

### Post by tommy_kay on 2008-06-10
This seemed to fix it:

[COLOR="RoyalBlue"]sudo dpkg-reconfigure xserver-xorg [/COLOR]

Although this resulted in a "panic" kernel crash, after I pulled the battery it rebooted normally.  And in graphics mode!

So, it's fixed.

This page was helpful: [https://help.ubuntu.com/6.10/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html]("https://help.ubuntu.com/6.10/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html")

Cheers, all.

Tom

---

