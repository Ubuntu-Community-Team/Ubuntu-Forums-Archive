---
title: "Various problems since upgrading to Feisty"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by rrwo on 2007-05-02
I've noticed various problems or weird behaviours since upgrading to Feisty (some of these I've already posted about in other messages):
[LIST=1]
[*] LaTeX runs dreadfully slow. I've no idea why it takes so long to process files.
[*] Evince usually crashes when viewing dvi files.  Sometimes it does, sometimes it doesn't.
[*] The Adobe Flash plugin crashes Firefox -- or at least Firefox sometimes crashes when
  viewing siteswith Flash. Again, sometimes it does, sometimes it doesn't.
[*] Intermittent network problems. It claims to get an address from DHCP server, but never actually does. Wired and wireless both have these problems. Again, randomly.
[*] Sound usually only works if I start from a cold boot. A warn boot or resume doens't
work, usually.
[*] Only one resolution is available. Since I use a widescreen monitor, this is a problem
when I want to plug my computer into a projector that can't handle widescreens.
(Presumably this is a change to the xorg.conf, but I'm curious as to why the default
install no longer gives other reoslution options.)
[*] XEmacs cannot mark regions anymore. I've had to switch to plain Emacs, which also had
the same problem but at least a configuration option fixed that. Alas, Emacs doesn't play nicely with the clipboard, so it's a pain to past to/from Emacs and another application.
[*] When I login or resume, it always starts on Desktop number 2. Why?
[*] Tomboy is in my startup, but sometimes it starts as an applet, othertimes it gives me the search notes dialoge.
[/LIST]

It seems Feisty has broken more things than it's fixed.  I'm not about to downgrade, but I'd really like to fix a lot of these.  It's hard to keep track of all of the threads for these.

---

### Post by laser_in_your_eye on 2007-05-03
I'm having the same kinds of problems after upgrading to feisty...

openoffice is slower than ever
firefox locks up periodically
vmware server takes forever to refresh from pause mode
etc

does anyone have any suggestions?  i'd prefer not to do a fresh install, especially if similar problems are occurring there.

---

### Post by rrwo on 2007-05-03
I should add that these are the problems from a fresh install.

When I upgraded, the system was so unstable and kept crashing.

I had temporarily switched to Debian Etch but was having the similar problems with sound and wireless.

---

### Post by rrwo on 2007-05-03
I hate cross-posting, but [changing video drivers seems to have helped a bunch of these problems]("http://ubuntuforums.org/showthread.php?t=431509").

---

### Post by SteveHoffmanUK on 2007-05-03
My Feisty problem has also been random: An external USB hard disk, which worked fine in Edgy, was sometimes recognised and sometimes not by Feisty - seemed to be no discernible pattern. I gave up and reverted to Edgy, but Edgy didn't recognise my wireless, so I have now reverted to Dapper! Everything works fine in Dapper.  Also, VMWare wouldn't install in Feisty.

I am deeply unimpressed by Feisty.

---

### Post by louieb on 2007-05-03
I have problems with fast user switching in feisty. Something I use quite a bit. So went back to Dapper on that machine. Recently had trouble with hang up at boot time on the laptop. Reinstall the latest Linux-image and took off the quiet splash options from the GRUB configuration file and haven't had a problem since.   

Read where Gutsy is going to be a fix and stabilize it type of release. Not much new stuff.  After Edgy and Feisty I guess the Ubuntu folks decided its time to go back and fix some stuff.

---

### Post by veloce on 2007-05-03
Whereas my upgrade from Edgy to Feisty has been almost trouble free.

Network switching from wired to wireless is now completely automatic.

Dual monitors is easier and better.

vmware server shuts down cleaner

It's great.

---

