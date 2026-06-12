---
title: "Should I reinstall or try a different distro?"
date: 2015-02-15
forum: Installation &amp; Upgrades
---

### Post by kellyvotrenom on 2015-02-15
I have installed Lubuntu on an older computer, it has a Pentium 2.4Ghz processor and 1.5GB of memory.  I use it just for music, mostly streaming with Firefox as the browser.

I am having various problems but speed is my main concern.  Browsing can be really sluggish, I can't do anything with any sort of efficiency, I am always waiting for pages to load. PCManFM is slow as well, it can take as long as 10-15 secs to load a second internal drive with my music file.

At work I have computers with about the same computing power and memory - running Linux Lite on one, Peppermint on the other - and don't have these problems.  They aren't super speedy but they are very useable.

I was thinking of reinstalling Lubuntu but maybe I should try a different distro?  When I first installed Lubuntu is seemed OK but as time goes by I think it's getting slower.  Some of this could be my 'noob-ness' since it was of my first real Linux installs and I'm sure I tried and experimented with some software and such.  Maybe as Linux upgrades the kernel it could be more than my aging processor can handle?

What do you think?  I'm not sure what I want to do, I really like the LXDE a lot, more than the DEs at work.  My main computer has Ubuntu installed with the Cinnamon desktop, which I love.

Thanks for any and all input,

Mark Springer
industrial arts

---

### Post by sudodus on 2015-02-16
If browsing is really slow, it can be because the linux version of flashplayer is not really good. You might also have problems with the driver for the graphics card/chip. 

- Please specify your graphics hardware!

I don't understand what you mean by  'PCManFM is slow as well, it can take as long as 10-15 secs to load a second internal drive with my music file'. Do you mean downloading from the internet or loading a file from a second internal drive into your music player? What music player are you using?

I think it is worthwhile tweaking your Lubuntu.

- Which version are you running (14.04.1 LTS)?

You might also try a community re-spin of Ubuntu 12.04 LTS or Ubuntu 14.04 LTS with a light desktop environment.

If still no progress, then it is time to try an ultra-light linux distro, for example Wary Puppy, TahrPup or Tiny Core.

But the old hardware might not cope with modern browsing habits or modern websites. See the following link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by kerry_s on 2015-02-16
maybe try xubuntu ? 
xfce gets more love from developers then lxde does, so you could get a better expereince.

---

### Post by kellyvotrenom on 2015-02-16
* it can be because the linux version of flashplayer is not really good. *
This is something I just started to try and divine.  Is it possible to use a different flashplayer in Firefox?

*- Please specify your graphics hardware!*
I thought of that today.  I need to find out if I can update my graphics drivers, it really didn't occur to me before this.  
Here is the card info:
 VGA compatible controller        : NVIDIA Corporation NV44A [GeForce 6200] (rev a1) (prog-if 00 [VGA controller]) w/256MB of memory

*I don't understand what you mean by  'PCManFM is slow as well, it can take as long as 10-15 secs to load a second internal drive with my music file'. Do you mean downloading from the internet or loading a file from a second internal drive into your music player? What music player are you using?*
Sorry to be vague.  What I mean is if I click on the music drive in PCMan, it takes 10-15 secs for the folder to open.  I downloaded Nautilus to see if there was difference and yes there was - quite a dramatic difference.  So something is amiss with PCMan.

*I think it is worthwhile tweaking your Lubuntu. - Which version are you running (14.04.1 LTS)?*
Tweaking in what way? and yes it is 14.04.1

*You might also try a community re-spin of Ubuntu 12.04 LTS or Ubuntu 14.04 LTS with a light desktop environment.*
I don't understand the term 'community re-spin', however I thought LXDE was light weight (??)

I will follow the link you posted below.  Sorry for all the additional questions but really appreciate the help and your taking time to answer.

I did start re-investigating lightweight distros again this morning, one of the more interesting ones is Trisquel Mini but am open to trying an even smaller distro,  LXLE also looks good.  

Thanks much,

Mark Springer
industrial arts

---

### Post by sudodus on 2015-02-17
> **kellyvotrenom said:**
> * it can be because the linux version of flashplayer is not really good. *
This is something I just started to try and divine.  Is it possible to use a different flashplayer in Firefox?

No, but in Chrome (and maybe in Chromium-Browser).

You can also use HTML5 at least for some YouTube videos.
> 
*- Please specify your graphics hardware!*
I thought of that today.  I need to find out if I can update my graphics drivers, it really didn't occur to me before this.  
Here is the card info:
 VGA compatible controller        : NVIDIA Corporation NV44A [GeForce 6200] (rev a1) (prog-if 00 [VGA controller]) w/256MB of memory

