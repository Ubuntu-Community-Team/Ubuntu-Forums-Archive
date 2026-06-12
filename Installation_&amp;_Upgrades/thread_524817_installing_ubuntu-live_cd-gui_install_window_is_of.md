---
title: "installing ubuntu-live cd-gui install window is off my screen"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by tommason on 2007-08-13
Hey,
I have been trying to install ubuntu on an old pc of mine...the live cd works absolutely fine until i try and run the install program, that seems to work fine, but the bottom half of the window is off the screen. I've tried maximising (it doesn't) resize window (it is at its smallest size and won't reduce further) tabbing (doesn't seem to want to get to the 'next' button)

I have a widescreen flat monitor (1440x900-19inch) which is connecting to my pc via an analogue cable - the only screen resolutions i can get is 800x600 or 640x480 which is why the problem is there. In 'blocked drivers' or whatever it's called it mentions a nvidia driver that it is preventing from being used. I try to force it to use it, it downloads something, attempts an install and then says 'can't do it' (pardon my lack of jargon)

Any ideas? (I am downloading the alternate cd as we speak, but wondered if there was a simple fix to this)

Cheers!

Tom :)

---

### Post by logos34 on 2007-08-13
> Any ideas? (I am downloading the alternate cd as we speak, but wondered if there was a simple fix to this)

sudo dpkg-reconfigure xserver-xorg

choose another video driver--try 'vesa' first.  accept defaults on pretty much everything else.  Then,

ctrl+alt+backspace

to reload the desktop.  Go to prefs>screen resolution and change the settings

OR

you can right click the panels and change the properties--align the top panel to the left and the bottom status bar to the right.  That will usually allow you to see just enough of the 'forward' and 'back' buttons at the bottom of the screen to preoceed with the install.

---

