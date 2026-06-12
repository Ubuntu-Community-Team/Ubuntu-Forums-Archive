---
title: "Software Update Broke KDE in Oneiric"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by dniMretsaM on 2012-02-14
Ok, so a while back I updated some stuff and noticed that it was going to remove KWin and other stuff that is important. The first thing I did was make a backup with Remastersys (before I let the update go through). After it finished, I logged out and then back in and everything was fine, so I figured nothing went wrong. However, yesterday I rebooted and I couldn't log in. So I went to terminal login and checked for more updates hoping they would fix the problem. Well a bunch of stuff updated, I rebooted, but still no dice (a few more things updated to day, but they didn't help either). I ended up adding the Kubuntu Backports PPA and installed the next KDE version, but I'm still stuck with console only. I searched around for similar problems, but I'm browsing with Lynx, so there is a large chance I missed something. Any help would be greatly appreciated.

---

### Post by jerrrys on 2012-02-14
Don't know if it works in kubuntu, but in terminal:

startx

Also since your in tty will "Ctrl Alt F7" give you a desktop?

---

### Post by drmrgd on 2012-02-14
When you say you can't log in, what is happening?  Is it just returning you back to the log in screen, giving you a black screen, or something else?  Also, out of curiosity, what video card do you have?

I'm not sure if this is at all related to your problem, but a Kubuntu update a few weeks ago left me unable to get a graphical log in as well (although I can't quite remember my symptoms either).  I was able to fix it by uninstalling and reinstalling my video drivers from another TTY. Maybe this the same problem for you?

---

### Post by dniMretsaM on 2012-02-14
Already tried startx, but that brings me back to the terminal with no real error code. When I say "can't login" I mean that it returns back to KDM. As for my video card, it's a 9 year old Intel something. I highly doubt it's a driver problem. However, I am currently out of state for what will probably turn out to be a funeral trip, so I am unable to test anything (I'm currently on my iPod).

---

