---
title: "??? about xsplash..."
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-09-12
I have all the updates as of this morning.  When I boot, I get what looks like usplash all the way to the gdm login screen.  After I log in, I get what looks like xsplash with the vertical throbber.  Then I get a large gray rectangle in the upper left corner taking most of the screen which remains until launch an app that takes the whole screen.  Is this the new boot experience?

---

### Post by bacardiandwatermelon on 2009-09-12
Yeah same thing happened to me, someone must have stuffed an update :-P

---

### Post by godhika on 2009-09-12
This sounds like a good reason for a bug report (the grey rectangle)

---

### Post by mariner09 on 2009-09-13
I just don't know how to capture it.  Maybe a picture.  The wallpaper doesn't show gray after the desktop comes up, but there's a hint of shadow like a normal window would produce on the desktop.  Almost like compiz is honoring the gray area as a window.  I can even take a small gnome terminal and drag it around like an eraser and make the shadow remnant disappear.

---

### Post by muximus on 2009-09-13
u mean the rest of it is how it is supposed to be?.. the brown background with what looks like a ribbed condom zoomed to the max??

---

### Post by go7Ul1ai on 2009-09-13
Something like this? (this happens when I click on the date/time applet):

[http://yfrog.com/3zscreenshotfgp](http://yfrog.com/3zscreenshotfgp)

---

### Post by bacardiandwatermelon on 2009-09-13
I guess my issue is slightly different... Didn't read your thread properly :-P
After an update I went from this nice xsplash...
[IMG]http://1.bp.blogspot.com/_OYa7zTvmZ2k/SoRXM-Lrc-I/AAAAAAAAAYA/Fg1G7YXBJwg/s400/xsplash.png[/IMG]

To this crappy one with the vertical throbber...
[IMG]http://www.phpchina.com/attachments/2009/08/1_200908311448221mH88.jpg[/IMG]

I tried purging the xsplash package and installing from source versions 0.7.1 and 0.7.0 but nothing changes... :-(

---

### Post by Darkshade on 2009-09-13
> **lee.jarratt said:**
> Something like this? (this happens when I click on the date/time applet):

[http://yfrog.com/3zscreenshotfgp](http://yfrog.com/3zscreenshotfgp)

Even worse :)

---

### Post by vredley on 2009-09-13
> **lee.jarratt said:**
> Something like this? (this happens when I click on the date/time applet):

[http://yfrog.com/3zscreenshotfgp](http://yfrog.com/3zscreenshotfgp)

I've been seeing that ever since I installed Karmic (Alpha 4). Thought it was an Intel graphics issue, but it only seems to happen with Compiz.

---

### Post by Darkshade on 2009-09-13
> **vredley said:**
> I've been seeing that ever since I installed Karmic (Alpha 4). Thought it was an Intel graphics issue, but it only seems to happen with Compiz.

I don't think it's Intel related, I have a PC with Nvidia card and another one with ATI, both suffer from this.

---

### Post by maheshasolkar on 2009-09-13
> **bacardiandwatermelon said:**
> I guess my issue is slightly different... Didn't read your thread properly :-P
After an update I went from this nice xsplash...

(see image in original comment)

To this crappy one with the vertical throbber...

(see image in original comment)

I tried purging the xsplash package and installing from source versions 0.7.1 and 0.7.0 but nothing changes... :-(

I've always had the one you refer to as 'crappy one with the vertical throbber'. I though that's how it is supposed to be. I don't quite like the vertical throbber. I'll be happy if that is not how it is supposed to be!

My test computer has Intel graphics.

---

### Post by vredley on 2009-09-13
> **Darkshade said:**
> I don't think it's Intel related, I have a PC with Nvidia card and another one with ATI, both suffer from this.


Since Jaunty, I've been blaming Intel graphics for just about everything. :p


> **maheshasolkar said:**
> I've always had the one you refer to as 'crappy one with the vertical throbber'. I though that's how it is supposed to be. I don't quite like the vertical throbber. I'll be happy if that is not how it is supposed to be!


I think the 'crappy vertical throbber' is just a (broken) placeholder; it should be fixed soon.

---

### Post by novafluxx on 2009-09-13
> **vredley said:**
> I think the 'crappy vertical throbber' is just a (broken) placeholder; it should be fixed soon.

I sure hope so, the one he has pictured there is very nice looking.

I've looked through the installed themes and stuff, and I see none of the neat new themes that I've heard about...

Where do I get them, how do I change the default throbber? Default artwork/theme just don't do it for me at all.:confused:

---

### Post by bacardiandwatermelon on 2009-09-14
This is the ppa I was using in sources.list file... Maybe you will have better luck with it :-)

```
deb http://ppa.launchpad.net/xsplash-team/ppa/ubuntu karmic main
```

---

### Post by jocko on 2009-09-14
> **bacardiandwatermelon said:**
> This is the ppa I was using in sources.list file... Maybe you will have better luck with it :-)

```
deb http://ppa.launchpad.net/xsplash-team/ppa/ubuntu karmic main
```
The package in that ppa is outdated. But you can still install it in synaptic (look in package-->lock version)

---

### Post by bacardiandwatermelon on 2009-09-14
sweet as didn't realise :-), I've locked in 0.7+r58+-new-assets-r63+200909020056 and am enjoying the goodness, i'll have to keep an eye out for a new update :-)

---

### Post by mariner09 on 2009-09-14
Lee,

That's exactly what I see.  Time to apply some updates and see what happens...

---

