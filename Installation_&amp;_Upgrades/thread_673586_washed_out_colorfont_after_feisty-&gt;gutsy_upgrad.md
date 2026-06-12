---
title: "washed out color/font after feisty-&gt;gutsy upgrade"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by BraveSirRobin on 2008-01-20
I just upgraded my kubuntu feisty install to gutsy by replacing all occurrences of "feisty" in /etc/apt/sources.list with "gutsy" and running apt-get dist-upgrade from the command line.

The upgrade seems to have been successful, but now I'm having trouble reading fonts and viewing certain images in firefox. A couple examples:

[list]
[*] The song/artist/title text on pandora.com is so faint (with pixels missing?) I can hardly read it, and the thumbs up/down image, which was very faint before, seems not to show up at all now.
[*] I have Forecastfox installed, and can no longer see the forecast images unless I'm sitting down in front of my screen.
[*] The text of the story blurbs (under the headlines) at usatoday.com is hard to read unless I put my face up to the screen and squint.
[*] I was using the "Sea Green" color scheme in Yahoo mail and, after the upgrade, it started looking so awful that I changed colors.
[*] The standard vBulletin theme (like [on this website](http://www.city-data.com/forum/) suddenly makes me think "walk toward the light" and the images and text are no longer as pronounced as before the upgrade.
[*] Can hardly see the buttons on the "Next" and "Back" links on [this page](http://money.cnn.com/galleries/2007/pf/0707/gallery.do_it_now_retirement.moneymag/4.html). They just look like regular links unless I look real close.
[/list]

I tried changing the brightness and contrast on my monitor (HP 20" flat-pannel), which helped a little, but the issues with readability/visibility are still there. I found [this thread](http://ubuntuforums.org/showthread.php?t=590424), which sounded like it might address my problem (even though it was only about fonts and not images), but the fix suggested in it doesn't seem to work.

Anyone know what's going on? Am I crazy? :confused:

---

### Post by PierGroup on 2008-01-21
Not mad. I made a similar post two days ago in the Desktop Environments forum. 

I have been trying all manner of changes to see if I could track down the area this change is coming from but, so far, without success.

It is a real PAIN!

---

### Post by PierGroup on 2008-01-23
See my latest posting in the 'faint text' thread for a possible solution.

---

### Post by BraveSirRobin on 2008-01-25
> **PierGroup said:**
> See my latest posting in the 'faint text' thread for a possible solution.

Awesome, thanks. [a restricted ATI video driver](http://ubuntuforums.org/showpost.php?p=4191035&postcount=3) was exactly what I needed.

Ran 'sudo restricted-manager-kde' and had adept download some stuff. After a restart graphics were 100x better.

---

