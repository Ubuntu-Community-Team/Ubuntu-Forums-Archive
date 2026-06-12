---
title: "UNR 9.10 Fresh Install on HP 110-1081tu netbook, No wireless"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by DanN on 2010-03-09
G'day,

I just got my self a netbook.  I bought the one with linux because I figured that if they sell it with linux, it's probably using h/w which supports linux.  

I played around with the Mi variant it had pre-installed, but it was a bit limited and slow, so I installed UNR instead.

The install went fine, and UNR is really nice to use and feels faster than the Mi too which is great.  However, wireless isn't working.  It's got a broadcom chipset (BCM4312) which I think needs a proprietary driver, but when I use the Hardware drivers tool, it doesn't have any options to install a driver.

I suspect there's a pretty simple process to get this working, but I haven't bought any new h/w to fiddle with for ages, so I'm not sure what it is, and I didn't find anything quickly on the forums, so if anybody could give me some advice it would be much appreciated.

Thanks

---

### Post by halj32 on 2010-03-09
You have to install the BCM drivers they are on the cd & you should be able to install them using the restricted drivers installer
CD
\pool\restricted\bcmwl

---

### Post by DanN on 2010-03-09
Thanks for the reply mate.  The broadcom drivers package was on the cd just like you said, and while it depended on DKMS, that was also on the cd.  So I installed both and ran the jockey.

Jockey now listed the broadcom driver so I tried to activate it.  It asked me for my password, then it briefly showed a screen saying something like, 'downloading and installing', but it was only up for a second, then it went back to jockey without activating.  I also tried it from the command line using jockey-text to see if it produced some error messages, but there was nothing.  

Does anybody have any idea why that might have happened? 

Thanks

---

