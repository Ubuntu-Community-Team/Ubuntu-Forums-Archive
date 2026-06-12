---
title: "my computer is old, what are my options?"
date: 2006-04-18
forum: Installation &amp; Upgrades
---

### Post by CharlesThe9th on 2006-04-18
I have a HP Vectra, Pentium III (733mhz), 128 megs of RAM, and three hard drives, two 10.1 Gig and an 82.0 Gig HD.  this thing hates to work with Windows and frustrates me enough to bang my head against the wall](*,) .  I tried loading ubuntu (server) and after I entered my username and password I couldn't get the GUI to start, unsure of what command to use.  I had previously and successfully entered Ubuntu regularly with no problems.  Should I just stay with the normal (non-server) version, eventhough I was trying to figue out which would be better for working on graphics.  Don't worry too much, I am trying to get a new laptop for school (NJIT).

---

### Post by Sef on 2006-04-18
> HP Vectra, Pentium III (733mhz), 128 megs of RAM

With those specs, I would recommend xubuntu.  It's a lightweight window manager.

In Breezy, do a server install first.

At the command line type these commands:

sudo apt-get update

sudo apt-get install xubuntu-desktop

Update: Thank you, KMandla

---

### Post by LMP900 on 2006-04-18
Try out Xubuntu, I had it running pretty good on my compaq with similar specs

---

### Post by teasum on 2006-04-18
There's also the Ubuntu Lite project, which I haven't tried myself.

[http://www.ubuntulite.org/dokuwiki/doku.php?id=repositories](http://www.ubuntulite.org/dokuwiki/doku.php?id=repositories)

It looks like it's worth a shot.  But I agree that Xubuntu is probably the best place to start with those specs.  I actually have an HP Vectra (500mHz 128m) that I'll be installing Ubuntu on soon, so I'll be interested to hear how Xubuntu (or whatever you choose) works for you.

---

### Post by aysiu on 2006-04-18
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by K.Mandla on 2006-04-18
Definitely give Xubuntu a whirl. I've tried straight Ubuntu on machines as slow as 475Mhz with 128Mb and Xubuntu performs much better. Ubuntulite is also a good option.

One note: I think Sef means this ...

```
sudo apt-get install xubuntu-desktop
```
after a server install. Of course, you'll need an Internet connection, although it can be done without one. Good luck! :mrgreen:

---

### Post by Ozitraveller on 2006-04-18
I'm running a PII/400 with 389 mb ram and 64mb video (nvidia), with the standard Ubuntu desktop. More ram would be nice but it works and it's stable.

---

### Post by ahh_dee on 2006-04-18
ive just did a server install with xbuntu but I wanted to change to use fluxbox instead. To me that is faster and all I need  So I did another server install but I am having startx problems.  does anyone know what i can do? Yeah its kinda off topic.

---

### Post by az on 2006-04-18
[QUOTE=CharlesThe9th]I have a HP Vectra, Pentium III (733mhz), 128 megs of RAM, and three hard drives, two 10.1 Gig and an 82.0 Gig HD.  this thing hates to work with Windows and frustrates me enough to bang my head against the wall](*,) .  I tried loading ubuntu (server) and after I entered my username and password I couldn't get the GUI to start, unsure of what command to use.  I had previously and successfully entered Ubuntu regularly with no problems.  Should I just stay with the normal (non-server) version, eventhough I was trying to figue out which would be better for working on graphics.  Don't worry too much, I am trying to get a new laptop for school (NJIT).[/QUOTE]
More ram would be better (even 64 megs more), but the default ubuntu desktop should run just fine on your box.

---

### Post by fgluck on 2006-04-18
Just installed Ubuntu on a 400 Mhz Compaq Presario 5300 series with 256Mb or so of memory. Runs OK however programs loads are slower than I would like and dragging windows around sometimes leaves "trails" that indicates to me that I may be at the upper limits of the hardware capability. 

All appears to work well. I am really just looking for an OS to drive a browser and streaming music. 

Having trouble getting Rhythmbox to play streams but other than that, seems to work OK.

Question -- can I install Xbuntu over the top of the full install or do I have to start over?

---

### Post by az on 2006-04-18
[QUOTE=fgluck] can I install Xbuntu over the top of the full install [/QUOTE]
Yup.

---

