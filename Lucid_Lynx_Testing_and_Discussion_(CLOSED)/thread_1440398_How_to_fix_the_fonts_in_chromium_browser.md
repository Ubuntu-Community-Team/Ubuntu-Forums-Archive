---
title: "How to fix the fonts in chromium browser"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jaco223 on 2010-03-27
Is there a way to fix the fonts in chromium browser. Maybe my eyes are bad, but I'm seeing blue and red hinting. Is this normal? or should the fonts look solid and black?

---

### Post by jaco223 on 2010-03-27
better screenshot

---

### Post by Enigmapond on 2010-03-27
Hi!

Maybe it's me but I don't see this. Have you slept lately?...{kidding} They look perfectly normal on your screenshot...to me at least.

Cheers!

---

### Post by bluelamp999 on 2010-03-27
See my post here - [http://ubuntuforums.org/showthread.php?p=8704572#post8704572](http://ubuntuforums.org/showthread.php?p=8704572#post8704572)

I had the same issue with Firefox and this fixed it. 

I've also tried it with Lucid and it works (for Firefox!)

---

### Post by jaco223 on 2010-03-27
bluelamp999 it certainly made a huge improvement to firefox , but it didn't seem to correct the problem in chromium. I even tried to match as best I could the font scheme from ff to that of chromium. I'll keep tinkering with it.

Edit: Is the fixed width font the one we see on webpages?

---

### Post by bluelamp999 on 2010-03-28
I just checked Chrome on my installed system (9.10) and my VirtualBox VM (10.04) and the annoying hinting is still there, so obviously the fix is only good for FF...

On a different note, when I made my initial posting about the issue in FF 3.6 (with before and after screen-shots) I had some people saying they couldn't see any difference (when it was totally obvious to me.)

This would lead one to believe that it could be hardware related. What kind of display hardware do you have? 

Mine is an ATI Mobility Radeon X300 graphics card on a Dell Latitude D810 laptop (1920 x 1200) with an external Dell 1906FP TFT monitor (1280 x 1024)

Is yours anything similar?

---

### Post by jaco223 on 2010-03-28
bluelamp I believe mine is the ATI Radeon HD 2400 series, I'm usin an iMac 24" 8,1 model from early 2008. I just reinstalled Lucid becuse I screwed my sound trying to install the oss sound driver, but anyway I just updated my font config file,, I'm using ff, but now I still see blue and red hinting. I'm looking for the cairo lcd update, but I can't find it. I'm using the nouveau driver where as before I was installing the opensource ATI video driver.

Edit. I haven't tried chromium yet, but yesterday the font config fix did not work for chromium.
I believe I have a LCD panel display 1600x1200 .

---

### Post by bluelamp999 on 2010-03-28
Jaco, I wish I could help you further but I've never owned a Mac in my life (except for an iPod!)

Maybe a post in the 'Apple Users' forum might be useful?

Good luck with finding a solution...

---

### Post by jaco223 on 2010-03-28
> **bluelamp999 said:**
> Jaco, I wish I could help you further but I've never owned a Mac in my life (except for an iPod!)

Maybe a post in the 'Apple Users' forum might be useful?

Good luck with finding a solution...

bluelamp999, thanks for your help. I will post in apple support. For now I will just use ff, I know there was a bug report filed on launchpad regarding the font rendering in chromium, that was from 2009. I don't understand why the issue hasn't been resolved as of yet. I was enjoying using chrome, but until the issue is resolved I'll just revert to using ff.

---

