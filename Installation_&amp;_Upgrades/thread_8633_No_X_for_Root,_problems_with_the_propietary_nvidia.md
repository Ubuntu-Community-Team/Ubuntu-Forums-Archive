---
title: "No X for Root, problems with the propietary nvidia driver (and other stuff)"
date: 2004-12-19
forum: Installation &amp; Upgrades
---

### Post by fhd on 2004-12-19
I know that this could better fit in another forum, but I want to announce some more problems I experienced in the same thread, because I'm not feeling good while opening three threads at the same time, so here are my problems:


First of all, I want to deactivate the beeping on pressing backspace with nothing to delete in x and vterms, can you tell me how I'll do this? I forgot it.

I want Ubuntu to stop opening nautilus whenever I mount something in a xterm, how can this be done?

Now another strange problem: When I try to start X applications as the superuser, they just wont start, here's the output:
```

# DISPLAY=":0.0" xeyes
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :0.0

```

well as a normal user, it works.
Sadly, I cannot configure gdm like this, neither starting it in a shell, nor starting it through the Gnome-Panel.

I also had to set my root password booting and chrooting in from a livecd, is it part of ubuntus philosophy not to have control of the root user? I found some ubuntu documentations, they were all using sudo, and the installation manager did not ask for a root password during installation.


And now my strange nvidia problems (they're probably not that strange)
I got some stuff, nvidia-glx, nvidia-kernel-common, linux-restricted-modules-2.6.8.1-4-k7 and nvidia-settings, I followed the ubuntu starters guide to use it, but it just doesn't work, XFree doesn't seem to be able to load the nvidia module, replacing the driver nv with nvidia keeps my Xserver from starting up, and nv is not the driver I want.

Am I doing anything wrong/can you advise me how its done?


Thats it so far, until now I'm very confortable with ubuntu, I never saw a so beginners-friendly distribution, though I have to get used to it, much seems to be best done through guis here, and I'm not used to guis.

[edit]
I managed to find out how to change that terminal beepin, it's related to a line in /etc/inputrc, or shoul d I say it "was"? ;)
[/edit]

[edit]
Well, I come to serve myself very well, another problem is solved; I got the nvidia module finally installed, I got myself the restricted kernel modules from apt again after purging the old ones, something nasty seemed to has happened to my /lib/modules, no the nvidia module is present, and everything works just fine.


But still something todo; the automatic mounting of Ubuntu really IS great, I would love to set this up myself on another of my boxes, Whenever I input new media, it automatically mounts and opens up a nautilus window with  the content. It's great.
But I hate it.
I want to deactivate it, I don't want unexpected windows to pop up whenever I mount something, BUT I want to set it up on my girlfriends sarge, How can this be {ac,deac}tivated by me?

And I still need to start X Stuff as the root user... ok, I don't need it, it would just be very nice.
Help is still appreciated.
[/edit]

[edit]
I now did it, found the gnome-volume-manager who's responsible for that automounting and deactivated it all (using the gconfd gui), though got and activated it on my girlfriends debian.

Don't worry, I'll delete this post if I can solve my last Problem; No X without sudoing.
[/edit]

---

