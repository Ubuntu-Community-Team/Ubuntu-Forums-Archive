---
title: "installing xscreensaver in 10.10"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by fresnofred on 2013-01-06
I had gnome-screensaver working great on my older dell laptop, running maverick meercat, which i realize u cannot update anymore.   the screensaver stopped working correctly so i uninstalled it and tried to install xscreensaver.  got all kinds of error messages.  it is not even listed in synaptic anymore. and with software manager i get some error messages.  cannot install with apt-get either.  is there some sort of ppa or other way i can install xscreensaver with ubuntu 10.10

---

### Post by VanillaMozilla on 2013-01-07
I suspect you're kinda outa luck.  Support is waning and/or disappearing entirely.  Gnome and Ubuntu seem to be running screaming from screensavers.  The reason being that there are lots of old bug reports on xscreensaver rotting in the corners.  These may actually be bugs in Gnome power management, or they may not.

Screensavers don't seem to be at the top of the list, but be patient.  Maybe by the 22nd century.

Bummer, because xscreensavers-extra (or whatever it's called) had all the classics, and some of the best ever.

---

### Post by Frogs Hair on 2013-01-07
10.10 is EOL and unless you can find and old package and dependencies your out of luck. See the link for supported releases.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Bucky Ball on 2013-01-07
You are not receiving security updates (or any other updates) which can leave your machine vulnerable. I would move on and forget 10.10.

---

### Post by fresnofred on 2013-01-07
pour me some coffee!  I got it working again.  Here is what I did:
went here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and selected lucid 10.04 lts, went to the bottom of this page and selected "all packages" and let the page load for a minute or so, chose and downloaded gnome-screensaver and used software manager to open it.  it told be it could not install cause it was missing libfxxf86misc1 or some such file.  went back to where the gnome-screensaver package was downloaded from and saw a very similar or the same file.  downloaded the deb and used gdebi to install it.  then went back to gnome-screensaver in my downloaded files and chose software manager to install and it gave me a warning about "trusted sources", but went ahead and installed it and it works good again.
grind me up some coffee beans!!!
PS: meant for lucid but apparently works for maverick if done right!!

---

### Post by VanillaMozilla on 2013-01-07
Yeah, well, it may or may not work.  Some of those locked up my login sessions on two different computers.

I second the thought about your unsupported machine.  I really hate to see people fail to update like that.  I understand the reason, but the new Ubuntu is fine with Gnome fallback, and something tells me they will continue to support that.

---

### Post by Bucky Ball on 2013-01-08
Glad you got it sorted, but it doesn't change the fact that you are running an unsupported release and, security-wise, this leaves you vulnerable. 

Good luck with it. ;)

---

