---
title: "How NOT to download updates right away?"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by Kung! on 2005-11-10
Hey all.  :)  I've been using Ubuntu on my laptop (a Dell Latitude C600) for about a month now - it runs one heckuva lot better than XP or 2000 ever ran, that's for sure.

HOWEVER...I can NOT get it to run on my home computer no matter what I do, and for a somewhat inane reason, I suppose...it installs wonderfully, UP UNTIL the point where it reboots and attempts to download updates and such from the internet.  At that point, it just sits there and looks at me.

I expect a bit of difficulty even WHEN I am able to boot up into it, because my 'Net connection is via Starband, a satellite internet provider.  But I'd at least like to be able to boot up into it to mess with it myself.  Is there any way I can bypass the automatic downloader/installer?

---

### Post by starscalling on 2005-11-11
im fairly new myself...
but as i recall you have to give it permission to do the updates
make sure you uncomment your /etc/apt/sources.list for the deb [http://.](http://.).... and deb-src [http://.](http://.).. for when you DO want to do the upgrades. 
unless of course your talking about some point in the middle of the installation process... in that case why not take the hard core route and just unplug it // disable the card or something? remember linux is about giving YOU the power to do what you want to! 
so: install. let it reboot. let it do the installs of the actual operating system. then log in to gnome and edit your network connection or browse or explore or whatever you want to!

---

### Post by Kung! on 2005-11-11
That's the problem - there should be some way to 'escape' out of it.  (And yeah, it's in the middle of the install process.)  I mean, I've seen the standard Debian menu before; this is a bit more automated than older Debian installs, but you would think there would be some sort of way to escape to the standard menu, and just continue on with the rest of the install process, skipping that step.

---

### Post by Basu on 2005-11-11
I suggest that you just unplug the cable and let things go. If there isn't a net connection then Ubuntu should just go on. When I first installed Hoary, I had a softmodem that wouldn't work and so I didn't download any upgrades during install, and manually put things in when I got a broadband line. (Of course I screwed up Xorg so now I'm going to fresh install Breezy, but that's another matter altogether)

---

