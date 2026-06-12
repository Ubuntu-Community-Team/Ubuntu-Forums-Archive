---
title: "Radeon RS200M: Low display and video quality in ubuntu 12.04"
date: 2014-06-27
forum: Installation &amp; Upgrades
---

### Post by tojonukokhadush on 2014-06-27
hello there! i recently network upgraded to 12.04 from 10.04! one thing i have been noticing is i am experiencing a low quality while playing a video than when the same video was played in 10.04; also i am noticing low video quality in youtube as well! even the fonts display are not so eye candy; we could change the settings(contrast and all) in 10.04 but here in 12.04 there's no any option! seems 10.04 was a percect package! how can i correct this problem?

---

### Post by ibjsb4 on 2014-06-27
Are you now running the Unity desktop?  It could be too much for an older computer.
You could try a different desktop and a different window manager.
```
sudo apt-get install gnome-session-fallback
```
This will give you a desktop that looks like 10.04 and can be ran with the Metacity WM.

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by Vladlenin5000 on 2014-06-28
The previous suggestion is to be taken seriously. Unity requires hardware resources not present in many old computers.
However... The issues you're experiencing are most likely related to an incorrect (or inefficient) video driver. Please give some information about your hardware. Nobody should be giving tips without knowing that first

---

### Post by mörgæs on 2014-06-28
Yes, please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by tojonukokhadush on 2014-06-30
thank you guys! i forgot to mention that i am already running on gnome-fallback-session! 

and when i do run the command- ```
sudo lshw -C display
```
sorry i did understand nothing but i got something like this-


[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]```
  *-display                      description: VGA compatible controller
       product: RS200M [Radeon IGP 330M/340M/345M/350M]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:11 memory:f6000000-f7ffffff ioport:a000(size=256) memory:f4500000-f450ffff memory:f4520000-f453ffff



```



and clearly what i can say is when i was running on 10.04 everything was just fine about the display and graphics and now its all like somewhat pixelized type graphics!

further help is expected!



and oh! when i run the following command- ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -sanitize > lshw.txt[/FONT][/COLOR]
```
it just returns "false"

---

### Post by ibjsb4 on 2014-06-30
> **Vladlenin5000 said:**
> Nobody should be giving tips without knowing that first
Suggestions are always welcome, but why must you post as if you are of authority here?  This is the second time I have spoke of this to you; is this why?  Lighten up please.

@OP
I will let the others follow up with their suggestions.

---

### Post by Mark Phelps on 2014-06-30
It's likely that the primary reason your video is such low quality is that between Ubuntu 10.x and 12.x, AMD dropped video driver support for your card, so now, you are running on the default open-source Radeon driver, which while quite good, apparently doesn't work well with "older" hardware like your video card.

---

### Post by mörgæs on 2014-07-01
An RS200M is from around 2002-3. As mentioned above there are no closed-source drivers available today.

In general you should give it the lightest workload possible. I suggest a fresh install of Lubuntu 14.04.

---

### Post by tojonukokhadush on 2014-07-02
okay! thanks a lot! i must switch to Lubuntu very shortly then :-( i was so in love with ubuntu! 10.04 particularly!

---

