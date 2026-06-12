---
title: "Lucid beta: negative visual impact"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kom-Si on 2010-03-21
I finally got tempted to try Lucid beta yesterday having seen an announcement, and regretted it immediately.

Reason: the new Nouveau video driver is not nearly as good as proprietary was on my Karmic installation (I use Nvidia 8600). The fonts look fuzzier, with color tints getting in the way and thinner strokes making them less readable. 

Overall impression: new video driver delivers rugged fonts rendering compared to the proprietary one. This ragged text experience made my eyes hurt, which caused me to promptly ditch the beta and return to 9.10.   

Since 90% of my work has to do with text I did feel the difference in font rendering right away, and the difference is not in favor of the newer release. 

Just wondering: is it a beta state of affairs and is someone working on the issue or will future Ubuntu users have to stick with the new video driver forever?

I latter case I'll keep using my current 9.10, but eventually will have to ditch Ubuntu altogether if they won't provide adequate graphics support.

One more thing: I find the new window controls placement (left side of the window title bar instead of the right as it used to be) **horrible**. It's okay for Ubuntu team to experiment, and I'm with them in that, but gosh give user an option to return back to their old conservative interface habits if they aren't all that happy with your experimenting...

---

### Post by coffeecat on 2010-03-21
You're comparing the new open-source driver (nouveau) in Lucid with the proprietary driver (nvidia) in Karmic. Did you try installing the nvidia driver in Lucid? I suppose not. It's not difficult.

