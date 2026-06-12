---
title: "Video flickers when something else takes focus"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-03-30
Something that I've noticed under Jaunty is that video flickers when something happens on top of it.

I run a twinview set up so when I have fullscreen video on one and then select something on the other, the gnome-panel on the video screen comes to the front (as expected, and wanted) but the video flickers briefly.

And when the new notifications pop up, the video flickers.

Something that I've noticed is that there isn't a video plugin for Compiz anymore. If there is, I don't know where it is now.

---

### Post by tjeremiah on 2009-03-30
happens to me since update. When viewing a video in full screen, no matter if its flash, vlc, w/e, the video would flicker and sometimes pauses and doesnt continue.

---

### Post by Darkshade on 2009-03-30
> **OliW said:**
> Something that I've noticed under Jaunty is that video flickers when something happens on top of it.

I run a twinview set up so when I have fullscreen video on one and then select something on the other, the gnome-panel on the video screen comes to the front (as expected, and wanted) but the video flickers briefly.

And when the new notifications pop up, the video flickers.

Something that I've noticed is that there isn't a video plugin for Compiz anymore. If there is, I don't know where it is now.

Happens to me too with twinview. I can see the wallpaper for a second (maybe less) when another window takes focus. I have the video plugin in ccsm but I don't see any change if it's turned on or off.
It's a little annoying but I'm sure it used to happen in Intrepid too (not sure about Hardy since I had only one monitor back then).

---

### Post by tjeremiah on 2009-03-30
> **Darkshade said:**
> Happens to me too with twinview. I can see the wallpaper for a second (maybe less) when another window takes focus. I have the video plugin in ccsm but I don't see any change if it's turned on or off.
It's a little annoying but I'm sure it used to happen in Intrepid too (not sure about Hardy since I had only one monitor back then).

I dont have twinview and I too can see the wallpaper for a second and the video plugin makes no difference. This is basically the only annoyance with the update along with shutting down that is the problem with 9.04. My graphic card is in my sig. This problem was not present in 8.10.

---

### Post by Pat L.I. on 2009-03-30
I am seeing this behavior on my eeepc 900. running 9.04 beta. 
This did not occur for me in Hardy.

---

### Post by Darkshade on 2009-03-30
At least it's not as bad as KDE4 where instead of your wallpaper you see your login screen AND your wallpaper :lolflag:
Someone needs to look into it though, it's becoming more and more annoying since I saw this topic about 30min ago, lol :(

---

### Post by Bakon Jarser on 2009-03-30
I see the wallpaper too for a fraction of a second.  I notice it when the controls pop up for smplayer and I also notice it when exiting fullscreen flash videos.  It doesn't happen with compiz effects turned off.  Has someone filed a bug report?  Also might help to list graphics cards/driver.

nvidia geforce 6150se / 180.37

---

### Post by tjeremiah on 2009-03-30
Intel Mobile GM965/960(rev 0c

---

### Post by Bakon Jarser on 2009-04-08
Took me a while but I finally got around to filing a bug report.  Can someone please confirm this.

[https://bugs.launchpad.net/ubuntu/+bug/358077](https://bugs.launchpad.net/ubuntu/+bug/358077)

---

### Post by Bakon Jarser on 2009-04-10
I've upgraded to the 185.19 beta driver and am still getting this.

---

### Post by Bou on 2009-04-10
Please go to CCSM, general options and uncheck "unredirect fullscreen windows". Then see if it still happens.

---

### Post by punischdude on 2009-04-10
> **Bou said:**
> Please go to CCSM, general options and uncheck "unredirect fullscreen windows". Then see if it still happens.

Fixed it for me. Thanks!

---

### Post by Bou on 2009-04-10
Glad to help!

---

### Post by jmmL on 2009-04-10
Seems to have fixed it for me as well, thanks!

---

### Post by Bou on 2009-04-10
You know, maybe we should send a bug and ask for it to be disabled by default. Does anyone know if there's an advantage to have it enabled?

---

### Post by Darkshade on 2009-04-10
Awesome, fixed it for me too.
Thanks!

---

### Post by tjeremiah on 2009-04-10
thanks :D

---

### Post by OliW on 2009-04-10
Yeah fixed for me. Woot.

I think it may have some ramifications on 3d performance. I'll test when it's not 1am and I'm (hopefully) sober.

---

### Post by JohnJackson on 2009-04-12
Looks like this bug was present on previous releases: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153204]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153204")

---

