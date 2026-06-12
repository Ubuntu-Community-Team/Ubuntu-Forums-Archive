---
title: "Resolution not recognized and external monitors not working in X11 intel graphics"
date: 2018-12-04
forum: Installation &amp; Upgrades
---

### Post by josdh149 on 2018-12-04
Ubuntu forums,

I have run into the following problem when in X11: my laptop does not recognize the original resolution of its internal screen but just logs in at 960x540 or something like that. At the login screen the resolution is still 1600x900.
This low resolution is also the only resolution available in the screen settings. To solve the problem I add the resolution manually with xrandr, however, this is the step that needs to be performed at every boot.
Additionally, it does not recognize any external monitors. So, when working with external monitors I choose to login into Wayland. The problem in Wayland, however, is my mouse lags so I prefer to use X11.

My laptop is equipped with a nvidia graphics card which I am not using. This is also the card which I do not prefer to use since I use a eGPU at home when running windows. Therefore, I disabled the internal nvidia in windows under device manager. I thought it was worth mentioning this since it might be also messing with the problem.

So, when not at home I run ubuntu which I prefer to use with only intel graphics.

Does anyone have a solution to this problem? Thanks in advance. 
I can understand you need to ask some additional questions to find the source of the problem so feel free to ask.

Jos

---

