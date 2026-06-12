---
title: "Gutsy on Parallels"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by pietrob71 on 2007-10-19
I'm trying to install Gutsy on Parallels 5160, but live CD doesn't start and I receive this message:
[IMG]http://pietrob71.netsons.org/gutsy_on_parallels.jpg[/IMG]

Thanks in advance

Pietro

---

### Post by geekparrot on 2007-10-19
I have this exact same problem as well.

My set up:
MacBook Pro 2.33Ghz Intel Core 2 uo
Mac OS X 10.4.10
Parallels Desktop 3.0
Trying to install Ubuntu 7.10 on Parallels

---

### Post by twistednexus on 2007-10-19
Ditto.  I have tried a variety of configurations with Parallels.  If I disable the network, my install hangs earlier when cupsd tries to start.  I can switch screens and kill the cups script, but then it still goes on to hang starting X.

I tried Ubuntu and Xubuntu distributions of Gutsy, both with no success.  Since I just attach the disk image to the server, I don't have to worry about burn speed.  The disk images also both validate as being correct.

I was able to install 6 and 7.04 without incident.  Both have been removed subsequently because I needed the space back.

MacBook Pro, 2.33GHz Core 2 Duo, 2GB of RAM
Parallels 3.0 Build 5160

---

### Post by astronerd on 2007-10-19
Also got this problem on a macbook with the newest parallels installed....

---

### Post by cheshirecat410 on 2007-10-19
Try lowering your video memory level, sound a bit crazy but it worked for me.

---

### Post by thelorax on 2007-10-19
I don't have parallels, but consider doing your install with the alternative install CD, not as pretty, but likely you'll avoid any potential X problems since it's a text based installer (worked fine in VMWare here).

---

### Post by pietrob71 on 2007-10-20
I've searched on google for a solution and I've find some post about this trouble; they suggest to use alternate_iso.
I've tried and I've installed Gusty on parallels without any problem.
I hope this can help who have this problem.
[IMG]http://pietrob71.netsons.org/gutsy_on_parallels.png[/IMG]

---

### Post by pietrob71 on 2007-10-20
Be Carefull! After installation I have launched the installer of Parallels Tools and than reboot; at this point, I have the same trouble (see first post of this thread).
I suggest to use a Snapshot of Parallels to freeze the fresh installation until someone more expert than me will explain us what is the problem and how to fix it.

---

### Post by stecz on 2007-10-20
I'm having some luck here... during boot switch parallels to full screen mode and it will start GDM. After it boots, then switch back to windows mode and you'll continue to work... I've increased the video memory as well. I'm going to start experimenting with lowering it to where it was before.

(this reply was sent from Gutsy using firefox on a Parallels install)..

John S.

---

### Post by stecz on 2007-10-20
After some more experimentation, I'm not sure what to think... the one thing that I've had really good luck with is going into full screen mode and then I can get GDM to start, then I can go into a window mode.  I was very consistently able to get GDM to start in a windows mode, but then it went back to not working (with the only change being changing video memory).


It's intermittent thought because I went back to 16meg of video memory and it was able to start GDM and not I'm back to it not working unless I go into full screen mode.


Oh well, at least there is a work around...


John S.

---

### Post by luigi193 on 2007-10-21
I am on a first Gen macbook running the newest Parallels...

I had the same problem everyone else was having, when I tried to boot, I got a black screen and it resized over and over again.

I did what everyone was recommending, which was lowering the Video Memory to 4 MB (aka the one for my resolution, 1280X800)

I also changed the default resolution to my res, don't know if that had any effect...

All is working now, but I am not sure if I should install parallel tools...

---

### Post by stecz on 2007-10-21
I have parallels tools installed... If I try to boot in a window, I intermittently have the original error described. (more accurately, I can intermittently get it to work). Everytime I think I have a cause and effect for it, it turns out to be wrong....

The system is totally usable if I just boot in full screen mode and then switch to a window if I want to.... Haven't had a single problem with that method.

I'm wondering if I turn off the dynamic window resizing if that helps...

This could be a bug in Parallels...   Has anyone opened an ubuntu bug for this?

John S.

---