One thing that affects perception of font rendering in the default theme in Lucid is that some text is rendered in dark grey (either #404040 or #323232 depending on location) whereas in the default Human theme in Karmic they were near-black (#101010 or #1A1A1A). And other themes will have other values. That's easily changed in Appearance > Theme > Customise > Colours. You'll probably find the fonts sharper if you blacken them this way - or just change the theme. Personally, I find the grey text wishy-washy and will probably change them when Lucid goes final. At the moment the theme is still being fine-tuned so I'm going to stay with the default look and see what happens.

As far as the button placement is concerned, many agree with you, some have come to like it. At the moment the button move to the left has affected all themes, but rumour is that before final only the new 'Light' themes will have left-placed buttons. Themes that are designed for right-placed buttons will be untouched. We shall see if this is so. In any event it is not difficult to move the buttons back to the right. A search of the forum would have found many threads on this topic.

In the meantime I am content to leave things as they are and see what and what does not change. We are still only in the early phase of Beta, after all.

---

### Post by Keyper7 on 2010-03-21
Nouveau is not a replacement for the proprietary driver. It is a replacement for the old nv driver.

You can still install the proprietary driver the same way you did before.

---

### Post by sdowney717 on 2010-03-21
I had to blacklist nouveau in order to install nvidia drive.
Otherwise the installer just cant do it.

So blacklist, reboot, get startx error, boot console window, install nvidia river reboot, done.

---

### Post by meborc on 2010-03-21
> **sdowney717 said:**
> I had to blacklist nouveau in order to install nvidia drive.
Otherwise the installer just cant do it.

So blacklist, reboot, get startx error, boot console window, install nvidia river reboot, done.

are you talking about the nvidia driver from their website? because the proprietary driver from system-administration-hardware drivers works fine for me... no blacklisting, just two clicks and a reboot

---

### Post by yoasif on 2010-03-21
> **Kom-Si said:**
> Reason: the new Nouveau video driver is not nearly as good as proprietary was on my Karmic installation (I use Nvidia 8600). The fonts look fuzzier, with color tints getting in the way and thinner strokes making them less readable. submit a bug report (ubuntu-bug Xorg) -- I had a similar issue on a desktop of mine during the Karmic cycle and it was fixed.

---

### Post by Kom-Si on 2010-03-22
> **coffeecat said:**
> Did you try installing the nvidia driver in Lucid? I suppose not. It's not difficult.

Oh yes, I did. To no avail, alas. The hardware driver installer shows NVIDIA drivers as installed and activated but 'not used'. And stupid me could figure out how to work around that one. I'd appreciate If you could elaborate a bit on re-instating NVIDIA drivers in Lucid. Hints posted here like 'blacklist, reboot' won't help me any for my Linux expertise leaves much to be desired. Step-by-step if you please. I'm all willing to give Lucid another try, but for the fonts. ;) 

And by the way, thanks for the extended reply. Didn't expect much attention really since my primary motive was to vent some of the frustration I felt at the moment...

---

### Post by Kom-Si on 2010-03-22
> **meborc said:**
> just two clicks and a reboot

**what** two clicks?

I saw the 'the proprietary driver from system-administration-hardware drivers' sitting there but I couldn't make it work. The util says that the driver 'is not used'. And no suggestion how to reverse the sitch... :(

So, how did you do it?

---

### Post by cariboo on 2010-03-22
Pretty well all versions of the Nvidia restricted driver say that same thing, but in fact they are in use. It is an error.

---

### Post by psyke83 on 2010-03-22
> **Kom-Si said:**
> I finally got tempted to try Lucid beta yesterday having seen an announcement, and regretted it immediately.

Reason: the new Nouveau video driver is not nearly as good as proprietary was on my Karmic installation (I use Nvidia 8600). The fonts look fuzzier, with color tints getting in the way and thinner strokes making them less readable. 

Overall impression: new video driver delivers rugged fonts rendering compared to the proprietary one. This ragged text experience made my eyes hurt, which caused me to promptly ditch the beta and return to 9.10.   

Since 90% of my work has to do with text I did feel the difference in font rendering right away, and the difference is not in favor of the newer release. 

Just wondering: is it a beta state of affairs and is someone working on the issue or will future Ubuntu users have to stick with the new video driver forever?

I latter case I'll keep using my current 9.10, but eventually will have to ditch Ubuntu altogether if they won't provide adequate graphics support.

One more thing: I find the new window controls placement (left side of the window title bar instead of the right as it used to be) **horrible**. It's okay for Ubuntu team to experiment, and I'm with them in that, but gosh give user an option to return back to their old conservative interface habits if they aren't all that happy with your experimenting...

I suspect that your font rendering problem has **nothing** to do with drivers.

Please see this bug: [#512615]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512615")

The bug is targeted for fixing by beta 2. However, you can take advantage of the [improved lcd filtering PPA]("https://launchpad.net/~improved-lcd-filtering") and [firefox-smooth-scaling PPA]("https://launchpad.net/~firefox-smooth-scaling/+archive/ppa") if you can't wait for the official fix. Highly recommended.

---

### Post by Kom-Si on 2010-03-22
> **psyke83 said:**
> I suspect that your font rendering problem has **nothing** to do with drivers.

Please see this bug: [#512615]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512615")

The bug is targeted for fixing by beta 2. However, you can take advantage of the [improved lcd filtering PPA]("https://launchpad.net/~improved-lcd-filtering") and [firefox-smooth-scaling PPA]("https://launchpad.net/~firefox-smooth-scaling/+archive/ppa") if you can't wait for the official fix. Highly recommended.

WOW! What a relief! Thanks a lot. After installing the PPA for Firefox I did feel the difference. Now I got a system I can live with... :)
Big kudos, mate - you saved my day!

PS Although I'm still perplexed by 'The driver is activated but not currently in use' message in the Hardware Drivers app. Why can't I use an activated driver, for chrissake?

---

### Post by coffeecat on 2010-03-22
> **Kom-Si said:**
> PS Although I'm still perplexed by 'The driver is  activated but not currently in use' message in the Hardware Drivers app.  Why can't I use an activated driver, for chrissake?

Did you miss this post?

> **cariboo907 said:**
> Pretty well all versions of the Nvidia restricted driver say that same thing, but in fact they are in use. It is an error.

Mine does the same. Jockey says the nvidia driver is activated but not in use - except that it is. It must be - compiz works.

I guess it'll be sorted out in due course.

---

### Post by Kom-Si on 2010-03-22
> **coffeecat said:**
> Did you miss this post?

Yeah. Saw it only after posting my reply to you.

> **coffeecat said:**
> I guess it'll be sorted out in due course.

Hope so. Thanks again...

---

### Post by jaoc223 on 2010-03-22
I may be a little off topic here, I apologize in advance, but for me I'm using an imac and dualboot with ubuntu, installing the ati opensource drivers have made a world of difference with my fonts in chromium browser, firefox browser and the rest of my system fonts.

---

### Post by coffeecat on 2010-03-23
> **jaoc223 said:**
> I may be a little off topic here, I apologize in advance, but for me I'm using an imac and dualboot with ubuntu, installing the ati opensource drivers have made a world of difference with my fonts in chromium browser, firefox browser and the rest of my system fonts.

That's an interesting observation. I'm posting from my laptop with ATI HD4200 and open source driver at the moment and the font rendering in Lucid is more pleasing than with the proprietary nvidia driver on my main desktop. Different monitors with different resolutions, of course, so not a completely fair comparison.

---

### Post by psyke83 on 2010-03-23
Folks,

Let's stop this misinformation before it spreads. If somebody finds that a proprietary driver to display  fonts superior to the open source driver (or vice-versa), you are mistaken. It is a *simple configuration issue*.*

The reason why fonts look different is due to the default *resolution* and *refresh rate *used by each  driver. Whatever setup is optimal for your screen can be configured by *any* of the drivers; in the case of open drivers, via the common XRandR interface used by the System -> Preferences -> Monitors application, and in the case of the closed drivers, their custom configuration utilities (or perhaps the XRandR interface if custom driver options do not conflict).

*There was an exception. I remember that some time ago when the EXA acceleration code was immature, some of the open drivers were not rendering fonts with the correct subpixel pattern  - for a very short time. This is no longer the case, and has not been the case for a very long time.

---

