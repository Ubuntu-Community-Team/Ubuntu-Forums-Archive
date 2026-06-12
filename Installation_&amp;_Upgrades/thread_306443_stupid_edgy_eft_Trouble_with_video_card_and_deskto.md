---
title: "stupid edgy eft: Trouble with video card and desktop performance"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by nickstatus on 2006-11-25
I am sick and tired of all the stupid bugs that edgy eft has to offer. what the hell is an "eft" anyway? so yeah, I am switching back to good ol' reliable dapper drake. any advice on the keeping of my current setup, just switching back the distro and nothing else? I'd rather not have to track down a thousand guides to get everything working again, but I suppose its worth it to get rid of this stupid eft nonsense.

---

### Post by _lynX on 2006-11-25
You could ask for help on your problems so we could help you fix your Edgy Eft installation, but if that is not an option, we'll need to know what types of hardware you have that would require setting up.

---

### Post by K.Mandla on 2006-11-25
> **nickstatus said:**
> what the hell is an "eft" anyway?
[http://en.wikipedia.org/wiki/Eft](http://en.wikipedia.org/wiki/Eft)

Try to relax, brother. Breathe deeply. We're all here to help. Tell us about your problems, or point us to the threads so we can contribute.

---

### Post by nickstatus on 2006-11-25
I'm glad I finally know what an "eft" is. Okay, this is running on a toshiba satellite a100 s2211td. Celeron 1.7 ghz i believe. ati mobility, but whether its a radeon or an express is up in the air. a little over a gig of ram. My main trouble right now is this thing that happens non-consistantly, where when gnome starts up, suddenly all the icons and toolbars disappear, leaving the desktop blank. or sometimes, only the toolbars and the top part of the window with the close and minimize/maximize buttons disappear. also it runs way slower, it hates my video card, and no amount of uninstalling and reinstalling anything that has to do with totem, xine, gstreamer, codec libraries and such will fix the fact that now my computer wont play media files. I guess I was foolish in assuming that the release of the new ubuntu would result in bricks of gold falling from the skies, and everyone ... scented milk, but this is rediculous.

---

### Post by K.Mandla on 2006-11-25
Well, let's see. I think if you use the *lspci* command, you should be able to tell if you're using a Mobility or an Express. If you don't get all the information you need, try *lspci -v*, *lspci -vv*, or *lspci -vvv* for extremely detailed information. (Don't forget the *lshw* command is sometimes helpful too.)

It does sound like there's some sort of driver issue going on. If you have that problem plus the media codec issue, you might want to look into Automatix, which (used to, anyway) installs drivers for your computer and media codecs along with any number of other goodies. But perhaps you've tried those things already.

It is worth mentioning that if Dapper works well for you, there's no shame in using that over Edgy. I keep Edgy on one machine and run Dapper on my don't-ever-want-to-break machine, because Edgy acted funny on that box.

P.S.: I edited your title a little in hopes of attracting more help. ;)

---

### Post by yelloguy on 2006-11-25
I am with you on this.  But I have a laptop running Edgy just fine.  I had to do a clean install after upgrading to Edgy from Dapper broke it bigtime.  However, now it runs just fine.  So, did you upgrade from Dapper or is it a clean install?

I am trying to install Edgy from the same CD to a desktop (whose Dapper install broke due to a hardware upgrade) and the live CD doesn't recognize my keyboard and mouse.  I searched and then posted on this forum but got no replies.  I have tried the CD on another desktop and never got it to boot.  All that and the problems I see on this forum lead me to believe that Edgy is not quite stable.  If you can download Dapper and it works for you then stick with it.  (Me, I will live life on the cutting "Edge")

---

### Post by nickstatus on 2006-11-25
> **yelloguy said:**
> (Me, I will live life on the cutting "Edge")

lol! thanks for all the help, I have tried most of that stuff, but I never had any problems with the drake, so ima goin back. If I run into any more issues, y'all probably be hearin' from me. thanks again

---

### Post by flameproof on 2006-11-30
> You could ask for help on your problems so we could help you fix your Edgy Eft installation, 

The performance is a known and up to now not fixable bug in some systems, incl. mine.

Check in terminal:  cat /proc/cpuinfo

What's your CPU MHz? Mine got stuck at 1000.000 - some others have only 600.000

I hope that is fixed soon.

---

