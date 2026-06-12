---
title: "Do embedded Flash videos (i.e. YouTube)  flicker for you too?"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-10-17
Since a few updates ago I've noticed this annoying behavior where embedded YouTube videos flicker a lot. This does not happen when watching the video from the YouTube page itself, only when the video is embedded onto another website. I've replicated this in Chromium and Firefox. Anyone else has seen this?

---

### Post by froggyswamp on 2009-10-17
No, but if you do a clean install from a daily Ubuntu build and still have this issue then I'd suggest reporting it (the clean install imo just makes sure it's not your fault nor some update issue).

---

### Post by andresmh on 2009-10-17
I've configured my system already, it took a few hours of work, I am not sure this annoyance would justify reinstalling :-/

---

### Post by froggyswamp on 2009-10-17
Just installing a new copy onto another partition (if you have one) (and see if the issue is there before you "configure" your system). Or take the "wait and see if anything changes" approach.

---

### Post by Insane_Homer on 2009-10-17
youtube was flickering for a few days with a few of the updates mid week, all seems ok now since update from 2 days ago I think.

may have something to do with the daily updates to the gfx drivers. may be a nvidia thing. don't recall having the problem on my laptop with ATI card, but then I've not really used it much this week.

---

### Post by inportb on 2009-10-17
It's a problem with either Flash or the video driver, and I suspect the video driver because Flash (the 64-bit build from Adobe Labs) seems to be just fine on my setup.

---

### Post by psyke83 on 2009-10-17
It happens to me as well on Intel 855GM graphics, so it's unlikely to be a specific video driver problem. The problem happens only with embedded videos. It's probably an issue with Flash or Firefox (not nspluginwrapper, as I'm using the 32 bit release).

Re-installing really seems overkill, IMHO. As long as you're using the stock Firefox packages and flashplugin-installer, that's enough.

---

### Post by jon.reeve on 2009-10-17
That happens to me, too, with an Intel 945M graphics card and a fresh install of Karmic. It also happened to me in Jaunty, too. I think it's a problem with Flash (we're all using the official Adobe version, right?) and not Firefox or graphics cards, because we all have different graphics cards and I get this problem using four or five different browsers.

---

### Post by andresmh on 2009-10-17
I also have an Intel video card. I think it is very likely that it's caused by recent isues with Mesa and Intel

---

### Post by HotShotDJ on 2009-10-17
> **andresmh said:**
> This does not happen when watching the video from the YouTube page itself, only when the video is embedded onto another website.This is something that I've noticed, on and off, even in Jaunty.  When I see it, I click-through to the actual YouTube page and the flickering goes away.  This was on a laptop with Intel 945GM graphics card and Jaunty 32 bit.  I just bought a brand new System76 Pangolin (PanP5) and installed Karmic on it and I haven't had that issue (Nvidia G105M, Karmic 64 bit w/ 64 bit Flash plugin).  I strongly suspect it is an issue with the Intel video drivers as noted by andresmh

---

### Post by nfl on 2009-10-24
This affects me, too. Karmic Koala, AMD64, 64-bit Flash plugin, GeForce 6600, binary nvidia driver. But it happened many months ago, too.

I think it's a YouTube specific problem. In other contexts, there is no difference between embedded and not embedded flash objects (after all, every flash object is embedded). Moreover, flickering doesn't simply mean a disappearing video, but the Embed/URL panel appears for a moment.

---

### Post by andresmh on 2009-10-24
> **nfl said:**
> 
I think it's a YouTube specific problem. In other contexts, there is no difference between embedded and not embedded flash objects (after all, every flash object is embedded). Moreover, flickering doesn't simply mean a disappearing video, but the Embed/URL panel appears for a moment.


yes, exactly, the embed/url screen appear for a moment. As others mentioned, it seems to be a Xorg problem.

---

### Post by blazk on 2009-10-25
it happens to me too in Midori on eeepc 701. Additionally 3d apps are very slow; glxgears reports around 400 fps, etracer~3fps. Graphics seems much faster in ubuntu 9.04.

UPDATE: added myself to the 'video' group and 3d acceleration now works. I still see the flash problem  for embedded videos on facebook; there is no flickering when played on youtube.

---

