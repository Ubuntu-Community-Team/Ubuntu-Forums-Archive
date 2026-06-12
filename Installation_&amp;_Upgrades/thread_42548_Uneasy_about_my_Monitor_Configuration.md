---
title: "Uneasy about my Monitor Configuration"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by polo_step on 2005-06-18
I have a Mitsubishi Diamond Pro 900u 19" monitor (Sony tube).

For some reason, this monitor is not transparently easy for Linux install packages, though I have no trouble with other monitors.

Kubuntu 5.04 auto-configures it at huge resolution.  I can manually go in Peripherals > Display and get it down to the desired 1024x768, but it locks the refresh rate at 85MHz, which I think is a little hot for extended use at this resolution (I cooked a couple of cheap 17" monitors a while back when a new graphic card configured that same setting in Windows, so I'm a bit leery of wrecking a good monitor).  There are no higher or lower rates offered in the interface.

Any thoughts on this?

Thanks for any help.

---

### Post by diebels on 2005-06-18
85MHz is a little hot yes, 85Hz is pretty normal;)
No need to worry. Newer monitors just switch off when given to high rates. I would set the resolution to as high as possible with 85Hz(I guess 1400x1050), since higher resolution looks nicer and 85Hz and higher is good for the eyes. If the fonts get to small just increase the font size in gnome-font-properties.

---

### Post by polo_step on 2005-06-18
[QUOTE=diebels]85MHz is a little hot yes, 85Hz is pretty normal;)
No need to worry. Newer monitors just switch off when given to high rates. I would set the resolution to as high as possible with 85Hz(I guess 1400x1050), since higher resolution looks nicer and 85Hz and higher is good for the eyes. If the fonts get to small just increase the font size in gnome-font-properties.[/QUOTE]
It auto-configures to an insanely high res @ 72MHz, but I need lower res because of my eyes...yet 1024x768 looks like 800x600.  I'm still sort of confused.

As long as I don't burn another monitor up everything else is small stuff.  Knoppix tried to run it at 101MHz! [-X

---

### Post by Worzel on 2005-06-19
I had silly sizes when I first installed Kubuntu, either 640 or else way bigger than my 15" monitor could handle.
Possibly this link [http://ike.room17.com/pipermail/ale/20031127/003787.html](http://ike.room17.com/pipermail/ale/20031127/003787.html) might be of help.
Jim

---

### Post by polo_step on 2005-06-20
Because of some weirdnesses with other stuff, I'm giving Ubuntu a chance and it still has me at 1024x768@85Hz.

I'd feel better if it was a little cooler than that.

And yes, I finally caught my compulsive typo -- I know that it's not MEGAHertz!  :???:

---

### Post by diebels on 2005-06-20
:) It's more than cool enough. I would run it at 1400x1050@85Hz. And if you think the fonts are to tiny for your eyes, run "gnome-font-properties" get into the advanced window and increase the font resolution.

---

