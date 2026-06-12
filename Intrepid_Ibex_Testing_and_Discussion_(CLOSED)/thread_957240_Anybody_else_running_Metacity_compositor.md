---
title: "Anybody else running Metacity compositor?"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Peter76 on 2008-10-24
I'm running Intrepid in VirtualBox and have compositing turned on in Metacity for a while now without any problems. I really like it's simple drop shadow and alt-tab effect; nothing fancy, but it looks good. Also makes it possible for awn to run. Would like to hear more experiences.

---

### Post by Hairy_Palms on 2008-10-24
yea ive been running it for the last few days, i like it, though the panel loses its drop shadow every time i logout untill i disable/reenable composite, much lighter than compiz, lets me run fullscreen opengl apps without the low fps and bugs that compiz causes :)

---

### Post by Sand &amp; Mercury on 2008-10-24
I wrote an article about it not long ago:

[http://hehe2.net/linuxhowto/compositing-with-metacity-another-look/](http://hehe2.net/linuxhowto/compositing-with-metacity-another-look/)

---

### Post by Hairy_Palms on 2008-10-24
nice article, i agree with the lack of config options, the only thing id really like is transparency, like what xfwm4 allows, before intrepid i replaces metacity and compiz with xfwm4 on an old intel integrated laptop and it worked fine

---

### Post by Peter76 on 2008-10-25
@ S&M: nice article!
@ Hairy Palms: The problem with the panel shadow is reported here: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/269670](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/269670)

Or is that you who reported it?

---

### Post by Hairy_Palms on 2008-10-26
not me who reported it, but i just signed onto it :) 
even with that bug i still love metacity composite, none of the bugs fullscreen apps get with compiz and much faster even if i set compiz to only do the same effects

---

### Post by talkingwires on 2008-10-26
When I use compositing, I use Metacity. Each new release, I enable it for a few days to check it out, but usually end up turning it off because it messes up VLC and Mplayer's video playback. The video is choppy unless I disable all other running programs, and Metacity paints the right-click menu (to switch over to full screen) under the actual video.

Then again, my laptop has a Raedon 7500, which has been blacklisted from running Compiz.

---

### Post by FuturePilot on 2008-10-26
I like the way the focused window has a more vibrant shadow underneath it, it really looks nice. The only problem is that it causes weird tearing when moving windows around quickly and in video playback. It looks kind of like a big Z.

---

### Post by SteveMcQwark on 2008-10-26
Haha! Zoro has invaded your computer through the Metacity Compositor!

---

### Post by ad_267 on 2008-10-26
I've been using it too. I really like the simplicity and basic effects. The only issue I have is that the Alt-Tab screen takes a little too long to appear.

---

### Post by FuturePilot on 2008-10-26
> **SteveMcQwark said:**
> Haha! Zoro has invaded your computer through the Metacity Compositor!

:lolflag:

---

### Post by jbg7474 on 2008-10-27
I tried out Metacity with compositing, and I really liked it.  In some ways I like it better than Compiz.  However, I'm using cairo-dock, and I noticed some flickering when I would mouse over the dock.  Using compiz fixes that problem.  I didn't notice any speed differences, though.

---

### Post by wizard10000 on 2008-10-27
> **Peter76 said:**
> I'm running Intrepid in VirtualBox and have compositing turned on in Metacity for a while now without any problems. I really like it's simple drop shadow and alt-tab effect; nothing fancy, but it looks good. Also makes it possible for awn to run. Would like to hear more experiences.

Do you get the problem with white icon artifacts that's been reported with awn and compiz under Intrepid?  It finally irritated me enough that I got rid of awn.  Even awn from trunk has the problem.

---

### Post by wizard10000 on 2008-10-28
I ran metacity a bit yesterday just for fun - with compositing enabled metacity used about 10mb of RAM with no windows open other than system monitor - compiz.real uses about twice that on my machine.

No real increase in performance I could see just fooling around for a few minutes - and I've grown attached to my emerald theme, desktop cube and transparent windows.  Back to compiz for me  :)

---