Old nvidia cards might work better with old nvidia proprietary drivers, that you find with older kernels (for example in re-spins based on Ubuntu 12.04 LTS).
> 
*I don't understand what you mean by  'PCManFM is slow as well, it can take as long as 10-15 secs to load a second internal drive with my music file'. Do you mean downloading from the internet or loading a file from a second internal drive into your music player? What music player are you using?*
Sorry to be vague.  What I mean is if I click on the music drive in PCMan, it takes 10-15 secs for the folder to open.  I downloaded Nautilus to see if there was difference and yes there was - quite a dramatic difference.  So something is amiss with PCMan.

This is one successful tweak for you (pcmanfm --> nautilus) :-)
> 
*I think it is worthwhile tweaking your Lubuntu. - Which version are you running (14.04.1 LTS)?*
Tweaking in what way? and yes it is 14.04.1

Trying different versions of nvidia proprietary drivers. Trying different web browsers and plug-ins to avoid ads, javascript, cookies and other things that are annoying, eat computing capacity and increase the risk of intrusion.

@everybody: Please suggest what to tweak :-)
> 
*You might also try a community re-spin of Ubuntu 12.04 LTS or Ubuntu 14.04 LTS with a light desktop environment.*
I don't understand the term 'community re-spin', however I thought LXDE was light weight (??)

A linux distro based on the same program packages (from the same repositories) as Ubuntu, but built and maintained by some other person or group of people (not Canonical). Bodhi and LXLE are examples with versions based on Ubuntu 12.04 LTS. LXLE uses the desktop LXDE and 'gives Lubuntu extra life' after the official Lubuntu end of life.
> 
I will follow the link you posted below.  Sorry for all the additional questions but really appreciate the help and your taking time to answer.

I did start re-investigating lightweight distros again this morning, one of the more interesting ones is Trisquel Mini but am open to trying an even smaller distro,  LXLE also looks good.  

Thanks much,

Mark Springer
industrial arts

---

### Post by MAFoElffen on 2015-02-17
IMHO-- 

Lots of experience breathing new life into old iron. I have 2 standbys for a minimal systems.  Foremost is Lubuntu. Even lighter is Linux Lite, which is another Ubuntu spin-off (and uses our repo's) that we've had pretty good luck with. When I say we, I mean for a computer recylcer I help out with.

On minimal, if you're having problems with Lubuntu, then Xubuntu would be a step in the wrong direction. I love Xubuntu, Ubuntu and Ubuntu Gnome, but... with a lite system where resources are limited, you really have to play with what you have to see what works best for you. (What is acceptable.)

Firefox is heavy for a browser. For lite versions... For lite alternate browsers I use Chromium (The stripped down opensource version). There's also Epiphany, Konqueror, Swift Weasel, SwiftFox and Midori.

Your video is fine with ubuntu packaged nvidia drivers. It is old enough that is is still covered by the Geoforce driver set, but not new enough to be considered as a fast GPU. That model will not be any faster with with nvidia's binaries. A faster card would make rendering faster (keep in mind that NVidia GT250's go for under $50 now...)

You didn't say anyhting about your memory type or bus speed. They refer to some 4-core mobile chips today as "Pentiums"... so just calling it a Pentium may be misleading.

---

### Post by kellyvotrenom on 2015-02-18
Thanks to everyone for all your suggestions.  It seems that most prudent thing to do would be to reinstall; I'll get to try a couple different distos in the process, which is always fun.  I may try Chrome again, but I recall it not being able to stream some of the sites I listen to.

One thing - I noticed that many of the LW distros use 12.04 LTS and I suspect that some of my problems showed up after I upgraded to 14.04.  So I am going to stick with 12.04 for this machine and see if it helps.

Thanks again,

Mark Springer
industrial arts

---

### Post by sudodus on 2015-02-18
Good luck, and please come back and shared your results :-)

---

### Post by kerry_s on 2015-02-18
12.04lts is still supported for another 2 years so you'll still be good.
have a look at elementary luna it's based on ubuntu 12lts, i found it to be very fast & lite. it also only has the minimum apps, so really easy to add the apps you want & keep bloat to a minimum.

have fun distro hopping, hope you find what your looking for. it took me a week of bouncing around, i finally settled on xfce desktop, i find it to be the most customizable to get it how ever i want, other de's/wm's i always had to force them, or had no choice at all.

---

### Post by mörgæs on 2015-02-19
Ubuntu 12.04 is still supported but not Lubuntu. 

The graphics card is not that old. In stead of going backwards I suggest a fresh install (no upgrades) of Lubuntu 14.10.

---

