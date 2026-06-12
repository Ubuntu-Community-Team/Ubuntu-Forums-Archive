---
title: "Default Panel Widgets Disappear"
date: 2012-03-31
forum: Installation &amp; Upgrades
---

### Post by bilijoe on 2012-03-31
For multiple reasons, I decided to roll back all my Ubuntu installations to LTS version 10.04. My standard approach to Upgrading (in this case, downgrading) is to use a moderate sized partition for "/", and all the rest of the space I have available for "/home". Then, when I up[down]grade, I have the install program re-format the '/' partition for the new install, but leave "/home" 'as is'. This has worked beautifully for me for years now, effectively being a cross between a "clean" [new] install, and an upgrade. (I.e., all my files, settings, preferences, etc. are preserved, but the system is installed "clean", on a freshly formatted partition.:p)

In this case (Down-grading from 11.04 to 10.04), I followed the same procedure. All seemed to go as expected, except for one little glitch.

When it came time to boot to the newly installed version 10.04, I got a benign-sounding error message, something to the effect of, "Unable to load (or initialize, or... ?) widget. Do you want to delete this widget?":confused: I figured, it's only a widget. If it (10.04) can't handle it for some reason, no reason to keep it. So I said "Yes", and deleted it. 

The boot completed successfully, and everything works fine - with one little exception. The entire right half of the top panel (the part with the battery status, network connection status, volume control, date/time, user status, and shut-down options button) was missing. OOPS! I guess that section was the widget in question.](*,)

So I re-ran the install (of 10.04), again formatting "/", and leaving "/home" alone. Apparent success, but still no right half of my top panel. Guess the data behind the widget in question lives in the "/home" partition (somewhere).:confused:

So, can anyone tell me where this data resides? If I know where it is, I can do a totally clean install (i.e., format "/home" as well, and then copy my backup of "/home" to the new, clean installation EXCEPT FOR THE DIRECTORY THAT HOLDS THE DATA FOR THE CONFIGURATION OF THE TOP PANEL. I figure that'll give me the result I want (keeping all my settings, preferences, etc., intact), except I'll have to redo the minimal task of re-fritzing (the Left part of) my top panel.

Sorry this has been so long-winded for such a simple request - I have ADD and sometimes just can't seem to be concise. In any event, the information about where the config info for the (top) panel is stored would be greatly appreciated.:popcorn:

---

