---
title: "Debian Multimedia Repo working in lucid!"
date: 2010-02-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by moviemaniac on 2010-02-02
Hi guys,

I was disappointed to read in launchpad that lucid will ship with a _very_ old ffmpeg-version (essentially the same that shipped with karmic which will be nearly a year old when lucid is "finished"). There have been some recent developments which are really great for me - such as TrueHD support, Blu-Ray subtitle-support, LPCM-support and much more. All of this (which is already supported by VLC) will be missed in Karmic.
I didn't want to compile my own version of ffmpeg due to many packages depending on it so I looked for an alternate way. This was when I found the Debian Multimedia repository ([http://www.debian-multimedia.org/dists/testing/](http://www.debian-multimedia.org/dists/testing/)) where new versions of multimedia-related software such as ffmpeg, mplayer... are being offered. Since Lucid is mainly based on Debian testing I chose this repo. Everything I installed (I tried k9copy, mplayer and ffmpeg) worked fine. I then compiled a new version of VLC (I alway compile a new version from git every week or so to keep track with the latest developments) and all the new features I so wanted were there.

Long story short: Check it out if you want more than lucid offers you ;)

**However I should add as a disclaimer that adding said repo is not for the inexperienced user (which shouldn't use the Alpha anyway)! Use it as a temporary source and don't leave it enabled all the time - and be sure to know which packages you install from there so you can easily revert back to Ubuntu's packages should need be!**

---

### Post by andrew.46 on 2010-02-02
Hi moviemaniac,

I have not used this repository but I have certainly seen a reference to it [on the vlc forums]("http://forum.videolan.org/viewtopic.php?f=13&t=70719&sid=e58607f316b6743d648df24fc14d962e") which would bear close reading.

All the best,

Andrew

---

### Post by moviemaniac on 2010-02-02
Thanks for the link, I didn't know about that...

However this only seems to affect the VLC version shipped with Ubuntu. I compile my own versions of VLC and have tried all different types of video and audio files today and everything I tried worked - including the new features introduces with newer ffmpeg releases.

I'll leave everything s it is for now but I guess I'll have to find a way to get recent, unstripped "non-broken" ffmpeg packages in the long(er) run.

---

### Post by jfernyhough on 2010-02-02
This has got to be a bad idea... but what the heck.

/enables random Debian repo.

:D

---

### Post by mc4man on 2010-02-02
> This has got to be a bad idea... but what the heck.

Virtually guaranteed to be a problem, while using the testing will work for a bit longer than if you used sid, both will at some point disappoint you...

---

### Post by jfernyhough on 2010-02-02
Actually I'm a little disappointed by the difference, though this may be down to the PPAs I'm using. Not many updates for me... only interesting thing is XBMC but there's a PPA for that too...

---

### Post by moviemaniac on 2010-02-03
> **mc4man said:**
> .

Virtually guaranteed to be a problem, while using the testing will work for a bit longer than if you used sid, both will at some point disappoint you...
I guess it depends on what you want the repo to do for you. ffmpeg is a pretty closed thing with not too many packages depending on it. I'm sure packages depending on Ubuntu's version of ffmpeg will break at some point (actually they do just now) but if I don't use Ubuntu's packages but build my own (because I want to stay bleeding edge as far as multimedia support is concerned) depending on the versions from this Multimedia repo it should be just fine.

**However I should add as a disclaimer that adding said repo is not for the inexperienced user (which shouldn't use the Alpha anyway)! Use it as a temporary source and don't leave it enabled all the time - and be sure to know which packages you install from there so you can easily revert back to Ubuntu's packages should need be!**

---

