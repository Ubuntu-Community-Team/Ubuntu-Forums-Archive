---
title: "Before I install..."
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by bug67 on 2010-03-03
I want to duel boot my HP Pavilian dv8 laptop.  It is currently running Windows 7 Professional.  I have downloaded and burnt a copy of the 64-bit version of Ubuntu and am able to boot to the LiveCD.

_**Problem # 1**_:

My wireless network is undetected.  If I plug directly into a hard line, I *can* connect to the Internet no problem just, no wireless.

If I launch device manager from Windows, it says I have an 

**[COLOR="Navy"]Intel® Centrino® Advanced-N 6200 AGN[/COLOR]** Wireless card.

What do I need to do to get this wireless card working?

I will save question # 2 (sound issues) for after I get question # 1 sorted.

Thanks in advance.

---

### Post by bug67 on 2010-03-04
Anybody?

:popcorn:

---

### Post by Ms_Angel_D on 2010-03-04
While plugged into the regular net connection try checking for restricted drivers. Go to System -> Administration -> Hardware Drivers. It may be that you need proprietary wireless drivers installed, to get your connection working.

If that doesn't work I'm not sure & hopefully somebody with a bit more knowledge can help you get it going.

Angel

---

### Post by bug67 on 2010-03-04
I'm curious.  Can I install restricted drivers while running from the LiveCD?  Where do those "drivers" get stored while I'm running from the LiveCD?  Maybe I should have posted in ABT?  :P

---

### Post by Ms_Angel_D on 2010-03-04
You know I'm not sure. I wasn't aware you were running a live cd. Though this may be why you don't have wireless. Some cards just require restricted drivers and without them you won't be able to have wireless working.

---

### Post by bug67 on 2010-03-04
Yes.  I'm posting this from the LiveCD right now.  

As soon as I booted I was informed there were drivers available for my *graphics card*.  I downloaded and installed them...I guess?  Said they were installed anyhow.

However, I didn't see anything about my wireless being available.

I don't want to do a full install unless I know, *without a doubt*, I can get this stuff working.

---

### Post by Ms_Angel_D on 2010-03-04
Well I wish I could be of more assistance, hopefully somebody else will be able to provide more help. Sorry :(

Angel

---

### Post by bug67 on 2010-03-04
Just wondering if maybe I should post this in the "Networking - Wireless" forum?  Or, maybe ask a Moderator to move it for me?

---

### Post by adam22 on 2010-03-04
Easiest thing to do would be to use Wubi and try wireless in there since it is so easy to remove and quicker.

However, with a newer machine like that, I highly doubt you'll experience any issues with a hard drive install. When you go to set up the wireless, does it see any networks at all, or can you just not connect to it?

---

### Post by maddg3241 on 2010-03-04
ya it should install if you wire it all by itself

---

### Post by bug67 on 2010-03-04
> **adam22 said:**
> "...When you go to set up the wireless, does it see any networks at all, or can you just not connect to it?"

It sees zero wireless networks.

I kinda want to make sure this all works before I do an install on my hard drive because if it doesn't work, it's kinda a pain to get things back to normal.  I'd have to reset my MBR and all that.  I want to make sure things are good before I have to go through all that.

Also, I've heard that Wubi is broken so, I don't want to do that.  I don't want a Wubi install anyhow.  I want a *real* duel boot.

So, again I ask if maybe I should post up in "Networking-Wireless?"

---

### Post by adam22 on 2010-03-04
If wireless works in Wubi, it will work on the hard drive. If it does not, then your questions are answered. 

You can remove it and install to the hdd if it works.

---

### Post by bug67 on 2010-03-05
What part of "Wubi is broken" did you miss?  :P

Anyhow I went ahead and did a full install and, of course, no wireless.  :rolleyes:

However, I think I may have been put onto the right track here:

[http://www.linuxmint.com/wiki/index.php/MintWifi](http://www.linuxmint.com/wiki/index.php/MintWifi)

Although the above is for Mint, everything should be the same for any *buntu.

Silly me, I found that wiki after I wiped my Linux partition and reset my Windows MBR.  I think I'll just wait a couple months for Lucid.

---

