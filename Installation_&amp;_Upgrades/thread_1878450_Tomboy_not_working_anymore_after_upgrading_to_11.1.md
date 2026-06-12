---
title: "Tomboy not working anymore after upgrading to 11.10"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2011-11-09
When I start Tomboy I get the icon in the launchbar.

ANY of the items of Tomboy work! So I tried to start Tomboy from the command line, and it is the same.

I tried even:
tomboy --start-here
tomboy --new-note

All these only adds the icon to the launchbar and one line to the command line:
[INFO 09:13:33.684] Initializing Mono.Addins

Any idea how to fix that?

bye

Ronald

---

### Post by ELMIT on 2011-11-10
I replaced Tomboy with Gnote.

How can I use it with Ubuntu One? So that I can share my notes on different computers?

---

### Post by directhex on 2011-11-10
> **ELMIT said:**
> I replaced Tomboy with Gnote.

How can I use it with Ubuntu One? So that I can share my notes on different computers?

Despite all the anti-Mono people going on about how Gnote is a replacement for Tomboy, Gnote has **no** online note sync. Never has.

---

### Post by ELMIT on 2011-11-10
Nevertheless I solved it:

mv ~/.local/share/gnote ~/Ubuntu One
ln -s ~/Ubuntu One/gnote ~/.local/share/gnote

;-)

---

