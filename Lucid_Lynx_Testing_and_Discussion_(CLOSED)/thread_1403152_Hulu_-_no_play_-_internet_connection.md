---
title: "Hulu - no play - internet connection"
date: 2010-02-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by techdude3177 on 2010-02-09
Anybody else having issues playing videos on hulu?
It gives me an error saying "Sorry, we are unable to stream this video. Please check your Internet connection and try again." I know its not my internet connection cause I am posting this right now. I am also able to stream youtube and I am able to stream videos off hulu off my 9.04 install.

Any ideas?

---

### Post by techdude3177 on 2010-02-21
seriously? no body else?

---

### Post by Chronon on 2010-02-21
also getting this in Kubuntu 9.10 with firefox 3.5.8.

---

### Post by techdude3177 on 2010-02-21
you running 64bit?

---

### Post by ronacc on 2010-02-21
getting the same thing on both my lucid and hardy installs (64bit) . it started a couple of weeks ago for me , before that hulu would play fine.

---

### Post by HalfEmptyHero on 2010-02-21
Yeah, same things been happening to me. Just download hulu desktop from the Labs at hulu.com, it works.

---

### Post by Chronon on 2010-02-22
I am using Kubuntu 9.10 on x86_64 with firefox 3.5.8 on my desktop, where I do see this problem.  Hulu Desktop does work fine on this machine.

My netbook is Ubuntu 9.10 on x86 with Firefox 3.5 and it does not exhibit this problem -- Hulu plays fine within firefox.

---

### Post by techdude3177 on 2010-02-22
so it appears to be a flash 64bit problem

---

### Post by ronacc on 2010-02-22
I d/l'd huludesktop (64bit) and installed it with gdebi , it tells me it can't find libflashplayer.so , I modified the ~/.huludesktop file to point to a valid and working install of libflashplayer.so (64bit) but it still tells me it can't find it .

---

### Post by Seventh Reign on 2010-02-22
Hulu Desktop works for the first few minutes and then it begins to stutter until it is unwatchable.

---

### Post by jtgeibel on 2010-02-23
I've been seeing this same behavior since late in December.  I installed chromium and it was also broken.  I'm convinced its a problem with 64-bit flash.

I've also experience a lot of flash crashes lately and problems with fullscreen popping up behind the browser window.  It got a little better for a few weeks, but now "Please check your Internet connection and try again" is all I get.

I think I manually installed a flash "upgrade" a few months ago which is why I started seeing instability then.  I notice the latest download here ([http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)) was released on Feb 11th.  It seems this 10.0.45.2 version is now in the karmic repositories.  I haven't decided if I should try hulu desktop or downgrade flash.

---

### Post by jtgeibel on 2010-02-23
I just tried on another machine with 10.0.32.18 and couldn't get it to work there either.  So it doesn't look like downgrading flash will help me.  Maybe hulu started rolling out some changes to their site that trigger an existing bug in the 64-bit linux flash player.

---

### Post by kansasnoob on 2010-02-23
Hulu's always been flaky for me.

I think we need a Hulu/Totem link!!!!!!!!!!!!!!!

Sorry, just dreaming.

---

### Post by bigbad486 on 2010-02-25
Same problem here.  Running firefox on ubuntu 9.10 karmic with a 64 bit.  I ran some script I found that fixed my 32/64bit flash version confusion problems and removed swf and gnash.  That fixed some issues with youtube and other flash, but Hulu is now giving me the "unable to stream" error instead of the old flash player version error.

---

### Post by Sef on 2010-02-25
>  Hulu is now giving me the "unable to stream" error instead of the old  flash player version error. 

I am getting the same error on Lucid Lynx with Firefox 3.6.

---

