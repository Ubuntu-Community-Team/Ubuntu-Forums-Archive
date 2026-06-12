---
title: "[SOLVED] Reinstalling essential Ubuntu packages"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Dan++ on 2008-05-26
I'm on Hardy.

In the process of uninstalling apache2 (used sudo apt-get purge), I somehow stumbled upon a way of uninstalling basically everything. It came up with a "use apt-get autoremove" message and then, quickly, went through a list of packages it was going to remove. They included amarok, compiz, python, eclipse just to name a small fraction. Basically a bunch of packages I wanted to keep because I use them.

Luckily, before it was too late I managed to stop a lot of them, but a lot were still purged. Unfortunately this included whatever it is which makes me able to get on the net, which I think was part of ubuntu-desktop (which I saw being removed when it was too late)

I've inserted the Ubuntu Live CD, is there a particular way I can basically just reinstall everything that was installed when I first put that CD in to install Ubuntu the first time, without losing all my files and packages?

Thanks.

---

### Post by PmDematagoda on 2008-05-26
When you boot Ubuntu in Recovery Mode, are you able to reinstall ubuntu-desktop(I know you need the internet connection, but did you try to see if it's still available in the terminal)?

---

### Post by Dan++ on 2008-05-26
Thanks for your reply :)

I went into recovery mode and tried it, it told me that there was no installation candidate available but there was a reference to it in another package. I also tried repairing broken packages but none were broken, and also fixing xorg, and that just said it might be overwriting settings.

So then I continue with normal boot, and log in, and I'm given nothing but the human theme orangey background with my mouse pointer. I have a feeling this is something to do with X, no?

EDIT: Also, I can open a terminal using the shortcut key I assigned it to (CTRL+ALT+KP_ENTER) but I don't really know what to do there.

---

### Post by Dan++ on 2008-05-26
Forgot to mention that I can open terminal from the screen which doesn't seem to load.

---

### Post by sisco311 on 2008-05-26
Insert your installation disc and type:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Dan++ on 2008-05-26
Thanks :) This doesn't work with the live CD. Is it possible it'll work with the alternate install CD? I've just finished downloading that and it's burning now.

---

### Post by aysiu on 2008-05-26
The Desktop CD (or live CD) does not contain a lot of packages. The Alternate CD contains all the default packages. If, however, you're connected to the internet, you should be able to just install from there instead of using CDs.

```
sudo nano -B /etc/apt/sources.list
``` Make sure there are no # signs in front of what look like web addresses. If there are, delete them. Then save (Control-X, Y, Enter). ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by Dan++ on 2008-05-26
> **aysiu said:**
> The Desktop CD (or live CD) does not contain a lot of packages. The Alternate CD contains all the default packages. If, however, you're connected to the internet, you should be able to just install from there instead of using CDs.

Unfortunately, the network card driver (presumably) was one of the packages deleted and I can't connect to anything at all :( Thank you for the suggestion though.

The alternate CD is almost done, hopefully it'll do the trick. I'll post here with results.

Thanks everyone :)

---

### Post by Dan++ on 2008-05-26
Okay, so: Good news is, I've got the Internet back. I inserted the alternate CD and installed ubuntu-desktop and that all worked fine.

The **bad** news is that when I log in there's still just the blank orange background. I can open terminal though, and it's updating from sources on the net. Also I opened nautilus and that's working but the GTK theme is just the default blue gnome one, rather than Ubuntu's Human.

Any ideas? Thanks so far everyone :)

---

### Post by Dan++ on 2008-05-26
I hate to bump, but I feel I'm close. Does anyone have any ideas?

Basically, the problem is: **Ubuntu is loading and I can log in and open things through terminal (if I use my terminal keyboard shortcut), but the panels won't load and the theme is this blue one instead of Ubuntu's Human.**

---

### Post by newbreed on 2008-05-26
wouldn't you feel better with a fresh cup?..no expert but after screwing all that up, regardless how many you saved, I'd just do a fresh install of hardy...:)

---

### Post by sisco311 on 2008-05-26
You should start a new tread.

---

### Post by Dan++ on 2008-05-26
@newbreed: Yeah, that's what I reckon I'll have to do anyway. But due to Windows being a boot-hogging loser I've had to reinstall three times in as many days, so I kinda want to avoid it. Having said that, I suppose by now I know the routine of how to get it working exactly how I like it, plus I hopefully will learn from my mistake (apt-get purge is a powerful and dangerous tool).

If nobody has any ideas I'll do that, as I've backed up my home folder onto my other hard disk. I'd like to know how to fix this problem in case there's a scenario where a fresh install isn't really an option. Plus, I kinda want to know what package it is that controls the panels.

Thanks :)

@sisco311: You mean thread?

---

### Post by sisco311 on 2008-05-26
> **Dan++ said:**
> @newbreed: Yeah, that's what I reckon I'll have to do anyway. But due to Windows being a boot-hogging loser I've had to reinstall three times in as many days, so I kinda want to avoid it. Having said that, I suppose by now I know the routine of how to get it working exactly how I like it, plus I hopefully will learn from my mistake (apt-get purge is a powerful and dangerous tool).

If nobody has any ideas I'll do that, as I've backed up my home folder onto my other hard disk. I'd like to know how to fix this problem in case there's a scenario where a fresh install isn't really an option. Plus, I kinda want to know what package it is that controls the panels.

Thanks :)

@sisco311: You mean thread?
yep. sorry for the typo.

---

### Post by Dan++ on 2008-05-26
Okay, decided to go for a fresh install and now it's all good. Thanks for all your help, everybody :)

---

