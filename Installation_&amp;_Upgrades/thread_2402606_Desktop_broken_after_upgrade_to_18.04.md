---
title: "Desktop broken after upgrade to 18.04"
date: 2018-10-02
forum: Installation &amp; Upgrades
---

### Post by voytekl on 2018-10-02
Hi all,

Looking for some help diagnosing an issue with desktop breakage after upgrade from Ubuntu 16.04 to Ubuntu 18.04.

The upgrade was ugly, and I lost a lot of packages, and had to rebuild a lot of stuff manually. I have most things working, but something is very wrong with the desktop GUI. I have the following symptoms.

1. GDM totally broken. Sets up a crash loop when installed and enabled. Nothing that looks like an error condition in /var/log/Xorg.0.log or /var/log/syslog. 
2. LightDM does work. However the only desktop I can get into without it crashing immediately is XFCE. Gnome shell on both Xorg and Wayland insta-crashes, and throws me back to the greeter, as does Unity. LWM never loads a desktop and I am stuck with a blank desktop and mouse cursor. Similarly nothing that looks like an error condition in /var/log/Xorg.0.log, ~/.xsession-errors etc in these cases.
3. OpenGL broken once I do get into XFCE. glxinfo gives 'Error: couldn't find RGB GLX visual or fbconfig'. I wonder if the heavier windowing systems depend on it, so hence them breaking?

I've tried purging all packages I can think of relating to Xorg, Gnome etc. and then reinstalling, hoping it will bring in any dependencies I've lost if that's it, but that doesn't help.

I should note it's an older card (AMD 5850) which has given me driver support issues in other contexts. 

At a bit of a loss after much playing around so any tips about next steps would be appreciated.

---

### Post by voytekl on 2018-10-02
Ok made some progress. OpenGL now working, which also fixed Unity.

Problem was something to do with package versions being broken due to the upgrade. I noticed libglx-mesa0 wasn't installed, and when I tried to install it I got 'libglx-mesa0 : Depends: libglapi-mesa (= 18.0.0~rc5-1ubuntu1) but 18.0.5-0ubuntu0~16.04.1 is to be installed'

I needed to do the following to make libglapi-mesa the right version:

```
sudo dpkg --remove --force depends libglapi-mesa phonon4qt5
apt install libglapi-mesa phonon4qt5
apt --fix-broken install
sudo apt install libglx-mesa0
```

Not sure if there are more of these out weird situations out there, and not sure how to find them. Still no idea how to approach the gnome stuff not working either.

---

### Post by voytekl on 2018-10-02
Ok, I'm now logging into Gnome shell. 

Thanks to [https://feeding.cloud.geek.nz/posts/debugging-gnome-session-problems-on-ubuntu-1404/](https://feeding.cloud.geek.nz/posts/debugging-gnome-session-problems-on-ubuntu-1404/) which showed me how to get better debug info from gnome session failure.

And [http://pjk.scripts.mit.edu/pkj/2017/04/16/gnome-a-tale-of-a-dead-fail-whale-with-a-happy-ending/](http://pjk.scripts.mit.edu/pkj/2017/04/16/gnome-a-tale-of-a-dead-fail-whale-with-a-happy-ending/) which showed me the fix for the problem that popped up in the xsession-errors file. The file /usr/share/xsessions/ubuntu.session needed to be created.

I've checked back now and gdm3 is also now working. Not sure which part of the process fixed it. But as it stands, all is well.

---

### Post by slickymaster on 2018-10-02
*Thread moved to **Installation & Upgrades**.*

---

### Post by ajgreeny on 2018-10-02
If this is now solved to your satisfaction please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

