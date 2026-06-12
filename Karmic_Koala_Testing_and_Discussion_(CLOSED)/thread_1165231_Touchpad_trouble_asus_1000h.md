---
title: "Touchpad trouble asus 1000h"
date: 2009-05-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nyarnon on 2009-05-20
My touchpad on my asus eeepc 1000h doesn't tap anymore, slides work fine. Anybody?

---

### Post by adult swim on 2009-05-20
i am having the same problem 
```
"SynPS/2 Synaptics TouchPad"	id=6	[XExtensionPointer]
```

---

### Post by MacUntu on 2009-05-20
Tapping is disabled by default (upstream decision):

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391)

Debian bug report (closed): [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497523](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497523)

and one blog post about it:

[http://who-t.blogspot.com/2009/04/synaptics-11-and-what-your-touchpad-can.html](http://who-t.blogspot.com/2009/04/synaptics-11-and-what-your-touchpad-can.html)

---

### Post by xens on 2009-05-20
same laptop, same problem :]

---

### Post by nyarnon on 2009-05-20
> **MacUntu said:**
> Tapping is disabled by default (upstream decision):




Is there some way to disable upstream, after the CTRL-ALT-BACKSPACE issue I start to think they entered silly mode.

---

### Post by adult swim on 2009-05-21
> **MacUntu said:**
> ...

and one blog post about it:

[http://who-t.blogspot.com/2009/04/synaptics-11-and-what-your-touchpad-can.html](http://who-t.blogspot.com/2009/04/synaptics-11-and-what-your-touchpad-can.html)

cool i dindnt know about the 2 finger scrolling

---

### Post by Nullack on 2009-05-21
> **nyarnon said:**
> Is there some way to disable upstream, after the CTRL-ALT-BACKSPACE issue I start to think they entered silly mode.

LOL, I like your humour mate

Seriously though without upstream, Ubuntu wouldnt exist. Ubuntu is but a small anchovy in a sea of much larger animals of the FOSS ecosystem.

---

### Post by freeman2000 on 2009-05-21
I'm also having the problem on an HP laptop.  I can scroll with the touchpad, but the tapping seems to be disabled.  This just happened with the last update.  I checked in System --> Preferences --> Mouse and the touchpad is enabled, so it is a bug in the latest update.  Aw shucks, give me back my touchpad!

---

### Post by nyarnon on 2009-05-21
> **Nullack said:**
> LOL, I like your humour mate

Seriously though without upstream, Ubuntu wouldnt exist. Ubuntu is but a small anchovy in a sea of much larger animals of the FOSS ecosystem.

And thats what it is humor. I recognise the value of upstream decissions. Even if I don't like 'em. There there for a reason.

---

### Post by nyarnon on 2009-05-21
> **freeman2000 said:**
> I'm also having the problem on an HP laptop.  I can scroll with the touchpad, but the tapping seems to be disabled.  This just happened with the last update.  I checked in System --> Preferences --> Mouse and the touchpad is enabled, so it is a bug in the latest update.  Aw shucks, give me back my touchpad!

Read the links you where given. Add the PPA of William Grant and update your system. My pad works fine again. 
Thanks again William ):P

---

### Post by afv on 2009-05-21
I too thought it was a bug. :roll:
Thanks.

(Asus F3JC here. Maybe change the thread title to something like "Touchpad tapping is now disabled by default"? :-s)

---

### Post by nyarnon on 2009-05-21
Hmmm and the trouble isn't open. Now I got taps working again, folders don't seem to open on a double tap or a button click for that matter, I need to use enter.

Sorry seems that the interval time was a bit to short set in the mouse settings, corrected it and all is fine.

---

### Post by techdude3177 on 2009-05-25
Woot for William! this worked for mine too!

---

### Post by freeman2000 on 2009-05-25
> **nyarnon said:**
> Read the links you where given. Add the PPA of William Grant and update your system. My pad works fine again. 
Thanks again William ):P


Seems that Karmic "xserver-xorg-input-synaptics" has yet to be updated.  I followed the links.  There's nothing in my xorg.conf concerning the touchpad - only the monitor & video card.  How do I find William's PPA?  Or can you, or anyone else, walk this rookie thru the steps to solve the "tapping" problem on my Karmic laptop?  Thanks in advance.

---

### Post by Stephmau on 2009-05-25
You can find the PPA here : [https://launchpad.net/~wgrant/+archive/ppa]("https://launchpad.net/~wgrant/+archive/ppa")

It works for me.

---

### Post by freeman2000 on 2009-05-25
Thanks, Stephmau.  I downloaded the Jaunty package and it works in Karmic.  I can "tap" once again!  Thanks.

---

### Post by Sarvatt on 2009-05-26
I've got an updated one for karmic in my PPA you can grab as well if you want to try something different.

[https://edge.launchpad.net/~sarvatt/+archive/ppa/+sourcepub/634362/+listing-archive-extra](https://edge.launchpad.net/~sarvatt/+archive/ppa/+sourcepub/634362/+listing-archive-extra)

BTW, be sure to get rid of gsynaptics and install gpointing-device-settings instead if you're using newer drivers, 2/3 finger scroll options are built into it and SHMConfig isn't needed anymore to change settings. with the latest 1.1.99 you can even turn off the annoying tap and drag thing via synclient that was permenantly enabled on synaptics before.

---

