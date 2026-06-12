---
title: "A new and simple way to enable external monitors"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TrueTom on 2009-09-19
Windows 7 introduced a nice little tool to select the video output configuration. By pressing the keyboard combination [WIN]+[P] you can quickly select between cloning and extending your desktop for example (Screenshot: [http://win7.in/wp-content/uploads/2009/03/winp.jpg]("http://win7.in/wp-content/uploads/2009/03/winp.jpg")). So I hacked together a proof-of-concept version for Linux for you to try. For the full experience create a global shortcut with [WIN]+[P]... :)

Download:

[http://dl.getdropbox.com/u/963697/mode-switcher.tar.gz]("http://dl.getdropbox.com/u/963697/mode-switcher.tar.gz")

(Btw.: You're out of luck atm if the names of your outputs are called something else than LVDS1 and VGA1)

---

### Post by kestal on 2009-09-19
> **TrueTom said:**
> Windows 7 introduced a nice little tool to select the video output configuration. By pressing the keyboard combination [WIN]+[P] you can quickly select between cloning and extending your desktop for example (Screenshot: [http://win7.in/wp-content/uploads/2009/03/winp.jpg]("http://win7.in/wp-content/uploads/2009/03/winp.jpg")). So I hacked together a proof-of-concept version for Linux for you to try. For the full experience create a global shortcut with [WIN]+[P]... :)

Download:

[http://dl.getdropbox.com/u/963697/mode-switcher.tar.gz]("http://dl.getdropbox.com/u/963697/mode-switcher.tar.gz")

(Btw.: You're out of luck atm if the names of your outputs are called something else than LVDS1 and VGA1)


Though a Windows 7 feature, it is a very interesting concept (not necessarily this, but a way to switch displays as quickly as this). This could be kind of useful to implement (well, especially for me). I am usually on my laptop and need to switch back and forth from things rather quickly and quietly whenever doing presentations, and its one of the only reasons why I stay on Windows 7 for my laptop.

Unfortunetely, judging by the description, this would only work for that specific configuration. Would LVDS1 be TV? Projector?

---

### Post by jocko on 2009-09-19
Well done! Unfortunately my displays are "DVI-0" and "S-video", so I can't test it (maybe on my laptop, but it's using the nvidia driver which is pretty straight forward to set up with nvidia's control panel).
But this would certainly help my desktop which has an ati card (now legacy), so I hope you continue working on it. Does it use xrandr (which really needs a *working* graphical front-end)? In that case, is there any way you could have your app get the names of the available outputs from xrandr?

---

### Post by kestal on 2009-09-19
It would be interesting to see if this can be implemented to grab the correct displays connected in any case and intuitively have it mapped out. Not necessarily just like this, but in the case if you have to connect to multiple monitors.

Holding the key configuration (which should be easily done with one hand) and then using the arrow keys to go through the options, where if you go to extend you can check for other options, like connecting one source to multiple monitors, or to a specific monitor (incase of Projector/TV being connected at the same time, or something less specific *whistles innocently*)

---

### Post by TrueTom on 2009-09-19
> **kestal said:**
> Unfortunetely, judging by the description, this would only work for that specific configuration. Would LVDS1 be TV? Projector?

LVDS is usually the monitor of a notebook, while VGA is the, well, VGA port to connect the external display or projector. The names are hardcoded at the moment instead of doing the right thing and query them. This is just a quick test to see if people like the idea and if it makes sense to fully develop it.

---

### Post by kestal on 2009-09-19
> **TrueTom said:**
> LVDS is usually the monitor of a notebook, while VGA is the, well, VGA port to connect the external display or projector. The names are hardcoded at the moment instead of doing the right thing and query them. This is just a quick test to see if people like the idea and if it makes sense to fully develop it.

Indeed. My apologies, mine is different :) I wont have a chance to look at it until I switch to my main computer in an hour or so though. I cant wait :)

---

### Post by wacked_up on 2009-09-19
This looks both useful and pretty. Very nice.
I'd love to be able to use this on my laptop!

---

### Post by SixedUp on 2009-09-19
> **TrueTom said:**
> LVDS is usually the monitor of a notebook, while VGA is the, well, VGA port to connect the external display or projector. The names are hardcoded at the moment instead of doing the right thing and query them. This is just a quick test to see if people like the idea and if it makes sense to fully develop it.

I'd like to have this utility. At the moment I have some simple bash scripts driving xrandr (looking at your code, I'm doing pretty much what you are) but I don't have the nice GUI to help.

Sadly I can't test your code unless you provide some info on pre-reqs to compile it; none of my machines have the same output names as you are using. If you produce a version that queries the outputs, I'd love to test it. I also have a laptop with 3 apparent outputs, only 2 of which are physically exposed on the chassis - would be interesting to see how your code could be made to cope with that scenario.

---

### Post by Johan Karl Johansen on 2009-09-19
anyone tried this?

---

### Post by kestal on 2009-09-20
> **Johan Karl Johansen said:**
> anyone tried this?

I would but I dont have VGA on laptop. only DP/HDMI/DVI. I extend on all of them for separate uses on W7.

---

### Post by nystire on 2009-09-20
This is really useful Thank you.

---

### Post by Rackstar on 2009-09-20
Would be very usefull indeed!

I always thought dual monitoring was still kind of non-intuitive in ubuntu. Still would like to see a dialog popping up when a screen is detected. (But this is outside this project)

---

### Post by SixedUp on 2009-10-07
No blame, but given the two week silence I'm curious to know if TrueTom is still interested in making this project happen, or if its fallen by the wayside?

---

### Post by TrueTom on 2009-10-07
Sorry, but some RL stuff came up. I plan to upload a new version at the weekend which supports display names as command line parameters so everyone can test it.

---

### Post by SixedUp on 2009-10-07
I completely understand - RL always seems to get in the way of the fun stuff. Look forward to testing your code in a few days time!

---

