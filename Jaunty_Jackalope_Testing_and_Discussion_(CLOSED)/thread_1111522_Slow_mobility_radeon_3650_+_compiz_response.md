---
title: "Slow mobility radeon 3650 + compiz response"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tr33m4n on 2009-03-30
Hello there,

Having used Jaunty since Alpha 5 I was very excited when fglrx was able to be installed in the beta release. Everything is as compiz-ie as it should be, however there's an odd problem when trying to resize windows, close windows, or open them from the taskbar. Basically there's a delay and it seems like nothing is happening... This may extend to other actions apart from the ones mentioned, but those are the ones i've noticed the most.

Anybody else having this problem?

My laptop is a Dell Studio 17, 2.0ghz, 3gbs ram, ati mobility radeon hd 3650... im sure the specs are more than enough for smooth compiz

Cheers
Dan

---

### Post by factotum218 on 2009-03-30
Sorry I don't have an answer for you but I have to ask, you have 3d acceleration working on that card? 

How are other 3d intensive things like, I dunno, a game or something similar?
I ask because I have the same card on my laptop. I just don't want to risk a complete reinstall to find out I get a black screen like I did with everything else up to this point.

---

### Post by uBeer on 2009-03-31
Hmmm, I have the exact same laptop... and the same problem!

Compiz runs ok, except when a window is resized or minimized/restored/maximized.
Don't know what's causing it though.

---

### Post by tr33m4n on 2009-03-31
hmmm, yeah its a little odd. In response to factotum218, yes 3d is working well, I installed World of Padman to test, and got a brilliant fps :) so I would say it would be safe upgrade... dont hold me to it though! lol

Cheers
Dan

---

### Post by uBeer on 2009-03-31
A question that's a bit off topic: does your laptop suspend/resume work? Cause mine won't wake up the display so at every resume I have to kill x with Alt-PrintScr-K to get the x server to restart.

---

### Post by tr33m4n on 2009-03-31
Erm yeah mine works fine... what make/model of comp you using?

Cheers
Dan

---

### Post by uBeer on 2009-03-31
I have:
Intel 2 Duo T5800@2GHz (not too fast),
Ati mobility radeon 3650 (of course...)
Broadcom Corporation BCM4322 802.11a/b/g/n Wireless (have to fight with it from time to time...)
No fingerprint reader, bluetooth or any of the extra stuff, except for a 1920x1200 resolution screen :D

I had suspend/resume working before (9 out of 10 times) with Intrepid. But that was with 32 bit. When I updated that to Jaunty it still worked and resume was even faster.

The reason that I did the update was because my Intrepid installation had become very slow, so I wanted to see if Jaunty would be a little bit faster. And it was, but not that much and there was the resize problem. That's why I did a complete reinstall to see if was some leftovers from Intrepid that caused the odd behaviour. But that happened to be the 64 bit version because I tried that one on my desktop and was quite impressed with it.

When I find the time I'll try installing the 32 bit version again to see if that resolves my suspend/resume problems (there are some more reasons for a reinstall because globalmenu-bar and eclipse64 don't work nice together and some other code assignments problems).

---

### Post by tr33m4n on 2009-03-31
global menu? are you trying to make youre install mac like? lol... not too sure why youre previous installation had become slow. I also have a broadcom adapter, no troubles here... although jealous of the 1920 (but not really, i find the glossy wled 1440 perfectly pretty). in terms of running 32bit, I'm running 64 with no issues in terms of suspend... maybe another topic for discussion. How's compiz running for you? do you experience the same problems previously mentioned?

Cheers
Dan

---

### Post by tr33m4n on 2009-03-31
I apologise, you mentioned before you had the same problems as we have... i've had a long day, lol, didn't take in youre other post!!

---

### Post by uBeer on 2009-04-01
Haha, no problemo :D

Ah, but now I get jealous of your setup, because I've gone and installed the 32 bit version and it still won't resume properly... And when after a resume I want to shut it down it shows a black screen instead of the Usplash and the fan starts blasting like something is going to blow.

Maybe if I get real desperate I could try and install Intrepid again and upgrade from there, see what has changed since then.

Did you do anything special to the default setup, or did it work out of the box?

But boy, this laptop is cool nonetheless!! And I love the space I have on the screen, that's why I came to like the global menu bar: it saves some more! And windows look so much better without the menu's. But I especially recommend to install it on machines with not to many pixels (and install the hide menu bar extension for Firefox).

---

### Post by tr33m4n on 2009-04-01
To be honest, I'm not entirely sure... I think it's just vanilla, but I may of installed something along the way... hmm, I know it's been this way for a while, but I miss the old xorg.conf... you sort of knew where you were with it. It makes me uneasy when everythings 'hidden', lol.

Anybody got any further with the compiz issues? I've tried disabling numerous plugins to see if that made any difference, with no avail :s grr

Dan

---

### Post by Parp on 2009-04-13
I'm having the same issue on a Dell Studio 540, it's got an ATI HD3450 in (not great, but I don't really use it for gaming).. It's really annoying me now. Also whenever I open a new app while listening to music there is a delay also, turn compiz off and no delay...

At least video is working properly in 9.04..

---

### Post by DanaG on 2009-04-13
I have the very same issue (HP 8530w, Mobility FireGL V5700 (RV635, same as HD3650).  Oddly enough, it only seemed to start having that lag issue after about two weeks ago.  The lag seems to be on creation or allocation of a surface for a window -- the lag is directly proportional to the area of the window, and even happens with metacity compositing.

---

### Post by zephyrgong on 2009-04-14
I have the same problem, and more worse, if I enable the compiz, there's a chance my laptop got frozen. I'm using Thinkpad T500 with HD 3650

---

