---
title: "Why is it recommended to fresh install gnome remix 12.10?"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by sodaa on 2012-11-16
I just installed Ubuntu 12.10 and noticed there wasn't a gnome classic etc. option at the login menu (vaguely remember this being there when I installed 12.04?). I was wanting to use the gnome desktop and came across the gnome remix 12.10, which said:

> 
It is strongly recommended to do a fresh install  however if you prefer to attempt an upgrade instead, first upgrade to  Quantal Quetzal 12.10. Then run the following commands: 
**sudo apt-get install ubuntu-gnome-desktop ubuntu-gnome-default-settings**from [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10)

and was wondering why it is recommended to do a fresh install? What would be the risks in just upgrading? 

Also, how different is this package to just: sudo apt-get install gnome-shell?

---

### Post by xskydevilx on 2012-11-17
> **sodaa said:**
> I just installed Ubuntu 12.10 and noticed there wasn't a gnome classic etc. option at the login menu (vaguely remember this being there when I installed 12.04?). I was wanting to use the gnome desktop and came across the gnome remix 12.10, which said:

from [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10)

and was wondering why it is recommended to do a fresh install? What would be the risks in just upgrading? 

Also, how different is this package to just: sudo apt-get install gnome-shell?

Well, when installing any OS (be it Ubuntu, Arch, Windows or OS X) it is always *recommended *to do a **fresh install**.
The risks of just upgrading can never be foreseen. Some crucial packages can break so it screws up your entire set-up or everything works out fine.
So, most people don't like to chance it and just go with the fresh install.

So to avoid anything *possibly *breaking, that's why it's recommended to do a fresh install on any OS.

Ubuntu GNOME Remix is really built and optimized for use with GNOME (so it contains artwork and stuff like that set-up for you).
If you just install *gnome-shell*, you'll get a similar interface as the GNOME Remix but it might not look or work the same way as it's suppposed to out of the box. (GNOME Shell that is)

So, what I'm trying to say is:
If you want to play it **safe **- **do a fresh install**.
If you want to risk it, just upgrade - **but be aware** - you might break your system.

---

