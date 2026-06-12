---
title: "How do I do this server+wireless setup+xfce/thunar"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by pikaia on 2008-01-15
Okay.

I just bought an old IBM Thinkpad 600e for $50.  Its got a PII366 and 64MB if RAM.  I tested out several (I think ALL) of the small linux distros and didn't like any as much as Ubuntu (which I run on my desktop).  So I decided to make my own slim-down version.  (DamnSmallLinux would lockup before loading, TinyME-same, Wolvix-same, Puppy was all I could get to boot on this thing and I had too much trouble installing/unistalling/relearning)

So my problem is, how can I install the Ubuntu Server, then get my wireless USB adapter (TEW-444UB) working so I can download and install the GUI and window managers (either Xfce or IceWM?  If possible at all.  Or is there a better (easier) option I'm clearly over looking.  Also does Fluxbuntu use synaptic?

I plan on getting at least a stick of 128MB to bring it up to 192, but until then...

Thanks.

---

### Post by Partyboi2 on 2008-01-15
You could try xubuntu and install it with the alternate cd from [here]("http://www.xubuntu.org/get")

---

### Post by pikaia on 2008-01-15
But for my 64MB of RAM isn't Xubuntu (even the alternate install) still going to be a bit heavy?  I know 64 isn't much to work with but I was hoping for a bit more functionality.  And I am not really pleased with the package abilities of some of the other distros.  I tried Kwort (Slackware+Xfce), and it looks nice and supposed to be made for low resource machines, but it was a real dog.  I tried to uninstall Openoffice from it and have Abiword or another small office variant, but I can't figure out how to uninstall things in Slackware.  Whereas Ubuntu is much, much more intuitive for a recent (eagerly learning ) convert, like me.  

I have read several people's accounts of how they used Ubuntu Server (which gives a minimal framework) and installed a lightweight GUI ontop and it works great... even with very low resources.  

Or I'd like to find a similarly featured lightweight desktop like xubuntu (which I have installed on an old 800Mhz, 384mb box too) but its a bit sluggish on that machine... so I can only imagine it on this *new* laptop.  

I'm not afraid to work the terminal, so setting up initially on Server isn't an issue, but getting ndiswrapper and my wireless adapter to work in Server scares me a bit, but if I can do that, I think installing Xfce or IceWM or an equivalently small, but full featured GUI shouldn't be too bad once I'm online.

I guess in short what I am looking for (hoping for) is a barebones, minimum installation of Xubuntu.  Something that maybe only has Synaptic (or deb installer), internet, and maybe a small music player that is reasonably functional (not a 10 minute wait).  And all without an internet connection... hmm.   Seems like a hell of a mountain to cross...

So if I'm just living a pipe dream... let me know... but a man can dream, and hopefully someone can help.

Thanks

---

### Post by Partyboi2 on 2008-01-15
For xubuntu they say the min is 64mb of ram but suggests better performance with 128. Ther server version requires only 64mb but that is not taking into an account if someone was to install a desktop.
But [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems") is something about low memory systems
and [here]("http://www.psychocats.net/ubuntu/minimal#barebones") is how to install  bare bones

---

### Post by pikaia on 2008-01-15
That HOWTO requires an internet hook up which is the main source of the problem.  This laptop doesn't have a ethernet port, and so from the server I'd need to set my usb wireless adapter AND then set up a GUI. 

I've taken it upon myself to load Debian.  A minimal install of debian (command only) and am trying to install the .deb file of xfce from a cd but it won't mount and install.  I'm getting a bit frustrated.

Can I install the deb file from the usb?  If so how?

---

