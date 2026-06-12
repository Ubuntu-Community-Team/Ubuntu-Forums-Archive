---
title: "No GUI after upgrading to 9.10"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by krishnamohan on 2009-11-22
I upgraded to 9.10 from 9.04...but now I get only the command line...and cannot run applications like firefox....

It had happened to me once before and then ***sudo apt-get install gnome*** solved the problem..

I tried it this time..but it says

[B][I]gnome:depends gnome-vfs-obexftp but it is not installable

[/I][/B]I had kubuntu desktop installed for 9.04...

Help!!!!!

---

### Post by krishnamohan on 2009-11-22
And yes...I used the alternate cd for upgrading..and allowed it to use the net for packages..

---

### Post by MelDJ on 2009-11-22
try sudo start gnome-desktop or sudo gnome-desktop

---

### Post by krishnamohan on 2009-11-22
Does not help ..
does not recognize command gnome..
 or see any application gnome-desktop..

When I try to run firefox, it says: No display detected

---

### Post by MelDJ on 2009-11-22
did you still keep kde? then try:
sudo start kde-desktop or sudo kde-desktop

---

### Post by krishnamohan on 2009-11-22
I tried startx...

says...

[B][I]Failed to load module Intel

No drivers available

No screens found...[/I][/B]

---

### Post by krishnamohan on 2009-11-22
***sudo apt-get install xserver-xorg-video-intel***


has worked for me.....

---

### Post by krishnamohan on 2009-11-22
Thanks Mel...

---

