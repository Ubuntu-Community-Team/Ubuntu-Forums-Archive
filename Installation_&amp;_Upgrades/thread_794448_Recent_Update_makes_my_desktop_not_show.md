---
title: "Recent Update makes my desktop not show"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by s3a on 2008-05-14
I can do absolutely anything normally on my comp but I just can't click on my desktop or even see any of the files/folders on it!! All this happened right after I installed updates on my comp! I restarted comp several times so thats not the problem. Please Help!

Thanks!

P.S.
Wallpapoz still works nicely but I can't see or click on anything on the desktop.

---

### Post by ThomasKloos on 2008-05-14
I am having the same issue. Just did the latest updates a few minutes ago, and now I just see my wallpaper. I can right click the desktop and I have a menu, but clicking Change Desktop Background doesn't do anything.

Anyone have any ideas? 

Thanks,
...Thomas

---

### Post by s3a on 2008-05-14
I can't even right click on my desktop!

---

### Post by Caraibes on 2008-05-14
I had a funny issue too... was wondering if my ram was bad... Memtest was ok, so a couple of reboots made it go away... Strange...

---

### Post by VMC on 2008-05-14
> **s3a said:**
> I can do absolutely anything normally on my comp but I just can't click on my desktop or even see any of the files/folders on it!! All this happened right after I installed updates on my comp! I restarted comp several times so thats not the problem. Please Help!

Thanks!

P.S.
Wallpapoz still works nicely but I can't see or click on anything on the desktop.

A little more information would be helpful. Dis you install Harty? How about typing ALT+F2 will that bring up a run command? Did you install this from live cd? AMD64, Intel, etc. Are there icons on your desktop?

---

### Post by s3a on 2008-05-15
This is a hard drive install of Ubuntu 7.10 (Gutsy Gibbon)...not hardy. Alt+F2 works, like I previously said: everything works normally it's just that my desktop icons dont show and I cant click/right click or anything on the desktop. One of the times that I logged in, it gave me an error message 

"Nautilus can't be used now, due to an unexpected error.

Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautlus may help fix the problem."

So there; I see a potential fix for my problem :). So...wat do I do exactly?

---

### Post by djmasters on 2008-05-17
Same thing here, no interactive desktop for any user after upgrading from 7.10.

I get to a login screen, enter username & password, get HH background but nothing else.  No icons, no task bar, no right click.   If I press ctrl-alt-del AND wait about 30 seconds I will get that menu.  Choosing logoff returns me to the background and not back to a login screen.   Subsequent CAD's do nothing.

I can access the command line via alt-f2.   Tried creating a new user, no desktop for them either.

---

### Post by Can0n on 2008-05-18
Same here, no right-click or anything else.

---

### Post by djmasters on 2008-05-18
> **djmasters said:**
> Same thing here, no interactive desktop for any user after upgrading from 7.10.

I get to a login screen, enter username & password, get HH background but nothing else.  No icons, no task bar, no right click.   If I press ctrl-alt-del AND wait about 30 seconds I will get that menu.  Choosing logoff returns me to the background and not back to a login screen.   Subsequent CAD's do nothing.

I can access the command line via alt-f2.   Tried creating a new user, no desktop for them either.


Messed with it some more yesterday and made some slight progress.  All I use this box for is to be a NAS device.  Other than enabling Samba and creating the share where all of my junk is, it's a 100% standard install.   Really don't understand why it puked, but whatever...

Figuring that Gnome is somehow hosed, I tried to install KDE instead.   Install went just fine and chose to use it as my desktop.   System came back up to a KDE login screen.  After logging in, I still get the orange Gnome desktop but it works now for the most part.   There's some funky artifacting going on but it seems to work.   

I would say that lends to validation that something in the update occasionally hoses Gnome.

---

### Post by s3a on 2008-05-21
You could could get Xubuntu or Kubuntu from the terminal and use that instead, back up your data (since you can still access it) then move to hardy...that's what I did and thanks to this person who gave me a .deb driver for my hsf dial-up modem not only am I running hardy but I'm running it in 64-bit! :D

P.S.
If you want to stay with gutsy then just follow the same procedure but re-install gutsy and dont update for a while until it's safe to assume the updates are safe to update to.

---

