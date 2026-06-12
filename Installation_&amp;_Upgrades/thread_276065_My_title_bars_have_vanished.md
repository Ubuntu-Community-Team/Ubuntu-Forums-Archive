---
title: "My title bars have vanished"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by wishartz on 2006-10-12
I updated ubuntu last night and now all my title bars on my applications have vanished.  I've tried looking in the view options in the menu of each app, but it isn't that.  It's really frustrating.  When I open up gnome-terminal it fixes itself to the top left of the screen, but I cannnot move it anywhere because there is nothing to grab on to.

It isn't just gnome apps that are doing this it is everything.  When I load firefox there is a menu, but no title bar.

Can anybody help please?

---

### Post by Kateikyoushi on 2006-10-12
Maybe something wrong with the theme ?

System >> Preferences >> Theme.

Are you using compiz ?

---

### Post by wishartz on 2006-10-12
I was using compiz, but my update broke it.  Now I've just gone back to using Gnome instead of XGL.

Mind you, I hadn't updated my packages for months.

---

### Post by Kateikyoushi on 2006-10-12
That explains it, seems it happened few months ago to some.

[Look here]("http://www.ubuntuforums.org/showthread.php?t=228672&highlight=no+title+bar"),

---

### Post by wishartz on 2006-10-12
Do you know how I can fix it?  I've tried to remove compiz but it wont let me I get the message

E: /var/cache/apt/archives/compiz-core_0.0.13.38-0ubuntu3_i386.deb: trying to overwrite `/usr/bin/compiz.real', which is also in package compiz
E: /var/cache/apt/archives/compiz-gnome_0.0.13.38-0ubuntu3_i386.deb: trying to overwrite `/usr/share/gnome/wm-properties/compiz.desktop', which is also in package compiz

I've tried using sudo apt-get remove compiz and synaptic.

---

### Post by wishartz on 2006-10-12
I managed to fix the problem by running this command:

metacity --replace 

Thanks for the help

---

