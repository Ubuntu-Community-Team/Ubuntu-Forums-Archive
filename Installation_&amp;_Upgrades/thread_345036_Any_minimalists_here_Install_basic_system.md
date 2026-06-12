---
title: "Any minimalists here? Install basic system ?"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by neoflight on 2007-01-23
Hello folks,

(Please ignore my post counts..still working...)

I would like to know whats the minimal installation i couldt have from ubuntu gnome desktop?
I am in the process of overhauling my installations here...

i have one thought here: Does ubuntu server installation + ubuntu-desktop look like a good option to get a minimalist env..?

By minimal i mean, the system + basic browsing capabilities, networking, acroread, word processor and a simple text editor.... 

i am stuck with the dependency hell while deleting stuff of 6.10 desktop and there are hundreds i am still scared to remove from my now-stable-system.

I would also like to know whether you are a minimalist or not...please vote...

If you are a minimalist, how did you do it?

---

### Post by yabbadabbadont on 2007-01-23
If you install ubuntu-desktop, you will end up with the same setup as if you had done a regular ubuntu install.  Personally, I use the alternate install cd to do a server install in expert mode.  I then strip out some of the crap included in ubuntu-standard (which it seems to always install, no matter what I try).  Then I add Xorg, Fluxbox, Firefox, Thunderbird, xine (and codecs), xmms, and finally gkrellm with a couple of plugins.

---

### Post by aysiu on 2007-01-23
yabbadabbadont is right. If you install *ubuntu-desktop*, that's not a minimal install at all.

My advice would be to do a server install, enable extra repositories, then install only a little bit more: ```
sudo aptitude update
sudo aptitude install icewm x-window-system-core dillo acroread kword mousepad menu xterm gdm synaptic gksu
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
``` You can always use Synaptic to add more stuff later, but that should get you a **very** basic system.

---

### Post by yabbadabbadont on 2007-01-23
> **aysiu said:**
> yabbadabbadont is right. If you install *ubuntu-desktop*, that's not a minimal install at all.

My advice would be to do a server install, enable extra repositories, then install only a little bit more: ```
sudo aptitude update
sudo aptitude install icewm x-window-system-core dillo acroread kword mousepad menu xterm gdm synaptic gksu
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
``` You can always use Synaptic to add more stuff later, but that should get you a **very** basic system.

Won't gdm and synaptic pretty much pull in half of gnome anyway?  It want's to pull in 65 packages when I simulate it with aptitude.  (actually, gnome-core would pull in 128...)  By the way, you wouldn't happen to know why none of the window manager deb files have a dependency on x-window-system-core?  They are useless without it, so I would think that it should be listed as a dep...  (I know you're not a dev, but I figured it wouldn't hurt to ask.   :D)

---

### Post by aysiu on 2007-01-23
Even with the packages GDM and Synaptic pull in, you'll have a very minimalist installation. They were just a suggestion. You don't really need them, and you can leave them out.

As for why x-window-system-core isn't a dependency of IceWM... no idea.

---

### Post by veli on 2007-01-23
I'm a minimalist too, regarding Ubuntu I mean, :-).

This is what I've done:

[http://doc.gwos.org/index.php/LightweightGnome](http://doc.gwos.org/index.php/LightweightGnome)

I'm trying to go down and down in terms of memory usage. With the above set up you could run Gnome at 60-70 MB when idle. But I have fully functional desktop, Office, multimedia, photo management, compiling tools, etc. The installed packages now are about 860. There were less than 700 after the fresh install, but I made kernel compiling, XFCE 4.4 compiling from source, so the number boost up a bit.

---

### Post by neoflight on 2007-01-24
Thank you so much for the posts...

I will try those and post back in a day or two after I do a complete backup. :)

EDIT: btw, is there any commmand i can use to get the number of packages i have in my system? thanks
edit again: I got it....it can be obtained from Synaptic > status (in the left-bottom tab)> installed (details in the status bar at the bottom)

---

### Post by szymon_g on 2007-01-25
you can try a ubuntu 6.12 "elokwentny emu" - "eloquent emu" from this site

[http://forum.ubuntu.pl/viewtopic.php?t=21274](http://forum.ubuntu.pl/viewtopic.php?t=21274)

it's (i mean : page) is in polish, but you should not have any problems with understanding it.
profesional version is really similar to 'debian base' installation- you have got only console programms, no X :-)

if you do not like hardcore like that, you can try to install 'standard (live or alternate) version of ubuntu, eneble sources in sources.list, install icewm + rox +whatever ya like :-) and write this command :

[http://forum.ubuntu.pl/viewtopic.php?t=17093](http://forum.ubuntu.pl/viewtopic.php?t=17093)

it should remove about 800mb of space. you will have a xserver, usefull programs like ooffice, but ya'll be able to delete/add new.

---

### Post by neoflight on 2007-06-15
i tried both ubuntu and debian... the most minimal system i couuld get was from debain. ..theoretically there should not be any difference...i guess its simply because debian permits me the choice to select what type i need ...installing everything and removing stuff after is a painful process....

---

### Post by Gremlinzzz on 2007-06-15
Have you tried Xubuntu then uninstall the things you wont use.

---

