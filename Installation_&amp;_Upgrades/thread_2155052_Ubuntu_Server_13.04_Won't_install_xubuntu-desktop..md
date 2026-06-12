---
title: "Ubuntu Server 13.04: Won't install xubuntu-desktop."
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2013-06-16
Hi.

I swear I've been doing this for a long time, but this time was different.

I start with ubuntu-server, this time 13.04.  Then when that's all set up nicely I install xubuntu-desktop (or whatever desktop.)  I went into aptitude, selected xubuntu-desktop, and when I said go it said something like "can't find a reason to install xubuntu-desktop."

Huh?

Can't exactly tell you what the message was because I promptly exited out of aptitude and did it with apt-get install xubuntu-desktop, which worked fine.

Why would aptitude refuse to install xubuntu-desktop?

---

### Post by dino99 on 2013-06-17
Its all about logic: a server is meant to be headless. So if you then want a desktop, why not directly install the usual ubuntu iso ?

[HTML]Can I add a "graphical user interface" (GUI) to a server?

Whilst we don't recommend running a GUI on a server for security and performance reasons, yes you can. Depending on what window manager you wish to use you can install the X Server and the window manager via apt-get. For details see the ServerGUI page.[/HTML]

[https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F](https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F)

---

### Post by 1clue on 2013-06-17
For a couple reasons:
[LIST=1]
[*]This isn't a server completely, it's also a desktop with dual monitors.
[*]I already had server sitting there.
[*]Supposedly, the difference between server and xubuntu is pretty much contained in 'xubuntu-desktop'
[*]Whatever's on the CD is old anyway, so you install the basic server, apt-get update and all that, and then load the gui.
[*]Frankly, if Ubuntu offered a skinnier server then I would use that as my CD.
[*]Lots of times I want something specific, I start with the minimum setup and only put on the apps I want.
[*]I just find it really odd that the package manager would flatly refuse to install something.
[/LIST]

Thinking back on it, I probably always used apt-get install whatever-gui-setup before.

The server image is all you need.  No sense wasting hard disk space on an iso that you don't need, right?

---

