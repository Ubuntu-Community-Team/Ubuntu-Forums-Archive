---
title: "bulk updates: a bad idea? (gnome desktop won't load)"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by chrubble on 2008-01-16
I'm pretty new to linux, and I recently installed Ubuntu 7.10 on an older Thinkpad T30.  Everything was workiing perfectly fine, but since Update Manager was notifying me a large (170+) number of updates available, I just did them all in one big batch- in hindsight, perhaps not a great idea.  Upon reboot, first I had problems with cupsd hanging, so I disabled that in init.d.  Now, I can get to a login screen, but after logging in, all I get is a blank Gnome desktop with a mouse pointer- no toolbars, menus, or icons- and it just hangs there.

I guess I have two questions:
- This may be a stupid question, but so do people generally just update individual apps and libraries based on need, or do you put faith in the update and package manager, and load all updates that are available?  I was only loading packages from the official Ubuntu repository.  

- what do I do now?  How do I troubleshoot this situation where I have a blank gnome desktop?  I can get to a text terminal with Ctrl-Alt-F1.  I've tried uninstalling and reinstalling ubuntu-desktop via apt-get.  But I don't know what logs I can look at that might help debug this.

Any help would be appreciated.

---

### Post by zvacet on 2008-01-17
It is a good idea to download updates wich comes from official repos,because most of the time they are security nature.Of course they are trusted third party repos like medibuntu.Basicly download them all and you will not make mistake specialy if you use only official repos.For second maybe it is video driver so try
in terminal

```
sudo dpkg-reconfigure xserver-xorg
```

and select **vesa** driver.When you are finish you should have elementar grapfic and then go search for driver for your card.

---

### Post by chrubble on 2008-01-17
Hi,

Thanks for the reply: I'm pretty sure it wasn't the graphics driver, as I was able to start up a full gnome desktop by typing startx from Recovery Mode.

I've ended up just reinstalling Ubuntu altogether.  I guess I'm still a little nervous about doing that whole set of updates, but I'll probably do them in a couple of small batches so I can see when it goes wrong.

---

### Post by Tensai_Lin on 2008-03-03
chrubble, 

Did you ever figure out what updates caused this. I've been moving between Ubuntu and Fedora on a single machine and had this exact problem happen in both of them. I eneded up just re-installing Fedora and leaving ubuntu off because it took too long to install both, but if you've solved it that would help me a lot!

---

